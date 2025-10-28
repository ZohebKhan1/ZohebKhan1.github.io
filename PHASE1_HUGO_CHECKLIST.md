# Phase 1 SEO Implementation Checklist - Hugo Edition

## What Was Done (Claude Code Implementation)

### ✅ Completed Hugo SEO Files

1. **custom_head.html** - `template/layouts/partials/custom_head.html`
   - Enhanced meta tags with academic keywords
   - Comprehensive JSON-LD Person schema with:
     - Alternate names (Zoheb Amanullah Khan, Zohebk)
     - Detailed occupation and skills
     - KnowsAbout array (19 research topics)
     - Complete education history
     - Work organization (Moskowitz Lab)
     - Social profile links
   - Performance optimizations (preconnect, DNS prefetch)
   - Automatically included by Wowchemy theme

2. **robots.txt** - `template/static/robots.txt`
   - Welcomes Google, Bing, Google Scholar bots
   - Blocks SEO tool crawlers (Ahrefs, Semrush, DotBot)
   - Includes sitemap reference
   - Copied to root during Hugo build

3. **params.yaml** - `template/config/_default/params.yaml`
   - Enhanced SEO description with research focus
   - Organization name: "Moskowitz Lab, University of Chicago"
   - Google Analytics ID: UA-36911186-4
   - Google Search Console verification field ready

### ⚠️ Files to DELETE (They Break Hugo)

These files in your **repository root** will prevent Hugo from working:
- `index.html` (root level)
- `robots.txt` (root level)
- `sitemap.xml` (root level)

Hugo generates these automatically. Root-level versions override Hugo's output.

---

## Your Action Items (Step-by-Step)

### Step 1: Test Hugo Build Locally ⏱️ 5 minutes

```bash
# Navigate to Hugo site
cd template

# Start development server
hugo server -D

# Open browser to: http://localhost:1313
```

**Verify:**
1. ✅ Site loads without errors
2. ✅ View page source → Look for `<script type="application/ld+json">` with your structured data
3. ✅ Check for keywords meta tag with "Zoheb Khan, Bioinformatics..."
4. ✅ Visit `http://localhost:1313/robots.txt` → Should show custom rules
5. ✅ Visit `http://localhost:1313/sitemap.xml` → Should show all pages

**If any errors occur:**
- Read error message carefully
- Check `template/layouts/partials/custom_head.html` syntax
- Ensure Hugo Extended version v0.100+ is installed
- Review `HUGO_SEO_IMPLEMENTATION_GUIDE.md` troubleshooting section

---

### Step 2: Clean Up Root Directory ⏱️ 2 minutes

**CRITICAL:** Remove standalone SEO files that break Hugo:

```bash
# From repository root (NOT template/)
cd /c/Users/zoheb/OneDrive/Desktop/github_projects/personal_website

# Check what files exist in root
ls -la *.html *.txt *.xml 2>/dev/null

# Delete the Hugo-breaking files
rm index.html robots.txt sitemap.xml

# Verify they're gone
ls -la *.html *.txt *.xml 2>/dev/null  # Should show nothing
```

**Why:** These files in the root directory are served INSTEAD of Hugo's generated files, completely breaking your Hugo site.

---

### Step 3: Commit and Push to GitHub ⏱️ 3 minutes

```bash
# From repository root
git status

# Add all Hugo SEO changes
git add template/static/robots.txt
git add template/layouts/partials/custom_head.html
git add template/config/_default/params.yaml
git add HUGO_SEO_IMPLEMENTATION_GUIDE.md
git add PHASE1_HUGO_CHECKLIST.md

# Remove standalone files if not already deleted
git rm index.html robots.txt sitemap.xml 2>/dev/null || true

# Commit
git commit -m "Implement Hugo-native SEO enhancements

- Add custom robots.txt with bot-specific rules
- Add custom_head.html with enhanced JSON-LD Person schema
- Update params.yaml with comprehensive SEO description
- Remove standalone SEO files that broke Hugo build"

# Push to GitHub
git push origin main
```

---

### Step 4: Wait for GitHub Pages Deployment ⏱️ 5-10 minutes

