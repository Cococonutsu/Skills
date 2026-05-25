---
name: latex-table-debugging
description: "Design, diagnose, and repair LaTeX tables by reasoning about how tabular cells, boxes, row/column color, multirow/multicolumn spans, line breaks, citations, footnotes, resizebox/adjustbox, and booktabs rules compose. Use for any LaTeX table whose visual output or compilation is fragile: disappearing citations, broken alternating row colors, black bars, partial cell backgrounds, misaligned multirow cells, overflowing text, bad line breaks, or package interactions in academic papers and reports."
---

# LaTeX Table Debugging

## Mental Model

Treat every table as stacked layers:

1. `tabular`/`tabularx`/`longtable` defines the grid, row boundaries, and alignment.
2. Column specs such as `l`, `c`, `r`, `p{...}`, `m{...}`, `b{...}`, `X`, and `>{...}` decide each cell's paragraph mode and width.
3. Cell content may add boxes: `\parbox`, `minipage`, `\makecell`, `\shortstack`, `\multirow`, `\multicolumn`.
4. Color commands paint either rows (`\rowcolor`), columns (`>{\columncolor...}`), or cell boxes (`\cellcolor`).
5. Global wrappers such as `\resizebox`, `adjustbox`, and `sidewaystable` scale or move the finished table.

Most bugs happen when a command from one layer is expected to behave like a command from another layer. Example: `\rowcolor` paints physical rows, while `\multirow` creates one box spanning several physical rows; those models do not automatically agree.

## General Workflow

1. Inspect the real preamble and table source. Search for `array`, `tabularx`, `booktabs`, `makecell`, `multirow`, `xcolor`, `colortbl`, `resizebox`, `adjustbox`, `cite`, `natbib`, and custom macros.
2. Identify the failing layer: grid, content box, color, span, citation/footnote expansion, or scaling.
3. Simplify only the failing layer. Do not rewrite the whole table if one cell macro is the issue.
4. Choose the least nested construct that expresses the layout.
5. After fixing the visible bug, recheck adjacent style constraints: row striping, rule thickness, vertical alignment, citation rendering, and column width.

## Choosing Cell Containers

Use `p{width}` columns when a column should wrap paragraphs naturally. Inside a `p` column, prefer plain text or a local `\parbox[t]{\linewidth}{...}` for controlled multiline content.

Use `\parbox[t]{<width>}{...}` when content needs internal line breaks, citations, or small formatting while still behaving like one normal cell box. In `p{...}` columns, `\linewidth` usually means the current column width.

Use `\makecell` for simple manual line breaks in uncolored, non-spanning cells. Avoid it in cells that are also under `\rowcolor`, `\cellcolor`, or `\multirow` unless the output has been checked, because `makecell` uses internal tabular-like machinery.

Use `\shortstack` for very small stacked labels without paragraph wrapping. Do not use it for long text, citations, or paragraph cells.

Use `minipage` only for complex cell contents such as lists, figures, or multiple paragraphs. It is heavier than `\parbox` and can change vertical spacing.

## Color Rules

- Use `\rowcolor` for alternating row styles. It colors physical rows, so repeat it on every physical row in a logical group.
- Use `\cellcolor` only for isolated emphasis. It colors the cell box and can conflict with `\multirow` or nested boxes.
- Use column coloring in the column spec only when an entire column should have a stable background.
- With `booktabs`, avoid heavy vertical rules and excessive cell coloring. If the existing paper already uses them, preserve local style rather than redesigning.
- If only the text background is colored, the content is probably inside a nested box that does not occupy the full row height.
- If a black rectangle appears, suspect `colortbl` interacting with `\makecell`, nested tabular material, malformed color scope, or color applied inside a span.

## Spans and Grouped Rows

Use `\multicolumn` for horizontal structure changes such as section headers or columns that need a different alignment/rule pattern.

Use `\multirow` only when the first column truly must be one vertically centered spanning cell. Keep its contents simple: text, short macros, or a stable box. Avoid putting row-color logic, complex line breaks, citations, footnotes, or nested tabular material directly inside the `\multirow` argument.

