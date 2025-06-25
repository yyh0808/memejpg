# MemeJPG - Funny Meme Collection Blog

A dedicated Hexo blog for sharing hilarious memes, using the Next theme and deployed on Cloudflare Pages.

## 🚀 Quick Start

### Local Development

1. Clone the repository
```bash
git clone <your-repo-url>
cd memejpg-website
```

2. Install dependencies
```bash
npm install
```

3. Start local server
```bash
npm run server
```

4. Visit http://localhost:4000

### Build and Deploy

```bash
# Clean cache
npm run clean

# Generate static files
npm run build
```

## 📝 How to Update the Blog

### 1. Create New Posts

```bash
hexo new post "Post Title"
```

Or directly create new `.md` files in the `source/_posts/` directory.

### 2. Post Format

Each post should include the following front matter:

```yaml
---
title: Post Title
date: 2024-12-19 10:00:00
categories:
  - Category Name
tags:
  - Tag1
  - Tag2
cover: /images/cover-image.jpg
---

Post excerpt content...

<!-- more -->

Post main content...
```

### 3. Adding Images

1. Place images in the `source/images/` directory
2. Reference them in posts using relative paths: `![Image Description](/images/image-name.jpg)`

### 4. Push Updates

```bash
git add .
git commit -m "Add new post: Post Title"
git push origin main
```

After pushing, GitHub Actions will automatically build and deploy to Cloudflare Pages.

## 🛠️ Configuration

### Main Configuration Files

- `_config.yml` - Hexo main configuration
- `_config.next.yml` - Next theme configuration
- `.github/workflows/deploy.yml` - GitHub Actions deployment configuration

### Cloudflare Pages Deployment

Set up the following in GitHub repository Settings > Secrets:

- `CLOUDFLARE_API_TOKEN` - Cloudflare API token
- `CLOUDFLARE_ACCOUNT_ID` - Cloudflare account ID

### Custom Domain

Configure custom domain in Cloudflare Pages project settings.

## 📁 Directory Structure

```
memejpg-website/
├── .github/workflows/     # GitHub Actions configuration
├── source/               # Source files directory
│   ├── _posts/          # Posts directory
│   ├── images/          # Images directory
│   ├── tags/            # Tags page
│   └── categories/      # Categories page
├── themes/next/         # Next theme files
├── _config.yml          # Hexo configuration
├── _config.next.yml     # Next theme configuration
└── package.json         # Dependencies configuration
```

## 🎨 Theme Features

- Responsive design with mobile support
- Image lazy loading and zoom functionality
- Local search functionality
- SEO optimization
- Social media sharing
- Code highlighting
- Math formula support (optional)

## 📊 SEO Optimization

The blog is configured with:
- Sitemap generation
- RSS feed
- Search engine optimization
- Open Graph tags
- Structured data

## 🤝 Contributing

1. Fork this repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License

MIT License

## 🔗 Related Links

- [Hexo Documentation](https://hexo.io/docs/)
- [Next Theme Documentation](https://theme-next.js.org/)
- [Cloudflare Pages Documentation](https://developers.cloudflare.com/pages/)

---

**Enjoy creating hilarious content!** 🎉