After pushing:
1. Go to: https://github.com/ZohebKhan1/ZohebKhan1.github.io/actions
2. Watch the latest workflow run
3. Wait for green checkmark (deployment complete)
4. Visit: https://zohebkhan1.github.io
5. Verify site loads correctly

**Troubleshooting:**
- If workflow fails: Click on it to see error message
- If site looks broken: Check that root-level index.html is deleted
- If changes don't appear: Hard refresh browser (Ctrl+Shift+R)

---

### Step 5: Verify SEO Implementation ⏱️ 10 minutes

**A. Check Live Site**

Visit https://zohebkhan1.github.io and:
1. Right-click → "View Page Source"
2. Search for (Ctrl+F):
   - `"@type": "Person"` → Should find your JSON-LD schema
   - `"alternateName": ["Zoheb Amanullah Khan", "Zohebk"]` → Structured data present
   - `"knowsAbout":` → Research areas listed
   - `<meta name="keywords"` → Keywords present

**B. Check robots.txt**

Visit: https://zohebkhan1.github.io/robots.txt

Should show:
```txt
# Robots.txt for Zoheb Khan Portfolio
User-agent: *
Allow: /
...
Sitemap: https://zohebkhan1.github.io/sitemap.xml
```

**C. Check Sitemap**

Visit: https://zohebkhan1.github.io/sitemap.xml

Should show:
```xml
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://zohebkhan1.github.io/</loc>
    ...
  </url>
</urlset>
```

---

### Step 6: Validate with Google Tools ⏱️ 10 minutes

**A. Rich Results Test**
1. Go to: https://search.google.com/test/rich-results
2. Enter: `https://zohebkhan1.github.io`
3. Click "Test URL"
4. Should recognize "Person" structured data
5. Check for zero errors

**B. Mobile-Friendly Test**
1. Go to: https://search.google.com/test/mobile-friendly
2. Enter: `https://zohebkhan1.github.io`
3. Should pass all tests (Wowchemy is responsive)

**C. PageSpeed Insights**
1. Go to: https://pagespeed.web.dev/
2. Enter: `https://zohebkhan1.github.io`
3. Check scores (aim for 90+ on Performance)

---

### Step 7: Google Search Console Setup ⏱️ 15 minutes

**CRITICAL FOR GOOGLE INDEXING**

#### A. Register Property
1. Go to: https://search.google.com/search-console
2. Sign in with your Google account
3. Click "Add Property"
4. Choose "URL prefix"
5. Enter: `https://zohebkhan1.github.io`
6. Click "Continue"

#### B. Verify Ownership
1. Choose "HTML tag" verification method
2. Copy ONLY the content value (not entire tag)
   - Example: If tag is `<meta name="google-site-verification" content="ABC123XYZ...">`
   - Copy only: `ABC123XYZ...`

3. Edit `template/config/_default/params.yaml`:
   ```yaml
   verification:
     google: 'ABC123XYZ...'  # Paste your code here
     baidu: ''
   ```

4. Rebuild and push:
   ```bash
   cd template
   hugo server -D  # Test locally first
   # Verify verification tag appears in page source

   cd ..
   git add template/config/_default/params.yaml
   git commit -m "Add Google Search Console verification"
   git push origin main
   ```

5. Wait 5-10 minutes for deployment
6. Return to Search Console → Click "Verify"

#### C. Submit Sitemap
1. In Search Console left sidebar: Click "Sitemaps"
2. Enter: `sitemap.xml`
3. Click "Submit"
4. Status should change to "Success" within minutes
5. Google will now start crawling your site

#### D. Request Indexing
1. In Search Console: Click "URL Inspection" (top)
2. Enter: `https://zohebkhan1.github.io`
3. Click "Request Indexing"
4. Wait for confirmation
5. **DO NOT** spam this - once is enough

---

### Step 8: Update Academic Profiles ⏱️ 20 minutes

**Critical Backlinks for SEO**

