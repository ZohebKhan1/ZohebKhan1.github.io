# Hugo SEO Implementation Guide
## Why Your Previous SEO Files Broke the Website

### The Problem
You had three excellent SEO files in your root directory:
- `index.html` - Full SEO meta tags, JSON-LD structured data
- `robots.txt` - Custom crawler directives
- `sitemap.xml` - Manual sitemap

**Why they broke Hugo:**
When you push a Hugo site to GitHub Pages, the build process works like this:
1. Hugo builds your site from `template/` → generates output in `public/`
2. GitHub Pages serves files from the root directory OR from `public/`
3. **If files exist in root (index.html, robots.txt, sitemap.xml), they're served INSTEAD of Hugo's generated files**
4. This means your Hugo site never loads - only the static index.html appears

### The Solution: The Hugo Way

Hugo has its own system for generating these files:
- **robots.txt** → Put in `template/static/` (Hugo copies it to root during build)
- **Sitemap** → Hugo auto-generates (already configured via `enableRobotsTXT: true`)
- **Meta tags & JSON-LD** → Add to Hugo layouts/partials

---

## Current Hugo SEO Status (What You Already Have)

### ✅ Already Working
1. **Sitemap Generation**: Hugo automatically generates `sitemap.xml`
   - Configured in `config.yaml` with `sitemap:` directive
   - Includes all pages, publications, blog posts
   - Located at: `https://zohebkhan1.github.io/sitemap.xml`

2. **Basic robots.txt**: Hugo generates basic robots.txt
   - Enabled via `enableRobotsTXT: true` in config
   - Allows all bots, includes sitemap reference

3. **Basic Meta Tags**: Wowchemy theme includes:
   - Title tags
   - Basic Open Graph tags
   - Twitter Card tags
   - Canonical URLs

4. **Structured Data**: Wowchemy includes Person schema
   - Based on `content/authors/admin/_index.md`
   - Automatically generated for author pages

### ❌ Missing (From Your Excellent Standalone Files)
1. **Enhanced robots.txt**: Custom bot rules (block SEMrush, Ahrefs)
2. **Comprehensive JSON-LD**: Extended Person schema with:
   - Alternate names (Zoheb Amanullah Khan, Zohebk)
   - Detailed occupation and skills
   - KnowsAbout array with research areas
   - Complete education history
   - ORCID and LinkedIn links (when available)
3. **Enhanced Meta Tags**:
   - Extended keyword list
   - Google Search Console verification
   - Revisit-after, distribution, rating tags
4. **Performance Optimizations**:
   - DNS prefetch for external domains
   - Preconnect for fonts

---

## Implementation Strategy

### Phase 1: Configuration-Based Improvements (Safest)
Update Hugo config files to enable built-in SEO features

### Phase 2: Custom Layouts (Most Control)
Create custom Hugo partials for enhanced SEO

### Phase 3: Cleanup
Remove root-level SEO files that break Hugo

---

## Step-by-Step Implementation

### Step 1: Enhanced robots.txt
**Location**: `template/static/robots.txt`
**Why here**: Hugo copies everything in `static/` to root during build

```txt
# Robots.txt for Zoheb Khan Portfolio
# https://zohebkhan1.github.io/

# Allow all bots to crawl the site
User-agent: *
Allow: /
Crawl-delay: 0

# Specifically welcome Google
User-agent: Googlebot
Allow: /
Crawl-delay: 0

# Specifically welcome Bing
User-agent: Bingbot
Allow: /
Crawl-delay: 0

# Specifically welcome Google Scholar Bot
User-agent: Googlebot-Scholar
Allow: /

# Block bad bots (optional - these bots crawl for SEO tools, not search engines)
User-agent: AhrefsBot
Disallow: /

User-agent: SemrushBot
Disallow: /

User-agent: DotBot
Disallow: /

# Sitemap location
Sitemap: https://zohebkhan1.github.io/sitemap.xml
```

### Step 2: Enhanced SEO Configuration
**Location**: `template/config/_default/params.yaml`

Update the `marketing` section:

```yaml
marketing:
  seo:
    site_type: Person
    local_business_type: ''
    org_name: 'Moskowitz Lab, University of Chicago'
    description: 'Zoheb Khan - Bioinformatician at the University of Chicago Moskowitz Lab specializing in genomics, RNA-seq analysis, Trisomy 21 research, and Hedgehog signaling pathways.'
    twitter: 'zohebk'
  analytics:
    google_analytics: 'UA-36911186-4'  # Already in hugo.toml
    baidu_tongji: ''
  verification:
    google: 'YOUR_VERIFICATION_CODE_HERE'  # Add when you get it from Search Console
    baidu: ''
```

### Step 3: Custom SEO Head Partial
**Location**: `template/layouts/partials/custom_head.html` (new file)

