+++
date = '2026-06-29T00:50:52+08:00'
draft = false
title = '打造个人表情包与壁纸收集站'
tags = ['项目', '前端', 'Meme']
comments = true
+++

今天花了大半天时间，把个人网站体系又完善了一波。主要做了两件事：给博客加上了评论系统，以及新建了一个表情包壁纸收集站。

## Giscus 评论系统

之前一直想给博客加评论功能，但又不想自己搭后端。最后选了 Giscus，基于 GitHub Discussions，零成本。

配置过程其实挺简单的：
1. 在 GitHub 仓库开启 Discussions
2. 安装 Giscus App
3. 去 giscus.app 获取配置参数
4. 在 hugo.toml 里填入 `repoID` 和 `categoryID`

唯一要注意的是文章的 front matter 里要加 `comments = true` 才会显示评论区。

## 表情包壁纸站

新建了 meme.wjjblog.ccwu.cc，用来收集表情包和壁纸。

### 功能

- **分类浏览**：壁纸 / 表情包，表情包还细分为动图和静图
- **分页加载**：762 张壁纸一次性加载太慢，改成每次 50 张，点击"加载更多"
- **下载按钮**：鼠标悬停显示下载按钮
- **响应式布局**：瀑布流，手机电脑都适配

### 技术栈

纯静态站，HTML + CSS + JS，部署在 Cloudflare Pages 上。没有用任何框架，就是最基础的三件套。

### 壁纸来源

目前壁纸全部是战双帕米什的游戏壁纸，总共 762 张。后续可能会加上其他游戏或动漫的壁纸。

## 踩坑记录

1. **762 张图片 git push 太慢** — 分批提交，每批 15 张，花了好一会儿才推完
2. **Hugo 新建文章必须用 hugo new** — 用 write 工具直接创建的 .md 文件 Hugo 不识别
3. **Cloudflare 缓存** — 推送后要等 1-2 分钟才能看到更新

## 项目结构

现在我的网站体系是这样的：

| 网站 | 域名 | 说明 |
|------|------|------|
| 主站 | wjjblog.ccwu.cc | 个人主页 |
| 博客 | blog.wjjblog.ccwu.cc | 技术文章 |
| 表情包 | meme.wjjblog.ccwu.cc | 壁纸与表情包 |

三个站都部署在 Cloudflare Pages 上，免费又好用。

---

*Stay curious, keep learning.*