For logical groups with two or more physical rows, a more robust pattern is often:

```latex
\rowcolor{black!6}
Group label & subrow A & result A \\
\rowcolor{black!6}
            & subrow B & result B \\
```

This is not benchmark-specific. It applies to any grouped rows, such as datasets with easy/hard splits, models with zero-shot/few-shot rows, metrics with precision/recall rows, or ablations with base/variant rows.

## Citations and Footnotes in Tables

- If a citation key renders in body text but disappears in a table, suspect the cell container before changing `.bib`.
- Keep `\citep`, `\citet`, `\footnote`, and `\thanks` out of fragile span arguments when possible.
- Put citations in normal cell content or in a stable `\parbox`. Avoid citations inside `\multirow{...}{...}{...}` when the same cell also uses manual line breaks or color commands.
- Do not replace unresolved citations with hard-coded author-year text. Fix the key, bibliography, or cell macro.
- For table notes, prefer the paper's established convention: `threeparttable`, caption notes, or footnotemark/footnotetext. Do not introduce a new note system casually.

## Scaling and Width

- Treat `\resizebox{\textwidth}{!}{...}` as a last-mile wrapper, not a layout solution. It can hide overwide columns by shrinking fonts and rules.
- First tune column widths, `\tabcolsep`, `\arraystretch`, and text wrapping. Then apply `adjustbox`/`resizebox` if the venue layout requires exact width.
- In `p{...}` columns, use `>{\raggedright\arraybackslash}` for readable wrapped text and to restore `\\`.
- When text overflows, prefer changing the column model over adding manual line breaks everywhere.

## Practical Decision Rules

- Need a colored two-line label in one normal cell: use a `p` column plus `\parbox[t]{\linewidth}{line1\\line2}`.
- Need alternating colors over a two-row item: repeat `\rowcolor` on both rows.
- Need one label visually spanning two rows and no citation/complex formatting: `\multirow` is acceptable.
- Need a label plus citation over two rows in a colored table: prefer repeated physical rows with an empty second label cell, or put the label/citation in a simple `\parbox` in the first physical row.
- Need a section header across all columns: use `\multicolumn`, then restart row coloring deliberately after it.
- Need compact multiline column headers: `\makecell` is usually fine because headers are often uncolored and non-spanning; still check if header row uses color.

## Transferable Examples

### Example 1: Two-Line Cell With Citation

Bad pattern: using `\\` directly in a fragile span or colored box.

```latex
\multirow{2}{=}{\cellcolor{gray!10}Dataset A\\[-0.3ex]\citep{dataset-a}}
& easy & 72.1 \\
& hard & 61.4 \\
```

Better pattern: keep the multiline citation in a normal cell box and color physical rows.

```latex
\newcommand{\twolinecell}[2]{%
  \parbox[t]{\linewidth}{\raggedright #1\\[-0.3ex]#2}%
}

\rowcolor{gray!10}
\twolinecell{Dataset A}{\footnotesize\citep{dataset-a}} & easy & 72.1 \\
\rowcolor{gray!10}
& hard & 61.4 \\
```

Use the same shape for datasets, methods, models, tasks, or benchmark names. Rename the helper macro to match the table domain if that improves readability.

### Example 2: Alternating Color Over Logical Groups

Bad pattern: coloring only the first row of a multirow logical item.

```latex
\rowcolor{black!6}
Model A & zero-shot & 38.2 \\
        & few-shot  & 44.7 \\
Model B & zero-shot & 41.0 \\
        & few-shot  & 46.3 \\
```

Better pattern: alternate by logical group, but apply color to each physical row.

```latex
\rowcolor{black!6}
Model A & zero-shot & 38.2 \\
\rowcolor{black!6}
        & few-shot  & 44.7 \\
Model B & zero-shot & 41.0 \\
        & few-shot  & 46.3 \\
```

Reason: `\rowcolor` does not know that two physical rows are one logical item.

### Example 3: Section Headers With Multicolumn

Bad pattern: a section row inherits the wrong alignment or breaks vertical rules.

```latex
\rowcolor{gray!10}
Open-source models & & \\
```

