# Noah Damski's Personal Website

A personal website built with Hugo, a fast and flexible static site generator, deployed automatically to GitHub Pages.

**Live site:** [https://ndamski.github.io/](https://ndamski.github.io/)

## Project Overview

This is a Hugo static site that serves as a personal portfolio and academic website. The site uses:
- **Hugo** for static site generation
- **GitHub Actions** for automated deployment
- **JSON data files** for structured content (education, experience, skills, research)
- **Custom layout templates** for rendering content
- **GitHub Pages** for hosting

## Prerequisites

Before you begin, make sure you have the following installed:

1. **Git** - Version control system
2. **Hugo Extended** (version 0.154.2 or compatible) - Static site generator
   - **Important:** You need the **Extended** version for Sass/SCSS support
3. **Go** (optional) - Hugo is built with Go, but not strictly required for basic usage

## Getting Started Locally

### 1. Clone the Repository
```bash
git clone https://github.com/ndamski/website.git
cd website
```

### 2. Install Hugo Extended
Follow the [official Hugo installation guide](https://gohugo.io/installation/) for your operating system.

Verify your Hugo installation:
```bash
hugo version
```
You should see something like: `hugo v0.154.2+extended` (note the "extended" suffix).

### 3. Run the Development Server
```bash
hugo server
```
This will start a local development server at `http://localhost:1313`. The site will automatically reload when you make changes to files.

### 4. Build the Site (for production)
```bash
hugo
```
This generates the static site files in the `public/` directory.

## Project Structure

```
website/
├── config/_default/           # Hugo configuration
│   ├── config.toml           # Site configuration (title, baseURL, etc.)
│   └── markup.toml           # Markdown and markup settings
├── data/                     # JSON data files for structured content
│   ├── education.json        # Education history
│   ├── experience.json       # Work experience
│   ├── skills.json           # Skills and competencies
│   └── research.json         # Research projects and publications
├── layouts/                  # HTML templates
│   └── index.html           # Homepage template
├── static/                   # Static assets
│   ├── img/                 # Images
│   │   └── favicon.png      # Site favicon
│   ├── Damski_Resume.pdf    # Resume PDF
│   └── ...                  # Other static files (research papers, etc.)
├── public/                   # Generated static site (created by Hugo)
├── .github/workflows/       # GitHub Actions workflows
│   └── deploy.yml           # Automated deployment to GitHub Pages
└── README.md                # This file
```

## Adding and Editing Content

### Editing Site Configuration
- **Site settings**: Edit `config/_default/config.toml`
- **Markdown settings**: Edit `config/_default/markup.toml`

### Updating Data Content
The site uses JSON files in the `data/` directory for structured content:

1. **Education**: Edit `data/education.json`
2. **Experience**: Edit `data/experience.json`
3. **Skills**: Edit `data/skills.json`
4. **Research**: Edit `data/research.json`

Example structure for education.json:
```json
[
  {
    "degree": "B.A. Economics",
    "college": "University of Florida",
    "description": "Relevant Coursework: Econometrics, Managerial Economics...",
    "range": "Aug. 2022 - May 2026"
  }
]
```

### Adding Static Files
- Place images in `static/img/`
- Place PDFs and other documents directly in `static/`
- Reference them in templates using `/filename.ext` (e.g., `/Damski_Resume.pdf`)

### Modifying Layouts
- The main homepage template is in `layouts/index.html`
- Hugo uses Go templates - refer to the [Hugo template documentation](https://gohugo.io/templates/) for syntax

## Deployment

### Automatic Deployment (GitHub Actions)
The site is automatically deployed to GitHub Pages using a GitHub Actions workflow (`.github/workflows/deploy.yml`):

1. **Trigger**: Pushes to `main` or `master` branch, or manual workflow dispatch
2. **Build Process**:
   - Checks out the repository
   - Installs Hugo Extended (v0.154.2), Dart Sass, and Node.js
   - Builds the site with Hugo
   - Deploys to GitHub Pages
3. **Configuration**: The workflow uses GitHub's `actions/deploy-pages` action

The live site is available at: `https://ndamski.github.io/`

### Manual Deployment
If you need to deploy manually:

1. Build the site:
   ```bash
   hugo
   ```
2. The generated files will be in the `public/` directory
3. You can deploy these files to any static hosting service

## Features and Configuration

### Current Configuration (`config.toml`)
- **Base URL**: `https://ndamski.github.io/`
- **Site Title**: "Noah Damski"
- **Language**: English (US)
- **Disabled Kinds**: Taxonomy and term pages (simplifies the site structure)
- **Favicon**: Located at `/img/favicon.png`

### Markup Features (`markup.toml`)
- **Goldmark renderer** with unsafe HTML (for embedding)
- **LaTeX math support** with `\[ \]`, `$$ $$`, and `\( \)` delimiters
- **Table of contents** with customizable levels
- **Code highlighting** with line numbers

## Troubleshooting

### Common Issues

1. **"hugo: command not found"**
   - Make sure Hugo is installed and in your PATH
   - Verify with `hugo version`

2. **"Error: failed to transform resource: TOCSS"**
   - You need Hugo **Extended** version, not the regular version
   - Install Hugo Extended: `brew install hugo` (macOS) or download from [Hugo releases](https://github.com/gohugoio/hugo/releases)

3. **Local site looks different from deployed site**
   - Clear Hugo cache: `hugo --gc`
   - Ensure you're using the same Hugo version (v0.154.2 Extended)

4. **GitHub Actions build fails**
   - Check the Actions tab in GitHub repository
   - Verify Hugo version compatibility in `.github/workflows/deploy.yml`

## Resources

- [Hugo Documentation](https://gohugo.io/documentation/)
- [Hugo Quick Start](https://gohugo.io/getting-started/quick-start/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

## License

This project is for personal use. Content is copyright Noah Damski.

---

*Last updated: April 2026*