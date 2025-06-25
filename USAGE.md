# MemeJPG博客使用指南

这是一份详细的使用指南，帮助你管理和更新MemeJPG博客。

## 📋 目录

1. [环境准备](#环境准备)
2. [本地开发](#本地开发)
3. [创建文章](#创建文章)
4. [图片管理](#图片管理)
5. [部署流程](#部署流程)
6. [常见问题](#常见问题)
7. [高级配置](#高级配置)

## 🛠️ 环境准备

### 必需软件

1. **Node.js** (版本 16 或更高)
   - 下载地址：https://nodejs.org/
   - 验证安装：`node --version`

2. **Git**
   - 下载地址：https://git-scm.com/
   - 验证安装：`git --version`

3. **代码编辑器**
   - 推荐：VS Code, Sublime Text, 或 Atom

### 克隆项目

```bash
git clone https://github.com/your-username/memejpg-website.git
cd memejpg-website
npm install
```

## 💻 本地开发

### 启动开发服务器

```bash
# 启动本地服务器
npm run server

# 或者使用完整命令
npx hexo server
```

访问 http://localhost:4000 查看博客。

### 常用命令

```bash
# 清理缓存和生成的文件
npm run clean

# 生成静态文件
npm run build

# 创建新文章
npx hexo new post "文章标题"

# 创建新页面
npx hexo new page "页面名称"
```

## ✍️ 创建文章

### 方法一：使用命令行

```bash
npx hexo new post "我的第一个meme文章"
```

这会在 `source/_posts/` 目录下创建一个新的 `.md` 文件。

### 方法二：手动创建

在 `source/_posts/` 目录下创建新的 `.md` 文件，文件名格式：`文章标题.md`

### 文章模板

```markdown
---
title: 文章标题
date: 2024-12-19 10:00:00
categories: 
  - 表情包分类
tags:
  - 标签1
  - 标签2
  - 标签3
cover: /images/封面图片.jpg
excerpt: 这里是文章摘要，会显示在首页列表中
---

这里是文章的简短介绍，会显示在首页。

<!-- more -->

这里是文章的详细内容，只有点击"阅读更多"后才会显示。

## 小标题

可以使用各种Markdown语法：

- 列表项1
- 列表项2

![图片描述](/images/图片名称.jpg)

**粗体文字** 和 *斜体文字*

> 引用文字

```代码块```

---

*标签：#标签1 #标签2 #标签3*
```

### 文章分类建议

- **经典表情包** - 经典、知名度高的表情包
- **热门表情包** - 当前流行的表情包
- **动物表情包** - 以动物为主角的表情包
- **心理表情包** - 反映心理状态的表情包
- **节日表情包** - 节日相关的表情包
- **影视表情包** - 来自影视作品的表情包

### 标签使用规范

- 使用中文标签
- 每篇文章3-6个标签
- 标签要准确描述内容
- 避免过于宽泛的标签

## 🖼️ 图片管理

### 图片存放

所有图片都应该放在 `source/images/` 目录下。

### 图片命名规范

```
images/
├── covers/              # 封面图片
│   ├── drake-meme-cover.jpg
│   └── cat-meme-cover.jpg
├── posts/               # 文章内图片
│   ├── drake-pointing.jpg
│   └── cat-table.jpg
└── site/                # 网站图片
    ├── avatar.png
    └── logo.png
```

### 图片优化建议

1. **格式选择**
   - 照片：使用 JPG 格式
   - 图标/简单图形：使用 PNG 格式
   - 动图：使用 GIF 格式

2. **尺寸建议**
   - 封面图：800x400px
   - 文章内图片：最大宽度 800px
   - 缩略图：300x200px

3. **文件大小**
   - 单张图片不超过 500KB
   - 使用在线工具压缩：TinyPNG, Squoosh

### 在文章中使用图片

```markdown
# 基本语法
![图片描述](/images/图片名称.jpg)

# 带链接的图片
[![图片描述](/images/图片名称.jpg)](/images/大图.jpg)

# HTML语法（更多控制）
<img src="/images/图片名称.jpg" alt="图片描述" width="600">
```

## 🚀 部署流程

### 自动部署（推荐）

1. **提交代码**
```bash
git add .
git commit -m "添加新文章：文章标题"
git push origin main
```

2. **自动构建**
GitHub Actions会自动：
- 安装依赖
- 构建静态文件
- 部署到Cloudflare Pages

3. **查看结果**
- 访问 https://memejpg.pages.dev
- 或你的自定义域名

### 手动部署

如果需要手动部署：

```bash
# 清理并构建
npm run clean
npm run build

# 上传 public/ 目录到你的服务器
```

## ❓ 常见问题

### Q: 本地服务器启动失败

**A:** 检查以下几点：
1. Node.js版本是否正确（16+）
2. 是否运行了 `npm install`
3. 端口4000是否被占用
4. 配置文件是否有语法错误

### Q: 图片不显示

**A:** 检查：
1. 图片路径是否正确（以 `/images/` 开头）
2. 图片文件是否存在
3. 图片文件名是否包含特殊字符

### Q: 文章不显示

**A:** 检查：
1. 文件是否保存在 `source/_posts/` 目录
2. 文件扩展名是否为 `.md`
3. Front Matter格式是否正确
4. 日期格式是否正确

### Q: 部署失败

**A:** 检查：
1. GitHub Secrets是否正确设置
2. Cloudflare API Token是否有效
3. 构建日志中的错误信息

### Q: 字体显示过大或过小

**A:** 检查字体配置：
1. 编辑 `_config.next.yml` 文件
2. 找到 `font:` 配置部分
3. 如果字体过大，设置 `enable: false` 使用默认字体
4. 如果需要自定义，确保使用 `em` 单位而不是 `px`
5. 重新构建：`npm run clean && npm run build`

## ⚙️ 高级配置

### 自定义主题

编辑 `_config.next.yml` 文件来自定义主题：

```yaml
# 修改配色
scheme: Pisces

# 自定义菜单
menu:
  home: / || fa fa-home
  archives: /archives/ || fa fa-archive
  tags: /tags/ || fa fa-tags

# 添加社交链接
social:
  GitHub: https://github.com/username || fab fa-github
```

### SEO优化

1. **更新站点信息**
```yaml
# _config.yml
title: MemeJPG
description: 专门分享搞笑meme图片的博客
keywords: meme,搞笑图片,表情包
```

2. **添加Google Analytics**
```yaml
# _config.next.yml
google_analytics:
  tracking_id: GA_TRACKING_ID
```

### 性能优化

1. **启用压缩**
```yaml
# _config.next.yml
minify: true
```

2. **启用缓存**
```yaml
# _config.next.yml
cache:
  enable: true
```

## 📞 获取帮助

如果遇到问题：

1. 查看 [Hexo官方文档](https://hexo.io/docs/)
2. 查看 [Next主题文档](https://theme-next.js.org/)
3. 在GitHub仓库提交Issue
4. 联系维护者

---

**祝你使用愉快！** 🎉
