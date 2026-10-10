---
layout: post
title: 用 Markdown 维护这个博客
date: 2026-10-10
excerpt: 写一篇文章，只需要一个 Markdown 文件；发布交给 GitHub Pages。
tags:
  - 写作
  - Markdown
---

这个博客采用 Jekyll 模板，文章保存在 `_posts` 文件夹中。页面样式和文章内容分开维护，写作时可以专注于文字。

## 新建一篇文章

文章文件名采用 `YYYY-MM-DD-title.md` 格式，例如 `2026-10-10-reading-notes.md`。文件开头保留下面的 Front Matter：

```yaml
---
layout: post
title: 一篇新的阅读笔记
date: 2026-10-10
excerpt: 用一句话介绍这篇文章。
tags:
  - 阅读
---
```

第二个 `---` 后面就是正文。可以写标题、段落、列表和代码块。

## 从清楚的结构开始

我喜欢让一篇笔记包含三个部分：背景、尝试和收获。短文章也可以有结构，方便以后回看。

> 先写清楚一件事，再逐步补充细节。

需要引用另一篇文章时，可以用 Jekyll 的文章链接标签。下面的链接会在构建时检查目标文章是否存在：

[读读博客的第一篇文章]({% post_url 2026-10-08-first-post %})。

## 写好以后怎样发布

先检查正文、日期、链接和 Git diff，再提交并推送到博客仓库的 `main` 分支。GitHub Actions 会运行已有的 Jekyll 构建和 Pages 部署工作流。

构建在 GitHub 上完成，本地编辑 Markdown、HTML 和 CSS 即可。部署成功后，新的文章就会出现在首页。

想了解模板和项目，可以访问[关于我]({{ '/about.html' | relative_url }})，或查看[博客源码]({{ site.author.repository_url }})。
