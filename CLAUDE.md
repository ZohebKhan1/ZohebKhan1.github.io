# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an academic personal website for Zoheb Khan (Bioinformatician at Moskowitz Lab, The University of Chicago) built using the Hugo static site generator with the Wowchemy Academic theme. The template originates from https://github.com/prasenjit52282/prasenjit52282.github.io with custom CSS adapted from nickballousite.

**Owner Information:**
- Name: Zoheb Khan
- Position: Bioinformatician at Moskowitz Lab, The University of Chicago
- Email: zohebk@uchicago.edu
- Education: B.A. in Genetics, University of Chicago (June 2022)
- Lab: https://moskowitzlab.uchicago.edu/
- GitHub: https://github.com/ZohebKhan1
- Google Scholar: https://scholar.google.com/citations?user=2gFbtqIAAAAJ&hl=en
- ResearchGate: https://www.researchgate.net/profile/Zoheb-Khan-7

**Research Focus:** Bulk RNA-seq analysis, developmental biology, Trisomy 21/Down syndrome, cardiac development, hedgehog signaling pathways, iPSC cortical neuron differentiation.

## Repository Structure

```
template/                         # Hugo site root
├── config/_default/              # Configuration files
│   ├── config.yaml              # Main config (title, baseURL, theme modules)
│   ├── params.yaml              # Site parameters (contact info, features, theme settings)
│   ├── menus.yaml               # Navigation menu structure
│   └── languages.yaml           # Language settings
├── content/                      # Site content
│   ├── authors/admin/           # Profile information
│   │   ├── _index.md           # Bio, interests, education, social links
│   │   └── avatar.jpg          # Profile photo (copy from src/personal_photo.png)
│   ├── publication/             # Publications (each in its own folder)
│   │   └── [pub-slug]/
│   │       ├── index.md        # Publication metadata and abstract
│   │       ├── cite.bib        # BibTeX citation (optional)
│   │       └── featured.jpg    # Featured image (optional)
│   ├── project/                 # Research projects
│   ├── blog/                    # Blog posts
│   ├── event/                   # Talks/presentations
│   ├── news/                    # News items
│   └── home/                    # Homepage widgets/sections
│       ├── about.md            # About section (links to admin profile)
│       ├── experience.md       # Work experience timeline
│       ├── publications.md     # Publications list
│       ├── projects.md         # Projects showcase
│       ├── contact.md          # Contact form
│       ├── accomplishments.md  # Certifications/awards
│       ├── posts.md            # Blog posts section
│       ├── talks.md            # Talks section
│       ├── news.md             # News section
│       └── cv.md               # CV download link
├── assets/                       # Source assets (SCSS, images)
│   ├── scss/custom.scss         # Custom SCSS styling
│   ├── css/                     # CSS libraries
│   └── media/                   # Logo, icons, images
├── layouts/                      # Custom HTML templates (overrides theme)
│   ├── partials/                # Partial templates
│   └── shortcodes/              # Hugo shortcodes
├── static/                       # Static files served as-is
│   ├── css/custom.css           # Custom CSS
│   ├── files/cv.pdf             # Downloadable CV
│   └── img/                     # Images
├── data/                         # Data files
│   ├── page_sharer.toml         # Social sharing config
│   └── fonts/                   # Font configurations
└── hugo.toml                     # Additional Hugo config (analytics, URLs)

src/                              # Source files (not part of Hugo site)
└── personal_photo.png           # Original profile photo (copy to content/authors/admin/avatar.jpg)
```

## Hugo Architecture

This site uses:
- **Hugo**: Static site generator (v0.100+)
- **Theme**: Wowchemy Academic (starter-hugo-academic) loaded as Hugo modules
- **Content Format**: Markdown with YAML frontmatter
- **Styling**: SCSS + Custom CSS (dark mode enabled by default)
- **Deployment**: GitHub Pages from main branch

### Key Hugo Concepts

