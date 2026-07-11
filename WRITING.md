# 写稿指南

博客使用 **Jekyll + Markdown**，文章保存在 `_posts/` 目录。

## 新建文章

在 `_posts/` 下创建文件，命名格式：

```text
YYYY-MM-DD-文章标题.md
```

示例 front matter：

```yaml
---
layout: post
title: "文章标题"
subtitle: "可选副标题"
author: "彩云"
date: 2026-07-11 10:00:00 +0800
header-img: img/post-sample-image.jpg
tags:
  - 标签一
  - 标签二
---

正文从这里开始……
```

## 推荐编辑方式

### 1. Cursor / VS Code（默认）

- 打开 `_posts/` 下的 `.md` 文件
- 使用 Markdown 预览（`Cmd + Shift + V`）
- 保存后 `./bin/dev` 自动刷新

### 2. Typora（所见即所得）

- 用 Typora 打开 `_posts/` 里的文件直接写
- 导出/保存为 Markdown 即可，与 Jekyll 完全兼容

### 3. Obsidian

- 适合先写思考笔记，再复制到 `_posts/` 发布

## 常用排版

```markdown
## 二级标题（会出现在右侧目录）

> 引用块

- 列表项

\`\`\`python
print("代码块")
\`\`\`
```

## 封面图

1. 将图片放入 `img/` 目录
2. 在 front matter 中设置：`header-img: img/your-image.jpg`

## 本地预览

```bash
./bin/dev
```

浏览器打开 http://localhost:4000

## 发布

```bash
git add .
git commit -m "新文章：标题"
git push
```

GitHub Actions 会自动构建并部署到 GitHub Pages。

## 启用评论（可选）

1. 在 GitHub 仓库开启 **Discussions**
2. 安装 [Giscus](https://giscus.app/zh-CN) 并获取 `repo_id`、`category_id`
3. 在 `_config.yml` 的 `giscus` 段填入 ID，并设置 `enabled: true`
