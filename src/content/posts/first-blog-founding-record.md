---
title: 第一次博客搭建
published: 2026-04-06
tags: [测试]
category: 随笔
draft: false

---

# 第一次搭建博客全记录：从零到上线

> 使用 Astro + Fuwari 模板，通过 GitHub + Vercel 免费部署，无需服务器和备案。

主要参考这篇[文章](https://axi404.top/blog/website-vercel#/)

## 环境配置和工具

下载安装Node.js和Git

Node.js[官网](https://nodejs.org/zh-cn/download)

Git[官网](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)



## 1. 选择模板并 Fork 到自己的 GitHub

上github上找一个模版，我选的是Astro[Fuwari 模板仓库](https://github.com/saicaca/fuwari)

 **Fork** 到自己仓库 。



## 2. 克隆到本地

在本地创建一个合适的文件夹，打开终端执行：

bash

```
git clone https://github.com/你的用户名/fuwari.git
cd fuwari
```



## 3. 安装依赖并启动本地预览

项目使用 `pnpm` 作为包管理器，执行：

bash

```
pnpm install
pnpm dev
```



等待几秒后，终端会显示：

text

```
Local: http://localhost:4321/
```



浏览器打开这个地址，就能看到博客的默认样式，并且修改文件后会自动刷新。

## 4. 个性化配置

博客的全局信息都在 `src/config.ts` 文件中。

### 修改网站标题和副标题

找到 `siteConfig` 对象：

ts

```
siteConfig: {
  title: 'Fuwari',          // 改成你自己的博客名
  subtitle: 'A static blog template', // 改成你的副标题
}
```



### 修改导航栏菜单

找到 `navBarConfig`，修改 `links` 数组：

ts

```
navBarConfig: {
  links: [
    { name: '首页', url: '/' },
    { name: '归档', url: '/archive' },
    { name: '关于', url: '/about' },
  ],
}
```



### 修改作者信息和头像

找到 `profileConfig`：

ts

```
profileConfig: {
  name: 'Your Name',        // 改成你的名字
  avatar: '/avatar.png',    // 把头像一个 png 图片放到 public 目录下
}
```



### 修改主题色

在 `siteConfig` 中调整 `themeColor.hue` 的数值（0~360）。

## 5. 创建“关于”页面

在 `src/content/spec/` 目录下新建 `about.md`，内容示例：

markdown

```
---
title: 关于我
layout: ../../layouts/PageLayout.astro
---

## 你好，我是 [你的名字]

欢迎来到我的博客。这里会记录技术学习、生活思考等内容。

你可以通过 [邮箱](mailto:your@email.com) 联系我。
```



## 6. 写第一篇文章

在终端运行：

bash

```
pnpm new-post hello-world
```



在 `src/content/posts/hello-world.md` 中编写：

markdown

```
---
title: 我的第一篇博客
published: 2025-04-06
tags: [随笔]
category: 生活
---

终于搭好了自己的博客！这里以后会分享技术、阅读和日常。
```



## 7. 提交代码到 GitHub

bash

```
git add .
git commit -m "初始化博客配置和第一篇文章"
git push origin main
```



## 8. 部署到 Vercel

- 登录 [Vercel](https://vercel.com/)，使用 GitHub 账号登录。
- 点击 **Add New → Project**，在列表中找到 `fuwari` 仓库，点击 **Import**。
- 保持默认设置，点击 **Deploy**。
- 等待约 30 秒，得到 `.vercel.app` 域名，例如 `fuwari-xxx.vercel.app`。



## 9. （可选）绑定自己的域名

- 在 Namecheap 或 Namesilo 购买域名。
- 在 Vercel 项目设置 → Domains 中添加域名，获取 DNS 记录。
- 在域名服务商处添加 CNAME 记录指向 `cname.vercel-dns.com`。
- 等待解析生效。

## 10. 后续更新流程

以后每次更新：

1. 本地编辑（运行 `pnpm dev` 实时预览）
2. `git add . && git commit -m "更新内容"`
3. `git push origin main`

Vercel 自动重新部署，约 30 秒后线上更新。

------

**最终效果**：一个完全属于自己的、免费的、访问快速的博客，支持 Markdown