#### A. Google Scholar (HIGHEST PRIORITY)
1. Go to: https://scholar.google.com/citations?user=2gFbtqIAAAAJ&hl=en
2. Click "Edit" (pencil icon)
3. Add homepage: `https://zohebkhan1.github.io`
4. Save changes
5. **Impact:** Google Scholar profiles rank very high in searches

#### B. GitHub Profile
1. Go to: https://github.com/ZohebKhan1
2. Click "Edit profile"
3. Add website: `https://zohebkhan1.github.io`
4. Save

#### C. ResearchGate
1. Go to: https://www.researchgate.net/profile/Zoheb-Khan-7
2. Log in
3. Edit profile → Add website URL
4. Save

#### D. Create ORCID (If You Don't Have One)
1. Go to: https://orcid.org/register
2. Create account with institutional email (zohebk@uchicago.edu)
3. Add website to profile: `https://zohebkhan1.github.io`
4. Add all your publications
5. **Then update your JSON-LD:**
   - Edit `template/layouts/partials/custom_head.html`
   - In `"sameAs"` array, add: `"https://orcid.org/YOUR-ORCID-ID"`

#### E. LinkedIn
1. Log into LinkedIn
2. Edit profile → Contact Info
3. Add website (choose "Personal Website")
4. Enter: `https://zohebkhan1.github.io`
5. **Then update your JSON-LD:**
   - Edit `template/layouts/partials/custom_head.html`
   - In `"sameAs"` array, add: `"https://www.linkedin.com/in/YOUR-USERNAME"`

---

### Step 9: Request Lab/Department Backlinks ⏱️ 10 minutes

**Critical for Academic Credibility**

#### A. Moskowitz Lab Website
Find the right contact:
- Lab webmaster
- PI's admin assistant
- Your direct supervisor

**Email Template:**

```
Subject: Request to Add Website Link - Zoheb Khan

Dear [Name],

I hope this email finds you well. I'm writing to request a small update to my profile on the Moskowitz Lab website.

I've recently launched my professional portfolio at https://zohebkhan1.github.io to showcase my bioinformatics research and publications. Would it be possible to add this link to my profile on the lab's people page?

This would help colleagues and potential collaborators find my work more easily.

Thank you for your time and assistance.

Best regards,
Zoheb Khan
Bioinformatician, Moskowitz Lab
```

#### B. UChicago Department Directory
- Email department webmaster
- Request to add website to your directory listing
- Use similar email template

---

### Step 10: Monitor Progress ⏱️ Ongoing

#### Week 1 Checklist:
- [ ] Google Search Console verified
- [ ] Sitemap submitted and processing
- [ ] All academic profiles updated with website link
- [ ] Lab/department link requested
- [ ] No crawl errors in Search Console

#### Week 2 Check:
- [ ] Search "Zoheb Khan" in Google (incognito mode)
- [ ] Check Search Console for impressions
- [ ] Verify all profile backlinks are live
- [ ] Review Search Console "Pages" report

#### Week 3-4:
- [ ] Ranking for "Zoheb Khan University of Chicago"
- [ ] Appearing for research-related queries
- [ ] Growing impressions and clicks in Search Console

---

## Success Metrics

### Immediate (Week 1):
- ✅ Site verifies in Google Search Console
- ✅ Sitemap shows "Success" status
- ✅ No crawl errors
- ✅ Rich Results Test passes
- ✅ All profile backlinks added

### Short-term (Weeks 2-4):
- ✅ Site appears when searching "Zoheb Khan"
- ✅ Ranking on first page for "Zoheb Khan University of Chicago"
- ✅ Search Console shows 10+ impressions per day
- ✅ Profile backlinks are indexed by Google

### Medium-term (Months 1-2):
- ✅ Ranking #1 for your name
- ✅ Appearing for research queries ("Trisomy 21 bioinformatics", "Hedgehog signaling analysis")
- ✅ 50+ impressions per day
- ✅ Lab/department backlinks live and indexed

---

## Common Issues & Solutions

### Issue: Hugo Build Fails
**Solution:**
```bash
cd template
hugo mod clean
hugo mod get -u
hugo mod tidy
hugo server -D
```

### Issue: Custom Head Not Showing
**Check:**
1. File exists: `template/layouts/partials/custom_head.html`
2. Valid HTML (no unclosed tags)
3. Check browser console for errors
4. View page source to confirm inclusion