1. **Content Organization**: Each content type (publication, project, blog) lives in its own directory under `content/`
2. **Front Matter**: YAML metadata at the top of markdown files controls page behavior
3. **Widgets**: Homepage sections are defined in `content/home/*.md` with `active: true/false` and `weight:` for ordering
4. **Author System**: The `admin` author in `content/authors/admin/_index.md` is marked as `superuser: true` and represents the site owner
5. **Hugo Modules**: Theme loaded via Go modules (defined in `config.yaml` under `module.imports`)

## Common Development Commands

### Local Development
```bash
# Navigate to Hugo site root
cd template

# Run development server with drafts
hugo server -D

# Run development server (published content only)
hugo server

# Site will be available at http://localhost:1313
# Hugo watches for file changes and live-reloads
```

### Building
```bash
# Build static site (output to public/)
cd template
hugo

# Build with future-dated content
hugo --buildFuture

# Build with drafts
hugo --buildDrafts
```

### Content Management
```bash
# Create new publication
hugo new publication/my-paper-2024/index.md

# Create new blog post
hugo new blog/my-post.md

# Create new project
hugo new project/my-project/index.md
```

## Critical Configuration Files

### 1. config/_default/config.yaml
- **What**: Main Hugo configuration
- **Key Fields**: `title`, `baseURL`, `theme`, `module.imports`
- **Update When**: Changing site title, domain, or adding Hugo modules

### 2. config/_default/params.yaml
- **What**: Site-wide parameters (Wowchemy theme settings)
- **Key Sections**:
  - Contact info (`email`, `address`, `coordinates`)
  - Site features (search, day/night mode, syntax highlighting)
  - Social sharing, comments, marketing (analytics)
  - Theme appearance (fonts, colors)
  - Regional settings (date format, address format)
- **Update When**: Changing contact info, enabling/disabling features, customizing appearance

### 3. config/_default/menus.yaml
- **What**: Navigation menu structure
- **Format**: List of menu items with `name`, `url`, `weight` (for ordering)
- **Update When**: Adding/removing navigation items

### 4. content/authors/admin/_index.md
- **What**: Primary author profile (site owner)
- **Key Sections**:
  - Front matter: `title`, `role`, `bio`, `interests`, `social`, `organizations`, `education`
  - Body: Full biography text (Markdown)
- **Update When**: Changing personal info, adding social links, updating bio

## Content Creation Guidelines

### Publications
Each publication is a folder under `content/publication/` with:

```markdown
---
title: "Paper Title"
authors:
  - admin                    # Refers to Zoheb Khan
  - "Other Author"
date: "2024-01-01T00:00:00Z"
doi: "10.1234/example"

# Publication type (1=conference paper, 2=journal article, 3=preprint, etc.)
publication_types: ["2"]

publication: "In *Journal of Example*"
publication_short: "In *J. Example*"

abstract: "Your abstract here..."

# Links
url_pdf: ''
url_code: ''
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image (place image named `featured.jpg/png` in page folder)
featured: false

# Associated projects (optional, references project slugs)
projects: []

# Slides (optional, Markdown slides)
slides: ""
---

Optional full text content here...
```

### Homepage Widgets
Files in `content/home/` control homepage sections:
- Each file has `active: true/false` to show/hide
- `weight: N` controls display order (lower = higher on page)
- `headless: true` means these pages don't have their own URL

To disable a section: Set `active: false` in the front matter

## Profile Photo Management

