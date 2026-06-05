# Installation & Setup Guide

## Prerequisites

- Node.js v16 or higher
- npm v8 or higher
- Angular CLI 16+
- A modern web browser

## Installation Steps

### 1. Install Node.js and npm

Download from [https://nodejs.org/](https://nodejs.org/)

Verify installation:
```bash
node --version
npm --version
```

### 2. Install Angular CLI

```bash
npm install -g @angular/cli
```

### 3. Clone/Download the Project

```bash
cd todo-app
```

### 4. Install Dependencies

```bash
npm install
```

### 5. Start Development Server

```bash
ng serve
```

or

```bash
npm start
```

### 6. Access the Application

Open your browser and navigate to:
```
http://localhost:4200
```

## Build for Production

```bash
ng build --configuration production
```

This creates an optimized build in the `dist/` directory.

## Running Tests

```bash
ng test
```

## Deployment

### Deploy to GitHub Pages

```bash
# Build for production
ng build --configuration production

# Deploy
npm run deploy
```

### Deploy to Netlify

1. Connect your GitHub repository to Netlify
2. Set build command: `ng build --configuration production`
3. Set publish directory: `dist/todo-app`

### Deploy to Vercel

```bash
npm install -g vercel
vercel
```

### Deploy to AWS S3 + CloudFront

```bash
# Build the app
ng build --configuration production

# Upload to S3
aws s3 sync dist/todo-app s3://your-bucket-name

# Invalidate CloudFront
aws cloudfront create-invalidation --distribution-id your-distribution-id --paths "/*"
```

## Configuration

### Environment Variables

Create `src/environments/environment.prod.ts`:

```typescript
export const environment = {
  production: true
};
```

### Storage Quota

The application uses browser local storage (~5-10MB limit):
- Check available storage
- Export data if storage is low
- Clear old/completed tasks

## Troubleshooting

### Issue: Port 4200 already in use

```bash
ng serve --port 4300
```

### Issue: npm packages not installing

```bash
# Clear npm cache
npm cache clean --force

# Delete node_modules and package-lock.json
rm -rf node_modules package-lock.json

# Reinstall
npm install
```

### Issue: Angular CLI not found

```bash
npm install -g @angular/cli@16
```

### Issue: Build failing

```bash
# Check TypeScript version
npm list typescript

# Update to compatible version
npm install --save-dev typescript@~5.1.6
```

## Development Commands

```bash
# Start dev server
ng serve

# Build for production
ng build

# Run tests
ng test

# Run linting
ng lint

# Generate component
ng generate component components/my-component

# Generate service
ng generate service services/my-service
```

## Browser Compatibility

- Chrome/Chromium 60+
- Firefox 55+
- Safari 11+
- Edge 15+
- Mobile browsers (iOS Safari, Chrome Mobile)

## Performance Tips

1. **Enable Gzip Compression**: Most servers do this automatically
2. **Use CDN**: Serve static assets from a CDN
3. **Browser Caching**: Set appropriate cache headers
4. **Minification**: Automatically done in production build
5. **Lazy Loading**: Implement for future feature modules

## Security Considerations

1. **HTTPS**: Always use HTTPS in production
2. **CSP**: Implement Content Security Policy headers
3. **XSS Protection**: Angular built-in XSS protection
4. **Data Validation**: All user input is validated
5. **Local Storage**: Sensitive data should be encrypted

## Backup & Recovery

### Export Data
```typescript
// In the app
Click: 📥 Export
Save the JSON file
```

### Import Data
```typescript
// In the app
Click: 📤 Import
Select the JSON file
```

### Manual Backup (Browser DevTools)
```javascript
// In browser console
const tasks = JSON.stringify(JSON.parse(localStorage.getItem('todoAppTasks')), null, 2);
console.log(tasks);
// Copy output to a file
```

## Support & Resources

- [Angular Documentation](https://angular.io)
- [TypeScript Handbook](https://www.typescriptlang.org/docs)
- [MDN Web Docs](https://developer.mozilla.org)
- [Stack Overflow](https://stackoverflow.com)

## Next Steps

1. Customize categories and colors in the app
2. Export your first task list
3. Try the dark mode
4. Export and backup regularly
5. Share feedback and feature requests
