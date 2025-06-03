# Deployment Guide

This guide explains how to deploy the AI Agents Presentation to various hosting platforms.

## 🚀 Deployment Options

### 1. GitHub Pages (Recommended)

GitHub Pages provides free hosting for static websites directly from your GitHub repository.

#### Automatic Deployment
This repository includes a GitHub Actions workflow that automatically deploys to GitHub Pages when you push to the main branch.

**Setup Steps:**
1. Fork or clone this repository
2. Go to your repository settings
3. Navigate to "Pages" section
4. Select "GitHub Actions" as the source
5. Push any changes to trigger deployment

#### Manual Deployment
1. Go to repository Settings → Pages
2. Select "Deploy from a branch"
3. Choose "main" branch and "/ (root)" folder
4. Click Save

**Your site will be available at:** `https://yourusername.github.io/ai-agents-presentation`

### 2. Netlify

Netlify offers easy deployment with continuous integration.

**Steps:**
1. Sign up at [netlify.com](https://netlify.com)
2. Connect your GitHub repository
3. Set build command: `echo "No build required"`
4. Set publish directory: `.` (root)
5. Deploy

**Features:**
- Automatic deployments on git push
- Custom domain support
- Form handling
- Edge functions

### 3. Vercel

Vercel provides fast deployment with global CDN.

**Steps:**
1. Sign up at [vercel.com](https://vercel.com)
2. Import your GitHub repository
3. No build configuration needed
4. Deploy

**Features:**
- Automatic deployments
- Custom domains
- Analytics
- Edge functions

### 4. Firebase Hosting

Google Firebase offers reliable hosting with CDN.

**Steps:**
1. Install Firebase CLI: `npm install -g firebase-tools`
2. Login: `firebase login`
3. Initialize: `firebase init hosting`
4. Configure `firebase.json`:
   ```json
   {
     "hosting": {
       "public": ".",
       "ignore": [
         "firebase.json",
         "**/.*",
         "**/node_modules/**"
       ]
     }
   }
   ```
5. Deploy: `firebase deploy`

### 5. AWS S3 + CloudFront

For enterprise deployments with AWS infrastructure.

**Steps:**
1. Create S3 bucket with static website hosting
2. Upload all files to the bucket
3. Configure CloudFront distribution
4. Set up custom domain (optional)

### 6. Local Development Server

For local development and testing:

**Using Python:**
```bash
python -m http.server 8000
```

**Using Node.js:**
```bash
npx serve . -p 8000
```

**Using PHP:**
```bash
php -S localhost:8000
```

## 🔧 Configuration

### Custom Domain
To use a custom domain:

1. **GitHub Pages:** Add a `CNAME` file with your domain
2. **Netlify:** Configure in site settings
3. **Vercel:** Add domain in project settings
4. **Firebase:** Configure in `firebase.json`

### Environment Variables
This is a static site, so no environment variables are needed. All configuration is in the HTML/CSS/JS files.

### Performance Optimization

**For production deployment:**
- Enable gzip compression
- Set up CDN
- Configure caching headers
- Optimize images
- Minify CSS/JS (optional)

## 📊 Analytics

To add analytics to your deployment:

### Google Analytics
Add this to the `<head>` section of `index.html`:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_TRACKING_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_TRACKING_ID');
</script>
```

### Plausible Analytics
Add this to the `<head>` section:
```html
<script defer data-domain="yourdomain.com" src="https://plausible.io/js/script.js"></script>
```

## 🔒 Security

### Content Security Policy
Add CSP headers for enhanced security:
```html
<meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self' 'unsafe-inline' https://cdn.jsdelivr.net https://cdnjs.cloudflare.com; style-src 'self' 'unsafe-inline' https://cdn.jsdelivr.net https://cdnjs.cloudflare.com; font-src 'self' https://cdnjs.cloudflare.com;">
```

### HTTPS
Always use HTTPS in production:
- GitHub Pages: Automatic HTTPS
- Netlify: Automatic HTTPS
- Vercel: Automatic HTTPS
- Custom hosting: Configure SSL certificate

## 🐛 Troubleshooting

### Common Issues

**404 Errors:**
- Check file paths are correct
- Ensure all files are uploaded
- Verify server configuration

**CSS/JS Not Loading:**
- Check CDN links are accessible
- Verify file paths
- Check browser console for errors

**Mobile Display Issues:**
- Test responsive design
- Check viewport meta tag
- Verify touch interactions

### Support
If you encounter deployment issues:
1. Check the [Issues](https://github.com/yourusername/ai-agents-presentation/issues) page
2. Create a new issue with deployment details
3. Include error messages and browser console output

---

Happy deploying! 🚀

