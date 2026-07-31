# lipan.me

[李攀的博客](https://lipan.me)。Jekyll + GitHub Pages，推到 `master` 即自动部署。

## 本地预览

```bash
bundle install
bundle exec jekyll serve
# http://127.0.0.1:4000
```

装不上依赖时（系统 Ruby 太老），用 Homebrew 的 Ruby：

```bash
brew install ruby
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
```

## 写一篇新文章

在 `_posts/` 下新建 `YYYY-MM-DD-slug.md`：

```markdown
---
title: 标题
author: 李攀
layout: post
categories: [tech]
tags: [Kubernetes, 云原生]
---

正文……
```

- `categories` 只填一个，取值见 `_config.yml` 的 `categories_meta`：
  `tech`（技术）/ `team`（团队管理）/ `startup`（创业）/ `life`（随笔）。
  它决定文章在归档页的筛选归属。
- `tags` 随意填，文章底部会展示，点击跳到站内搜索。
- 图片放 `img/`，正文里用 `/img/xxx.png` 引用。
- 字数和阅读时长自动算，不用手写。

## 目录结构

| 路径 | 说明 |
| --- | --- |
| `_config.yml` | 站点信息、社交账号、分类定义、首页名片标签 |
| `_layouts/` | `default` / `post` / `page` 三个模板 |
| `_includes/` | `head` `header` `footer` `social` `entry-list` `cat-name` |
| `_sass/` | `_variables` 尺度字体、`_base` 色板与复位、`_layout` 组件、`_syntax-highlighting` 代码高亮 |
| `index.html` | 首页：个人名片 + 最近文章 |
| `archive/` | 全部文章 + 分类筛选 |
| `search/` + `search.json` | 纯前端站内搜索，索引在构建时生成 |
| `page2..5/` | 旧分页地址，重定向到归档页 |

## 改主题色

深浅两套色板都在 `_sass/_base.scss` 顶部，用 CSS 变量定义。
`--accent` 是强调色（朱红），改一个值全站生效。

## 注意

- `_config.yml` 里的 `permalink` 是**显式固定**的。Jekyll 默认的日期 permalink
  含 `:categories`，一旦去掉这行，所有文章 URL 都会变，历史链接和 SEO 全废。
- 样式由 GitHub Pages 的 Jekyll 3.9（libsass）编译，`_sass` 里不要用
  `@use` / `math.div` 等 Dart Sass 语法。
