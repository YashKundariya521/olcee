
```
/
├── index.html            # Homepage
├── about.html            # About Us page
├── contact.html          # Contact Us page
├── privacy.html          # Privacy Policy page
├── terms.html            # Terms of Service page
├── css/
│   └── style.css         # Main stylesheet
├── js/
│   └── script.js         # Main JavaScript file
├── images/               # Image assets (favicons, logos, banners, product images)
│   ├── product-ecoserve.jpg (example)
│   └── ...               # Other images (og-image.jpg, favicon.ico, etc.)
├── products/             # Directory for product detail pages
│   ├── ecoserve.html
│   ├── writeon.html
│   ├── flexifoil.html
│   ├── bubblex.html
│   └── scrubbpro.html
├── AGENTS.md             # Guidelines for AI development agents
├── README.md             # This file
└── robots.txt            # Instructions for web crawlers
```

## Setup and Local Development

No special build process is required for local development.

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```
2.  **Open HTML files in a browser:**
    You can open `index.html` or any other HTML file directly in your web browser to view the website locally.
    For example, on macOS: `open index.html`
    On Windows/Linux: Navigate to the directory and double-click the file, or use `xdg-open index.html` (Linux).

3.  **Using a local server (Recommended for full functionality like fetch API):**
    Some browser features (like `fetch` API calls for the contact form, though it's to an external service) behave more reliably when files are served by a web server. You can use simple local servers:
    *   **Using Python's HTTP server (Python 3):**
        ```bash
        python -m http.server
        ```
        Then open `http://localhost:8000` in your browser.
    *   **Using Node.js `http-server` package:**
        First, install it globally if you haven't: `npm install -g http-server`
        Then run in the project root:
        ```bash
        http-server
        ```
        Then open the URL shown (usually `http://localhost:8080`).
    *   **Using VS Code Live Server extension:** If you use VS Code, the "Live Server" extension is a convenient way to serve files locally.

## Key Configuration Points

### Contact Form
- The contact form in `contact.html` is configured to submit data to Formspree.
- **Action Required Before Deployment:** You **must** replace the placeholder Formspree URL in `contact.html`:
  ```html
  <form id="contact-form" action="https://formspree.io/f/YOUR_FORM_ID_HERE" method="POST">
  ```
  Replace `YOUR_FORM_ID_HERE` with your actual Formspree form ID after setting up a form on formspree.io.

### Image Assets
- All image paths are relative (e.g., `images/hero-banner.jpg`, `../images/product-banner-ecoserve.jpg`).
- **Action Required Before Deployment:** Ensure all placeholder images referenced in the HTML are replaced with actual, optimized image files in the `images/` directory. This includes:
    - General site images (logos, favicons, Open Graph images like `og-image.jpg`).
    - Hero banner images.
    - Product card images for the homepage.
    - Product banner and gallery images for each product page.
    - Any images on the About page.
- Optimize images for web (compress, resize, use appropriate formats like WebP if desired and supported by target audience, otherwise JPG/PNG).

### Multilingual Support
- The site includes a language switcher (EN, HI, AR).
- Basic `lang` and `dir` attribute switching is implemented in `js/script.js`.
- CSS includes `html[dir="rtl"]` styles for Arabic.
- **Actual content translation is not implemented.** To achieve full translation, you would need to:
    1.  Integrate a JavaScript-based translation API (e.g., Google Cloud Translation API).
    2.  Or, create separate static translated versions of each page (e.g., `index.hi.html`, `index.ar.html`) and update the language switcher to navigate to these pages.

## Build Process (Manual Optimizations)

Before deployment, consider these manual optimization steps if not using an automated build tool:

1.  **Minify CSS:**
    Use an online tool or a CLI tool like `csso-cli` to minify `css/style.css`.
    Example: `csso style.css -o style.min.css` (then update the link in HTML).
2.  **Minify JavaScript:**
    Use an online tool or a CLI tool like `terser` to minify `js/script.js`.
    Example: `terser script.js -o script.min.js -c -m` (then update the link in HTML).
3.  **Image Optimization:** As mentioned above, ensure all images are compressed and appropriately sized.

## Deployment

This is a static website, so it can be deployed to any static web hosting provider.

1.  **Choose a Hosting Provider:**
    Examples: GitHub Pages, Netlify, Vercel, Google Cloud Storage, AWS S3, Azure Static Web Apps, or any traditional web host.

2.  **Deployment Steps (General):**
    *   **Prepare files:** Ensure all necessary files (HTML, minified CSS/JS, optimized images) are ready.
    *   **Upload files:** Use the hosting provider's interface or CLI tools (e.g., `git push` for GitHub Pages/Netlify/Vercel, `gsutil` for GCS, `aws s3 sync` for S3) to upload the website files to the hosting server.
    *   **Configure Domain:** Point your custom domain (`olcee.com`) to the hosting provider. This usually involves updating DNS records (e.g., A, CNAME) with your domain registrar.
    *   **Enable HTTPS:** Ensure an SSL/TLS certificate is installed and HTTPS is enforced. Most modern static hosting providers offer free automated SSL certificates (e.g., via Let's Encrypt).

### Example: Deploying to GitHub Pages
1.  Ensure your repository is on GitHub.
2.  Go to your repository's "Settings" tab.
3.  Scroll down to the "Pages" section.
4.  Choose the branch to deploy from (e.g., `main` or `master`) and the `/ (root)` folder.
5.  Save. GitHub Actions will build and deploy your site.
6.  Configure your custom domain (`olcee.com`) in the GitHub Pages settings. This will involve adding CNAME/A records to your DNS provider. GitHub Pages provides free HTTPS for custom domains.

### Example: Deploying to Netlify/Vercel
1.  Sign up for Netlify or Vercel.
2.  Connect your Git repository.
3.  Configure build settings (usually auto-detected for static sites; no build command needed for this project).
4.  Deploy.
5.  Add your custom domain (`olcee.com`) through their dashboard and follow DNS configuration instructions. They provide free automated SSL.

## Testing

Refer to the "Testing" plan step for details on:
- Cross-browser testing
- Responsive design testing
- Functionality testing (navigation, forms, language switcher)
- Accessibility testing (WCAG 2.1 AA)
- Performance testing
- Content review and validation

Use browser developer tools, online validators, and tools like Lighthouse and Axe DevTools for comprehensive testing.

---

This README provides a basic guide for understanding, developing, and deploying the Olcee International website.
```