**Source**: `src/personal_photo.png` (Zoheb's photo)
**Destination**: `template/content/authors/admin/avatar.jpg`

```bash
# Copy profile photo to correct location
cp src/personal_photo.png template/content/authors/admin/avatar.jpg
```

**Important**: Must be named `avatar.jpg` for theme to recognize it.

## Customization Points

### Custom Styling
- **SCSS**: `template/assets/scss/custom.scss` (compiled by Hugo)
- **CSS**: `template/static/css/custom.css` (loaded directly)
- **Chroma Themes**: `template/assets/css/libs/chroma/*.css` (syntax highlighting themes)

### Custom Layouts
Override theme templates by placing files in `template/layouts/`:
- `partials/`: Partial templates (header, footer, etc.)
- `shortcodes/`: Custom Hugo shortcodes
- `_default/`: Default page templates

### Icons & Branding
- Site logo: `template/assets/media/logo.png`
- Site icon: `template/assets/media/icon.png` and `icon-192.png`
- Custom org icons: `template/assets/media/icons/brands/`

## Deployment

### GitHub Pages Setup
1. Create GitHub repository named `[username].github.io` (e.g., `ZohebKhan1.github.io`)
2. Push Hugo site to `main` branch
3. In repository settings → Pages:
   - Source: Deploy from a branch
   - Branch: `main`
   - Folder: `/` (root)
4. GitHub Actions will build and deploy automatically
5. Site will be live at `https://[username].github.io`

**Note**: Ensure `baseURL` in `config/_default/config.yaml` matches your GitHub Pages URL.

## Wowchemy Theme System

The site uses Wowchemy (formerly Academic) theme loaded as Hugo modules. Key features:
- **Responsive Design**: Mobile-first, responsive layouts
- **Dark Mode**: Automatic dark/light theme switching (enabled by default)
- **SEO Optimized**: Meta tags, structured data, sitemaps
- **Academic Features**: Publications, projects, talks, CV download
- **Netlify CMS Support**: Optional CMS for content management (included in modules)

### Theme Configuration
Most theme behavior is controlled via `config/_default/params.yaml`:
- Appearance (fonts, colors, theme mode)
- Features (search, code highlighting, math rendering)
- Marketing (analytics, commenting systems)
- Regional settings (date formats, address formats)

## Important Notes

1. **Hugo Version**: Requires Hugo Extended v0.100+ (for SCSS processing)
2. **Theme Updates**: Theme is loaded via Hugo modules, not stored in repository
3. **Content vs. Static**: Content files (Markdown) go in `content/`, static assets (images, PDFs) go in `static/`
4. **Author References**: Use `admin` in author lists to reference the primary author (Zoheb Khan)
5. **URL Structure**: Publications use `/publication/`, projects use `/project/`, etc. (defined in `config.yaml` permalinks)
6. **Analytics**: Google Analytics configured in `hugo.toml` (`googleAnalytics = 'UA-36911186-4'` - update this for Zoheb's account)

## Troubleshooting

### Build Issues
- **Module errors**: Run `hugo mod get -u` to update Hugo modules
- **SCSS errors**: Ensure Hugo Extended version is installed
- **Missing pages**: Check `active: true` in front matter

### Content Not Showing
- Verify `draft: false` (or omit `draft` field)
- Check `date` is not in the future (unless using `--buildFuture`)
- Ensure front matter is valid YAML

### Styling Issues
- Custom CSS must be in `static/css/` or `assets/scss/`
- SCSS changes require Hugo server restart
- Check browser cache (hard refresh with Ctrl+Shift+R)

## Migration Checklist

When customizing this template for Zoheb Khan:
- [ ] Update `config/_default/config.yaml`: `title`, `baseURL`
- [ ] Update `config/_default/params.yaml`: All contact info, organization details
- [ ] Replace `content/authors/admin/_index.md` with Zoheb's information
- [ ] Copy `src/personal_photo.png` to `content/authors/admin/avatar.jpg`
- [ ] Delete all example publications in `content/publication/`
- [ ] Update or remove example projects in `content/project/`
- [ ] Update or disable news items in `content/news/`
- [ ] Update `config/_default/menus.yaml` with desired navigation
- [ ] Update `hugo.toml`: Google Analytics ID
- [ ] Update social links in admin profile (Google Scholar, ResearchGate, GitHub)
- [ ] Add real publications, projects, and CV
- [ ] Test locally with `hugo server -D`
- [ ] Deploy to GitHub Pages
