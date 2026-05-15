# SKILL.md Frontmatter BOM 问题记录

## 记录格式

本文档使用 Markdown（`.md`）。原因很简单：仓库里的内容本身就是 Markdown 和 YAML，直接放在仓库里最容易阅读、检索和长期维护。

## 问题现象

这个问题通常出现在 Windows 端编辑 `SKILL.md` 时，文件被保存成 UTF-8 with BOM，然后推到 GitHub。

在 macOS 端从 GitHub 拉取后，Codex 可以看到这个 skill 目录，`SKILL.md` 也看起来是正常的：

```yaml
---
name: research-paper-writing
...
```

但文件真实开头其实是：

```text
<U+FEFF>---
```

也就是前面多了一个不可见的 BOM 字节 `EF BB BF`。

### 典型表现

- skill 目录已经安装到本地，但 Codex UI 里不显示对应的 `$` 快捷命令
- 目录和文件都在，但技能没有被正确加载
- 眼睛看不出问题，只有按字节检查才会发现

## 什么时候会出现

最常见的场景是：

1. 在 Windows 上创建或编辑 `SKILL.md`
2. 编辑器默认使用 UTF-8 with BOM 保存
3. 把仓库推到 GitHub
4. 在 macOS 端拉取同一仓库
5. Codex 加载 skill 时读取 `SKILL.md` 顶部 frontmatter
6. 因为文件不是严格以 `---` 开头，frontmatter 解析失败

这类问题不一定每次都会被发现，通常要等到在 Codex 里找不到 `$skill-name` 的快捷命令时才会注意到。

## 为什么会出问题

Codex 读取 skill 时依赖 `SKILL.md` 顶部的 YAML frontmatter。

它要求文件真正的第一个字节就是 `-`，也就是：

```text
---
```

如果前面有 BOM，解析器看到的不是 `---`，而是：

```text
EF BB BF 2D 2D 2D
```

这会让 frontmatter 识别失败，技能虽然在仓库里，但不会正常进入可调用状态。

## 怎么解决

1. 把 `SKILL.md` 重新保存成 UTF-8 without BOM。
2. 确认文件头前 3 个字节是 `2D 2D 2D`。
3. 如果要检查完整开头，可以用：

```bash
xxd -l 16 research-paper-writing/SKILL.md
```

4. 正确结果应该像这样：

```text
2d 2d 2d 0a ...
```

5. 错误结果会像这样：

```text
ef bb bf 2d 2d 2d ...
```

6. 重新提交并推送到 GitHub。
7. 在 macOS 端重新拉取或刷新 Codex 的 skill 列表。

如果用 VS Code，可以这样处理：

1. 打开 `SKILL.md`
2. 点击右下角的编码信息
3. 选择 `Save with Encoding`
4. 选择 `UTF-8`
5. 重新保存

## 预防办法

这个仓库已经补了两层保护：

- `.editorconfig` 统一 `*.md` 和 `*.yaml` 的编码与换行
- GitHub Actions 会检查所有 `SKILL.md`，一旦发现 BOM 或不是以 `---` 开头就直接失败

## 适用范围

这个问题不是某一个 skill 独有的，而是所有带 frontmatter 的 `SKILL.md` 都可能受影响。

本仓库里已经核对过：

- `research-paper-writing/SKILL.md` 之前有 BOM，已经修复
- `paper-reading-analysis/SKILL.md` 没有 BOM

也就是说，问题的根源不是 skill 结构，而是 `SKILL.md` 的编码方式。
