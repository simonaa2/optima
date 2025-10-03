# Optima

A simple web application that can be deployed to Google Cloud App Engine or Cloud Run.

## Project Structure

- `app.yaml` - Google Cloud App Engine configuration
- `Dockerfile` - Docker configuration for Cloud Run deployment
- `nginx.conf` - Nginx server configuration
- `cloudbuild.yaml` - Google Cloud Build configuration
- `public/` - Static files served by the application
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

### Option 1: Google Cloud Run (using Docker)

To deploy using Cloud Build and Cloud Run:

1. Install the Google Cloud SDK: [https://cloud.google.com/sdk/docs/install](https://cloud.google.com/sdk/docs/install)
2. Initialize gcloud: `gcloud init`
3. Create a new project or select an existing one: `gcloud projects create [PROJECT_ID]` or `gcloud config set project [PROJECT_ID]`
4. Enable required APIs:
   ```bash
   gcloud services enable cloudbuild.googleapis.com run.googleapis.com
   ```
5. Submit the build to Cloud Build:
   ```bash
   gcloud builds submit --config cloudbuild.yaml
   ```

The `cloudbuild.yaml` configuration will:
- Build a Docker image from the Dockerfile
- Push the image to Google Container Registry
- Deploy the image to Cloud Run
- Make the service publicly accessible

**Note**: The deployment region is set to `us-central1` in `cloudbuild.yaml`. You can change this to a region closer to your users.

### Option 2: Google Cloud App Engine

To deploy directly to App Engine (without Docker):

1. Install the Google Cloud SDK: [https://cloud.google.com/sdk/docs/install](https://cloud.google.com/sdk/docs/install)
2. Initialize gcloud: `gcloud init`
3. Create a new project or select an existing one: `gcloud projects create [PROJECT_ID]` or `gcloud config set project [PROJECT_ID]`
4. Deploy: `gcloud app deploy`
5. View your application: `gcloud app browse`

**Note**: The first deployment will prompt you to select a region for your App Engine application. Choose the region closest to your users.

### Post-Deployment Configuration

After deploying your application, update the following files with your actual domain:

1. **public/sitemap.xml**: Update the `<loc>` tag with your actual domain URL
2. **public/robots.txt**: Uncomment and update the Sitemap URL with your actual domain

This ensures search engines can properly index your site.

## Development

The application serves a simple welcome page with a modern gradient design. All missing resources are handled gracefully to prevent 404 errors in server logs.

## Security

The application includes:
- Security headers (X-Content-Type-Options, X-Frame-Options, X-XSS-Protection)
- Robots.txt to discourage crawling of sensitive paths
- Proper handling of common security scan attempts