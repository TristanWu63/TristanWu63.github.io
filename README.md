# TristanWu63 的个人博客

基于 [yejianqin61-cell/nice-template](https://github.com/yejianqin61-cell/nice-template) 的 Jekyll 静态个人博客，保留原有页面与布局，用 Markdown 写文章。

- 博客地址：https://tristanwu63.github.io/
- 远程仓库：https://github.com/TristanWu63/TristanWu63.github.io
- 部署记录：https://github.com/TristanWu63/TristanWu63.github.io/actions

博客地址在首次推送并成功部署后可访问。当前个人简介与两篇起步文章为初始文案，可在首次提交前修改。

## 文件与内容

| 文件 | 用途 |
| --- | --- |
| `_config.yml` | 昵称、简介、GitHub 链接、博客网址和时区 |
| `index.html` | 首页、文章列表、项目与资源卡片 |
| `about.md` | 关于页 |
| `_posts/*.md` | Markdown 文章 |
| `_layouts/default.html` | 全站导航、页脚和页面信息 |
| `_layouts/post.html` | 文章布局 |
| `assets/style.css` | 蓝灰配色、排版、移动端样式 |
| `.github/workflows/pages.yml` | GitHub Actions 构建与部署 |

文章、样式与资源都在仓库中，不使用外部 CDN。电脑上只需 Git、GitHub CLI 和浏览器，不需要安装 Node.js、npm、Ruby 或本地 Jekyll。Jekyll 构建由 GitHub Actions 完成，不添加新的构建系统。

## 新增文章

在 `_posts/` 中新建 `YYYY-MM-DD-title.md`，保留现有 Front Matter：

```yaml
---
layout: post
title: 一篇新的学习笔记
date: 2026-10-10
excerpt: 用一句话介绍文章。
tags:
  - 学习
---
```

第二个 `---` 后写 Markdown 正文。文章链接采用 `/posts/title/`，首页自动显示最近六篇文章。未来日期的文章会等到日期到达后的下一次构建才出现；需要发布时推送一次修改或手动运行工作流。

站内资源使用 `relative_url`，跨文章引用使用 `{% post_url 2026-10-08-first-post %}`。图片可放在 `assets/images/`，例如：

```markdown
![图片说明]({{ '/assets/images/example.png' | relative_url }})
```

## 检查与预览

`index.html` 是含 Liquid 标签的 Jekyll 源码，双击不能看到最终页面。首次部署前检查 Front Matter、文件路径和 `git diff`；完整构建与最终网页检查在 GitHub Actions 部署后完成。

## 确认后首次提交和推送

在项目目录打开 PowerShell，先检查：

```powershell
git status --short
git remote -v
git diff --check
git diff
```

`origin` 应指向 `https://github.com/TristanWu63/TristanWu63.github.io.git`。`template` 保存原模板来源。新文件不会出现在普通 `git diff` 中，也应检查 `_posts/2026-10-10-writing-with-markdown.md` 和 `.gitignore`。

确认内容后执行：

```powershell
git add -- _config.yml index.html about.md assets/style.css _layouts/default.html _layouts/post.html _posts/2026-10-08-first-post.md _posts/2026-10-10-writing-with-markdown.md .github/workflows/pages.yml .gitignore README.md
git diff --cached --check
git diff --cached
git commit -m "Personalize Jekyll blog and configure GitHub Pages"
git push -u origin main
```

`origin` 是新建的空仓库，首次推送包含原模板历史和这次修改。无需强制推送。

## 自动发布

远程仓库 Pages 的 Source 使用 **GitHub Actions**。`.github/workflows/pages.yml` 在推送到 `main` 时构建和发布，也支持手动运行。

工作流沿用模板的官方 Pages Actions：checkout、configure-pages、jekyll-build-pages、upload-pages-artifact、deploy-pages。只有部署任务获得 `pages: write` 与 `id-token: write`；不需要手动设置 PAT、密码或自定义部署密钥。

首次推送后检查：

```powershell
gh run list --repo TristanWu63/TristanWu63.github.io --workflow pages.yml
```

在仓库的 Actions 页确认 build 和 deploy 均成功，再访问博客地址。网站尚未发布时出现 404 属于正常情况。

## 以后更新

修改 Markdown、HTML 或 CSS，检查变更后提交并推送到 `main`，工作流会更新博客。不要引入 React、Vue、Node.js、npm、外部 CDN 或新的构建工具，也不要重写整个模板。