This file will be included in the `<head>` section and adds:
- Enhanced meta tags
- Comprehensive JSON-LD structured data
- Performance optimizations

```html
<!-- Enhanced SEO Meta Tags -->
<meta name="keywords" content="Zoheb Khan, Zoheb Amanullah Khan, Zohebk, University of Chicago, UChicago, UofC, Moskowitz Lab, Ivan Moskowitz, Bioinformatics, Genomics, Computational Biology, RNA-seq, GWAS, Tbx5, Down Syndrome, Trisomy 21, Hedgehog Signaling, Atrial Fibrillation, St. Mark's School of Texas">
<meta name="revisit-after" content="7 days">
<meta name="distribution" content="global">
<meta name="rating" content="general">

<!-- Performance Optimizations -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="dns-prefetch" href="https://scholar.google.com">
<link rel="dns-prefetch" href="https://github.com">
<link rel="dns-prefetch" href="https://www.researchgate.net">

<!-- Enhanced JSON-LD Structured Data -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Zoheb Khan",
  "alternateName": ["Zoheb Amanullah Khan", "Zohebk"],
  "url": "{{ .Site.BaseURL }}",
  "image": "{{ .Site.BaseURL }}/authors/admin/avatar.jpg",
  "email": "mailto:zohebk@uchicago.edu",
  "description": "Bioinformatician at the University of Chicago Moskowitz Lab specializing in genomics, RNA-seq analysis, Trisomy 21 research, and Hedgehog signaling pathways.",
  "jobTitle": "Bioinformatician",
  "worksFor": {
    "@type": "Organization",
    "name": "Moskowitz Lab, University of Chicago",
    "url": "https://moskowitzlab.uchicago.edu/",
    "address": {
      "@type": "PostalAddress",
      "addressLocality": "Chicago",
      "addressRegion": "Illinois",
      "addressCountry": "United States"
    }
  },
  "alumniOf": [
    {
      "@type": "CollegeOrUniversity",
      "name": "University of Chicago",
      "url": "https://www.uchicago.edu/",
      "sameAs": "https://en.wikipedia.org/wiki/University_of_Chicago"
    },
    {
      "@type": "EducationalOrganization",
      "name": "St. Mark's School of Texas",
      "url": "https://www.smtexas.org/",
      "address": {
        "@type": "PostalAddress",
        "addressLocality": "Dallas",
        "addressRegion": "Texas",
        "addressCountry": "United States"
      }
    }
  ],
  "hasOccupation": {
    "@type": "Occupation",
    "name": "Bioinformatician",
    "description": "Computational analysis of biological data, specializing in genomics and RNA sequencing",
    "skills": [
      "RNA-seq", "ChIP-seq", "ATAC-seq", "Hi-C", "Micro-C",
      "scRNA-seq", "snRNA-seq", "H3K27ac ChIP",
      "Spatial Transcriptomics", "DESeq2", "maSigPro",
      "GSEA", "Python", "R", "Bioconductor"
    ]
  },
  "knowsAbout": [
    "Bioinformatics", "Genomics", "Computational Biology",
    "RNA-seq Analysis", "Trisomy 21/Down Syndrome",
    "Hedgehog Signaling Pathway", "Atrial Fibrillation",
    "Heart Development", "Gene Regulatory Networks",
    "Developmental Biology", "iPSC Cortical Neuron Differentiation",
    "Neural Crest Cell Development", "Chromatin Accessibility",
    "GWAS Analysis"
  ],
  "sameAs": [
    "https://github.com/ZohebKhan1",
    "https://scholar.google.com/citations?user=2gFbtqIAAAAJ&hl=en",
    "https://www.researchgate.net/profile/Zoheb-Khan-7"
  ],
  "affiliation": {
    "@type": "Organization",
    "name": "University of Chicago",
    "url": "https://www.uchicago.edu/"
  },
  "award": [
    "B.A. in Genetics, University of Chicago (2022)"
  ]
}
</script>
```

### Step 4: Hook Custom Head into Hugo Theme
**Location**: `template/layouts/partials/site_head.html` (new file)

This file overrides Wowchemy's head partial to include your custom SEO:

```html
<!-- Original Wowchemy head content -->
{{ partial "head_metadata" . }}
{{ partial "head_highlighter" . }}
{{ partial "head_resources" . }}

<!-- Your custom SEO enhancements -->
{{ partial "custom_head" . }}
```

### Step 5: Update Admin Profile
**Location**: `template/content/authors/admin/_index.md`

Ensure comprehensive metadata (this already exists, just verify):

