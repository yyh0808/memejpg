# MemeJPG博客部署指南

本指南将帮助你将MemeJPG博客部署到Cloudflare Pages，并设置自动化部署流程。

## 🚀 部署到Cloudflare Pages

### 步骤1：准备GitHub仓库

1. **创建GitHub仓库**
   - 登录GitHub，创建新仓库
   - 仓库名建议：`memejpg-website`
   - 设置为Public（免费用户）

2. **上传代码**
```bash
# 初始化Git仓库
git init
git add .
git commit -m "Initial commit: MemeJPG博客"

# 添加远程仓库
git remote add origin https://github.com/your-username/memejpg-website.git
git branch -M main
git push -u origin main
```

### 步骤2：设置Cloudflare Pages

1. **登录Cloudflare**
   - 访问 https://dash.cloudflare.com/
   - 登录或注册账户

2. **创建Pages项目**
   - 点击左侧菜单 "Pages"
   - 点击 "Create a project"
   - 选择 "Connect to Git"

3. **连接GitHub**
   - 授权Cloudflare访问GitHub
   - 选择 `memejpg-website` 仓库

4. **配置构建设置**
   ```
   Project name: memejpg-website
   Production branch: main
   Build command: npm run build
   Build output directory: public
   Root directory: /
   ```

5. **环境变量**（可选）
   - 如果需要，可以设置环境变量
   - 例如：`NODE_VERSION=18`

### 步骤3：配置GitHub Secrets

为了使GitHub Actions正常工作，需要设置以下Secrets：

1. **获取Cloudflare API Token**
   - 访问 https://dash.cloudflare.com/profile/api-tokens
   - 点击 "Create Token"
   - 使用 "Custom token" 模板
   - 权限设置：
     - Zone: Zone:Read, Zone Settings:Read
     - Account: Cloudflare Pages:Edit

2. **获取Account ID**
   - 在Cloudflare仪表板右侧找到 "Account ID"
   - 复制这个ID

3. **在GitHub设置Secrets**
   - 进入GitHub仓库
   - Settings > Secrets and variables > Actions
   - 添加以下Secrets：
     - `CLOUDFLARE_API_TOKEN`: 你的API Token
     - `CLOUDFLARE_ACCOUNT_ID`: 你的Account ID

### 步骤4：测试部署

1. **推送代码触发部署**
```bash
git add .
git commit -m "Test deployment"
git push origin main
```

2. **查看部署状态**
   - GitHub: Actions标签页查看构建状态
   - Cloudflare: Pages项目页面查看部署状态

3. **访问网站**
   - 默认域名：`https://memejpg-website.pages.dev`
   - 或你设置的自定义域名

## 🌐 自定义域名设置

### 步骤1：添加域名

1. **在Cloudflare Pages中**
   - 进入项目设置
   - 点击 "Custom domains"
   - 点击 "Set up a custom domain"

2. **输入域名**
   - 例如：`memejpg.com` 或 `blog.memejpg.com`

### 步骤2：配置DNS

如果域名在Cloudflare管理：
- 系统会自动添加CNAME记录

如果域名在其他服务商：
- 添加CNAME记录指向 `memejpg-website.pages.dev`

### 步骤3：SSL证书

- Cloudflare会自动为自定义域名提供SSL证书
- 通常在几分钟内生效

## 🔧 高级配置

### 预览部署

Cloudflare Pages会为每个Pull Request创建预览部署：
- 预览URL格式：`https://[commit-hash].memejpg-website.pages.dev`
- 可以在合并前测试更改

### 环境变量

在Cloudflare Pages设置环境变量：
1. 进入项目设置
2. 点击 "Environment variables"
3. 添加变量（如Google Analytics ID）

### 重定向规则

创建 `public/_redirects` 文件：
```
# 重定向示例
/old-url /new-url 301
/blog/* /posts/:splat 301
```

### 自定义头部

创建 `public/_headers` 文件：
```
/*
  X-Frame-Options: DENY
  X-XSS-Protection: 1; mode=block
  X-Content-Type-Options: nosniff
```

## 📊 性能优化

### 图片优化

1. **使用Cloudflare Images**（付费功能）
   - 自动压缩和格式转换
   - 响应式图片

2. **手动优化**
   - 使用WebP格式
   - 压缩图片大小
   - 设置合适的尺寸

### 缓存设置

Cloudflare自动处理缓存，但可以优化：
1. 设置Page Rules
2. 配置Browser Cache TTL
3. 启用Always Online

### CDN加速

- Cloudflare全球CDN自动加速
- 支持HTTP/2和HTTP/3
- 自动压缩静态资源

## 🔍 监控和分析

### Cloudflare Analytics

- 访问量统计
- 性能指标
- 安全事件

### Google Analytics

在 `_config.next.yml` 中配置：
```yaml
google_analytics:
  tracking_id: GA_TRACKING_ID
```

### 搜索引擎优化

1. **提交站点地图**
   - Google Search Console
   - Bing Webmaster Tools
   - 站点地图URL：`https://your-domain.com/sitemap.xml`

2. **robots.txt**
   - 自动生成在 `/robots.txt`

## 🚨 故障排除

### 常见问题

1. **构建失败**
   - 检查Node.js版本
   - 查看构建日志
   - 验证package.json

2. **404错误**
   - 检查文件路径
   - 验证构建输出目录

3. **样式丢失**
   - 检查CSS文件路径
   - 验证主题配置

### 调试技巧

1. **本地测试**
```bash
npm run clean
npm run build
npm run server
```

2. **查看日志**
   - GitHub Actions日志
   - Cloudflare Pages部署日志

3. **检查配置**
   - 验证YAML语法
   - 检查文件权限

## 📞 获取帮助

- [Cloudflare Pages文档](https://developers.cloudflare.com/pages/)
- [GitHub Actions文档](https://docs.github.com/en/actions)
- [Hexo文档](https://hexo.io/docs/)

---

**祝你部署成功！** 🎉
