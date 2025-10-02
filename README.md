# Optima

A simple web application hosted on Google Cloud App Engine.

## Project Structure

- `app.yaml` - Google Cloud App Engine configuration
- `public/` - Static files served by App Engine
  - `index.html` - Main application page
  - `404.html` - Custom 404 error page
  - `favicon.svg` - Application icon
  - `robots.txt` - Search engine crawler instructions
  - `sitemap.xml` - Site map for search engines

## App Engine Features

- **Rewrite Rules**: Automatically redirects `/favicon.ico` requests to `/favicon.svg`
- **SPA Support**: All routes are redirected to `index.html` for single-page application behavior
- **Security Headers**: Includes security headers for protection against common vulnerabilities
- **Caching**: Optimized caching for static assets
- **404 Handling**: Custom 404 page for better user experience

## Deployment

To deploy this application to Google Cloud App Engine:

1. Install the Google Cloud SDK: [https://cloud.google.com/sdk/docs/install](https://cloud.google.com/sdk/docs/install)
2. Initialize gcloud: `gcloud init`
3. Create a new project or select an existing one: `gcloud projects create [PROJECT_ID]` or `gcloud config set project [PROJECT_ID]`
4. Deploy: `gcloud app deploy`
5. View your application: `gcloud app browse`

**Note**: The first deployment will prompt you to select a region for your App Engine application. Choose the region closest to your users.

## Development

The application serves a simple welcome page with a modern gradient design. All missing resources are handled gracefully to prevent 404 errors in server logs.

## Security

The application includes:
- Security headers (X-Content-Type-Options, X-Frame-Options, X-XSS-Protection)
- Robots.txt to discourage crawling of sensitive paths
- Proper handling of common security scan attempts