```yaml
title: Zoheb Khan
role: Bioinformatician
bio: My research interests include genomics, RNA-seq analysis, and developmental biology.

interests:
  - Bioinformatics
  - Genomics
  - RNA-seq Analysis
  - Trisomy 21/Down Syndrome Research
  - Hedgehog Signaling Pathways
  - Developmental Biology

social:
  - icon: envelope
    icon_pack: fas
    link: 'mailto:zohebk@uchicago.edu'
  - icon: github
    icon_pack: fab
    link: https://github.com/ZohebKhan1
  - icon: google-scholar
    icon_pack: ai
    link: https://scholar.google.com/citations?user=2gFbtqIAAAAJ&hl=en
  - icon: researchgate
    icon_pack: ai
    link: https://www.researchgate.net/profile/Zoheb-Khan-7

organizations:
  - name: University of Chicago
    url: 'https://www.uchicago.edu/'

education:
  courses:
    - course: B.A. in Genetics
      institution: University of Chicago
      year: 2022
```

### Step 6: Verify Hugo Build Process

After making changes:

```bash
cd template
hugo server -D
```

Visit `http://localhost:1313` and:
1. View page source → Check for custom meta tags
2. Visit `http://localhost:1313/robots.txt` → Verify custom robots.txt
3. Visit `http://localhost:1313/sitemap.xml` → Verify sitemap exists
4. Test with: https://search.google.com/test/rich-results

### Step 7: Clean Up Root Directory

**IMPORTANT**: After verifying Hugo builds correctly, DELETE these files from root:
- `index.html` (root level)
- `robots.txt` (root level)
- `sitemap.xml` (root level)

These files break Hugo. Your SEO content is now integrated into Hugo templates.

```bash
# From repository root
rm index.html robots.txt sitemap.xml
git add -A
git commit -m "Remove standalone SEO files, integrate into Hugo templates"
git push
```

---

## Phase 1 Checklist Items (Hugo Edition)

### Technical Setup
- [ ] Custom robots.txt in `template/static/robots.txt`
- [ ] Enhanced params.yaml with SEO description and org name
- [ ] Custom head partial with JSON-LD structured data
- [ ] Site_head.html override to include custom SEO
- [ ] Verify Hugo builds without errors
- [ ] Delete root-level index.html, robots.txt, sitemap.xml

### Google Search Console
- [ ] Push Hugo site to GitHub
- [ ] Wait for deployment (5-10 minutes)
- [ ] Register at https://search.google.com/search-console
- [ ] Add property: https://zohebkhan1.github.io
- [ ] Get verification code
- [ ] Add to `params.yaml` under `marketing.verification.google`
- [ ] Submit sitemap: `https://zohebkhan1.github.io/sitemap.xml`
- [ ] Request indexing for homepage

### Profile Backlinks
- [ ] Google Scholar: Add website URL
- [ ] GitHub profile: Add website URL
- [ ] ResearchGate: Add website URL
- [ ] Create ORCID account: https://orcid.org/register
- [ ] LinkedIn: Add website URL
- [ ] Add ORCID and LinkedIn to JSON-LD sameAs array

### Academic Backlinks
- [ ] Email Moskowitz Lab webmaster for profile link
- [ ] Email department for faculty/staff directory link
- [ ] Add to UChicago directory if available

---

## Testing Your SEO Implementation

### 1. Local Hugo Build Test
```bash
cd template
hugo server
# Open http://localhost:1313
# View page source → Look for your custom meta tags and JSON-LD
```

### 2. Production Build Test
```bash
cd template
hugo
# Check public/robots.txt exists
# Check public/sitemap.xml exists
# Check public/index.html has your meta tags
```

### 3. Online Validation Tools

**After deploying to GitHub Pages:**

- **Rich Results Test**: https://search.google.com/test/rich-results
  - Enter: `https://zohebkhan1.github.io`
  - Should recognize Person schema

- **Mobile Friendly Test**: https://search.google.com/test/mobile-friendly
  - Should pass all tests (Wowchemy is responsive)

- **Schema Validator**: https://validator.schema.org/
  - Paste your page source
  - Should validate Person schema with no errors

- **PageSpeed Insights**: https://pagespeed.web.dev/
  - Enter: `https://zohebkhan1.github.io`
  - Aim for 90+ score

---

## Common Hugo SEO Mistakes to Avoid

### ❌ DON'T:
1. Put index.html in repository root (breaks Hugo)
2. Put sitemap.xml in repository root (Hugo generates it)
3. Edit files in `public/` (Hugo deletes this folder on rebuild)
4. Put robots.txt in repository root (put in `template/static/` instead)
5. Try to override Hugo's sitemap entirely (customize via config instead)

### ✅ DO:
1. Put custom files in `template/static/` (copied to root during build)
2. Use `template/layouts/` to customize HTML output
3. Configure SEO in `params.yaml` and `config.yaml`
4. Let Hugo generate sitemap and RSS feeds
5. Test locally with `hugo server` before pushing

---

## Understanding Hugo's Build Process