Better pattern: use `\multicolumn` explicitly and then restart row styling.

```latex
\rowcolor{gray!10}
\multicolumn{3}{l}{\textbf{Open-source models}} \\
\midrule
Model A & 7B & 38.2 \\
Model B & 13B & 41.0 \\
```

If the table uses vertical rules in column specs, put the correct rule pattern in the `\multicolumn` alignment argument, such as `{l|}` or `{>{\raggedright\arraybackslash}p{4cm}}`.

### Example 4: Multiline Header Cells

Usually acceptable:

```latex
\textbf{Model} & \makecell[c]{\textbf{Single}\\\textbf{Choice}} &
\makecell[c]{\textbf{Fill}\\\textbf{with Hints}} \\
```

More stable when the header row is colored or uses paragraph columns:

```latex
\newcommand{\headtwoline}[2]{%
  \parbox[c]{\linewidth}{\centering\textbf{#1}\\[-0.2ex]\textbf{#2}}%
}

\rowcolor{gray!10}
\textbf{Model} & \headtwoline{Single}{Choice} & \headtwoline{Fill}{with Hints} \\
```

Rule: `\makecell` is convenient for compact headers, but if color artifacts appear, replace it with a `\parbox` whose width is controlled by the column.

### Example 5: Width Fix Before Resize

Bad pattern: using `\resizebox` as the first fix for an overwide table.

```latex
\resizebox{\textwidth}{!}{%
\begin{tabular}{lll}
Model & Prompt & Explanation \\
...
\end{tabular}}
```

Better pattern: first give long-text columns paragraph widths.

```latex
\setlength{\tabcolsep}{3.5pt}
\renewcommand{\arraystretch}{1.08}
\begin{tabular}{
>{\raggedright\arraybackslash}p{2.6cm}
>{\raggedright\arraybackslash}p{4.2cm}
>{\raggedright\arraybackslash}p{7.2cm}
}
Model & Prompt & Explanation \\
...
\end{tabular}
```

Apply `\resizebox` or `adjustbox` only after the column model is sane, especially in camera-ready tables where font size and rule thickness matter.

## Case Example: Benchmark Rows

Problem pattern:

```latex
\multirow{2}{=}{\cellcolor{black!6}PunMemeCN\\[-0.3ex]\citep{xu2025punmemecn}}
& easy: 4-option single choice & ... \\
\rowcolor{black!6}
& hard: 4-option single choice & ... \\
```

Why it is fragile:

- `\multirow` owns one vertical box while `\rowcolor` colors physical rows;
- `\\` inside the `\multirow` argument is not a normal table row break;
- `\cellcolor` colors the spanning box, not necessarily the row group;
- `\citep` expansion can disappear inside this fragile argument.

Do not "fix" it by nesting `\makecell` inside the colored `\multirow`:

```latex
% Bad: citation may appear, but colortbl can render a black bar.
\multirow{2}{=}{%
  \cellcolor{black!6}\makecell[l]{PunMemeCN\\[-0.3ex]\citep{xu2025punmemecn}}%
}
```

A robust general pattern:

```latex
\newcommand{\celltwoline}[2]{%
  \parbox[t]{\linewidth}{\raggedright #1\\[-0.3ex]#2}%
}

\rowcolor{black!6}
\celltwoline{PunMemeCN}{\footnotesize\citep{xu2025punmemecn}}
& easy: 4-option single choice & ... \\
\rowcolor{black!6}
& hard: 4-option single choice & ... \\
```

The macro name should match the local table's semantics. For benchmarks it may be `\benchname`; for datasets, models, metrics, or methods use a neutral local name such as `\celltwoline`, `\datasetcell`, `\modelcell`, or an existing paper macro.

## Editing Discipline

- Preserve content, labels, keys, and table numbering unless explicitly asked to change them.
- Make one structural change at a time and re-inspect the rendered table or user-provided screenshot.
- If local compilation is unavailable or unnecessary, still reason from the source and screenshot, and say what was not compiled.
- Prefer local helper macros for repeated cell patterns, but keep them generic enough for the table's actual domain.
