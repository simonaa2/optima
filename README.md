# Optima

A simple web application hosted on Firebase.

## Project Structure

- `firebase.json` - Firebase hosting configuration
- `.firebaserc` - Firebase project configuration
- `public/` - Static files served by Firebase hosting
  - `index.html` - Main application page
  - `404.html` - Custom 404 error page
  - `favicon.svg` - Application icon
  - `robots.txt` - Search engine crawler instructions
  - `sitemap.xml` - Site map for search engines

## Firebase Hosting Features

- **Rewrite Rules**: Automatically redirects `/favicon.ico` requests to `/favicon.svg`
- **SPA Support**: All routes are redirected to `index.html` for single-page application behavior
- **Security Headers**: Includes security headers for protection against common vulnerabilities
- **Caching**: Optimized caching for static assets
- **404 Handling**: Custom 404 page for better user experience

## Deployment

To deploy this application to Firebase:

1. Install the Firebase CLI: `npm install -g firebase-tools`
2. Login to Firebase: `firebase login`
3. Deploy: `firebase deploy`

## Development

The application serves a simple welcome page with a modern gradient design. All missing resources are handled gracefully to prevent 404 errors in server logs.

## Security

The application includes:
- Security headers (X-Content-Type-Options, X-Frame-Options, X-XSS-Protection)
- Robots.txt to discourage crawling of sensitive paths
- Proper handling of common security scan attempts