```
1. Source Files (What You Edit)
   ├── template/content/        → Content (Markdown)
   ├── template/layouts/        → HTML templates
   ├── template/static/         → Static files (CSS, images, robots.txt)
   └── template/config/         → Configuration

2. Hugo Build Command: `hugo`
   ├── Reads content/ and converts Markdown → HTML
   ├── Applies layouts/ templates
   ├── Copies static/ files to root
   ├── Generates sitemap.xml, RSS feeds
   └── Outputs everything to public/

3. Output (What Gets Deployed)
   └── public/
       ├── index.html           → Generated from content + layouts
       ├── robots.txt           → Copied from static/ or generated
       ├── sitemap.xml          → Auto-generated by Hugo
       ├── authors/             → Author pages
       ├── publication/         → Publication pages
       └── ...

4. GitHub Pages Deployment
   ├── Reads from repository root OR public/
   ├── Serves index.html as homepage
   └── Makes sitemap.xml and robots.txt available
```

**Key Insight**: Never edit `public/` directly. Always edit source files in `template/` and rebuild.

---

## Why This Approach Won't Break Your Site

### Previous Problem:
```
Repository Root:
├── index.html          ← Static HTML, breaks Hugo
├── robots.txt          ← Static file, breaks Hugo
├── sitemap.xml         ← Static XML, breaks Hugo
└── template/           ← Hugo site (never built)
```

**Result**: GitHub Pages served index.html, ignoring Hugo entirely.

### New Approach:
```
Repository Root:
└── template/                     ← Hugo site root
    ├── static/
    │   └── robots.txt           ← Custom robots.txt (copied to root)
    ├── layouts/
    │   └── partials/
    │       ├── custom_head.html  ← Custom SEO meta tags
    │       └── site_head.html    ← Hooks custom_head into theme
    ├── config/_default/
    │   └── params.yaml          ← SEO configuration
    └── content/                  ← Content (generates HTML)
```

**Result**: Hugo builds everything correctly, SEO enhancements included.

---

## Deployment Workflow

### Initial Setup
```bash
# 1. Implement Hugo SEO changes (use this guide)
cd template
hugo server -D  # Test locally

# 2. Build production site
hugo

# 3. Verify output
ls public/robots.txt
ls public/sitemap.xml
grep "application/ld+json" public/index.html

# 4. Clean up root directory
cd ..
rm index.html robots.txt sitemap.xml  # Remove files that break Hugo

# 5. Commit and push
git add .
git commit -m "Implement Hugo-native SEO enhancements"
git push
```

### Ongoing Updates
```bash
# Edit content or layouts
cd template
hugo server -D  # Preview changes

# Build and deploy
hugo
cd ..
git add .
git commit -m "Update content"
git push
```

---

## Expected Results

### Week 1
- Site appears in Google Search Console
- robots.txt and sitemap.xml are accessible
- Rich Results Test recognizes Person schema

### Week 2-3
- Site appears for "Zoheb Khan" searches
- Search Console shows impressions
- Profile backlinks are indexed

### Month 1
- Ranking #1 for "Zoheb Khan University of Chicago"
- Appearing for research-related queries
- Growing search traffic

---

## Next Steps After Implementation

1. **Monitor Search Console Weekly**
   - Check for crawl errors
   - Review search queries bringing traffic
   - Monitor click-through rates

2. **Update Content Regularly**
   - Add new publications as they're published
   - Write blog posts about research
   - Update profile with new accomplishments

3. **Build Quality Backlinks**
   - Get listed on lab website
   - Get listed on department directory
   - Collaborate and get cited

4. **Enhance Content**
   - Add more detailed research descriptions
   - Create project pages for major works
   - Add downloadable CV

---

## Troubleshooting

### Hugo Build Fails
```bash
# Check Hugo version
hugo version  # Need Extended v0.100+

# Update Hugo modules
cd template
hugo mod get -u
hugo mod tidy
```

### Custom Head Not Showing
```bash
# Verify file exists
ls template/layouts/partials/custom_head.html

# Check if site_head.html includes it
cat template/layouts/partials/site_head.html
```

### robots.txt Not Working
```bash
# Verify location
ls template/static/robots.txt  # Should exist

# Check build output
ls template/public/robots.txt  # Should exist after `hugo`

# Test URL (after deployment)
curl https://zohebkhan1.github.io/robots.txt
```

### JSON-LD Not Validating
- Use https://validator.schema.org/
- Common issues:
  - Missing required fields (name, url)
  - Invalid URL format
  - Duplicate @type declarations

---

## Contact and Support

If you encounter issues:
1. Check Hugo documentation: https://gohugo.io/documentation/
2. Check Wowchemy docs: https://wowchemy.com/docs/
3. Validate structured data: https://validator.schema.org/
4. Test with Google tools: https://search.google.com/test/rich-results

Remember: Hugo generates static HTML. View the source of your deployed site to see what Hugo actually produces.
