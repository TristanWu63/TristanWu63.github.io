---
layout: default
title: 关于我
permalink: /about.html
---

<section class="wrap section about" aria-labelledby="about-title">
  <div><p class="eyebrow">A little about me</p><h1 id="about-title">关于我</h1><div class="rule"></div></div>
  <div class="about-note">
    <p>你好，我是 {{ site.author.name | escape }}。{{ site.author.bio | escape }}</p>
    <p>这个博客是一个慢慢生长的个人空间：记录一个问题怎样被解决，也记录尚未想清楚的部分。不追求一次写完，先把值得留下的内容写下来。</p>
    <ul class="tag-list"><li>学习笔记</li><li>静态网页</li><li>Markdown</li><li>持续写作</li></ul>
    <p><a href="{{ site.author.github_url | escape }}">我的 GitHub</a> · <a href="{{ site.author.repository_url | escape }}">博客源码</a></p>
  </div>
</section>