### Issue: robots.txt Not Working
**Check:**
1. File exists: `template/static/robots.txt`
2. Build produces: `template/public/robots.txt`
3. Root-level `robots.txt` is deleted
4. Visit: `https://zohebkhan1.github.io/robots.txt`

### Issue: "Index.html" Instead of Hugo Site
**Solution:**
```bash
# Delete root-level index.html
rm index.html
git rm index.html
git commit -m "Remove standalone index.html that breaks Hugo"
git push
```

### Issue: Google Not Indexing
**Patience:**
- Takes 1-2 weeks minimum
- Can take up to 4 weeks
- Don't spam "Request Indexing"
- Focus on quality backlinks

**Actions:**
- Ensure Search Console verification is complete
- Verify sitemap is submitted
- Check for crawl errors in Search Console
- Add more quality backlinks (ORCID, LinkedIn, lab website)

---

## What to Expect (Timeline)

### Days 1-3:
- Site deployed with SEO enhancements
- Search Console verified
- Tools recognize structured data
- No Google search results yet (normal)

### Week 1:
- Google starts crawling
- Search Console shows impressions
- May appear in searches (low ranking)

### Weeks 2-3:
- Consistent search appearances
- Ranking improves for your name
- Profile backlinks get indexed
- Search Console impressions grow

### Month 1:
- Ranking #1 or high on page 1 for "Zoheb Khan"
- Appearing for "Zoheb Khan University of Chicago"
- Lab/department links boost credibility
- 50+ daily impressions

### Months 2-3:
- Ranking for research keywords
- Growing organic traffic
- Cited in academic searches
- Strong authority for your name

---

## Important Reminders

### ✅ DO:
1. **Be patient** - SEO takes 2-4 weeks minimum
2. **Monitor Search Console** - Weekly checks for errors
3. **Update content** - Add publications, projects regularly
4. **Build quality backlinks** - Focus on academic sites
5. **Keep ORCID updated** - Link to your website there

### ❌ DON'T:
1. **Don't spam** "Request Indexing" - Once is enough
2. **Don't buy backlinks** - Google penalizes this
3. **Don't modify public/*** - Hugo regenerates it
4. **Don't create root-level HTML/XML** - Breaks Hugo
5. **Don't expect instant results** - 2-4 weeks is normal

---

## Next Steps After Phase 1

Once you're ranking #1 for your name and have steady traffic:

### Phase 2: Content Optimization
- Add detailed project pages
- Write blog posts about research
- Create publication summaries
- Add research highlights

### Phase 3: Advanced SEO
- Schema.org ScholarlyArticle markup for publications
- Breadcrumb navigation
- FAQ schema for research topics
- Video embeds with VideoObject schema

---

## Questions or Issues?

**Resources:**
- Implementation Guide: `HUGO_SEO_IMPLEMENTATION_GUIDE.md`
- Hugo Docs: https://gohugo.io/documentation/
- Wowchemy Docs: https://wowchemy.com/docs/
- Schema Validator: https://validator.schema.org/
- Google Search Central: https://developers.google.com/search

**Contact:**
- Lab IT support for department/lab website links
- UChicago webmaster for directory listings

---

## Checklist Summary

### Immediate (Do Today):
- [ ] Test Hugo build locally (`hugo server -D`)
- [ ] Delete root-level index.html, robots.txt, sitemap.xml
- [ ] Commit and push to GitHub
- [ ] Wait for deployment
- [ ] Verify live site works

### This Week:
- [ ] Google Search Console setup and verification
- [ ] Submit sitemap
- [ ] Update Google Scholar, GitHub, ResearchGate profiles
- [ ] Create ORCID if needed
- [ ] Request lab/department backlinks

### Ongoing:
- [ ] Monitor Search Console weekly
- [ ] Check search rankings
- [ ] Add new publications/projects
- [ ] Build quality academic backlinks

---

**You're now ready for Phase 1!** Follow these steps carefully, and your site will be indexed and ranking within 2-4 weeks. 🚀
