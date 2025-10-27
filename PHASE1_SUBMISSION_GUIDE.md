# Phase 1 SEO Implementation Guide for Zoheb Khan

## ✅ Completed Technical Setup
- Complete meta tags (Open Graph, Twitter Cards, canonical URL)
- Comprehensive JSON-LD Person Schema with all academic affiliations
- XML sitemap with all page sections
- Optimized robots.txt welcoming search engines
- Performance optimizations (preconnect, dns-prefetch)

## 📋 Step 1: Google Search Console Setup

### A. Access Google Search Console
1. Go to: https://search.google.com/search-console
2. Sign in with your Google account
3. Click "Add Property"

### B. Add Your Site
1. Choose "URL prefix" option
2. Enter: `https://zohebkhan1.github.io`
3. Click "Continue"

### C. Verify Ownership
1. Choose "HTML tag" verification method
2. Copy the verification meta tag (looks like: `<meta name="google-site-verification" content="ABC123...">`)
3. Add ONLY the content value to your index.html where it says:
   ```html
   <!-- <meta name="google-site-verification" content="YOUR_VERIFICATION_CODE_HERE" /> -->
   ```
   Replace with:
   ```html
   <meta name="google-site-verification" content="ABC123..." />
   ```
4. Commit and push the change to GitHub
5. Wait 2-3 minutes for GitHub Pages to update
6. Click "Verify" in Search Console

### D. Submit Sitemap
1. In Search Console, go to "Sitemaps" in left sidebar
2. Enter: `sitemap.xml`
3. Click "Submit"
4. Google will now start crawling your site

### E. Request Indexing
1. Go to "URL Inspection" tool
2. Enter: `https://zohebkhan1.github.io`
3. Click "Request Indexing"
4. Wait for Google to process (can take 1-2 weeks)

### F. Monitor Progress
- Check "Coverage" report for any issues
- Review "Performance" to see search queries
- Monitor "Links" to see who's linking to you

## 📧 Step 2: Critical Backlink Requests

### A. University of Chicago / Moskowitz Lab Website

**Find the right contact:**
- Lab webmaster or PI's admin assistant
- Department IT administrator
- Your direct supervisor

**Email Template:**

```
Subject: Request to Update My Profile Link - Zoheb Khan

Dear [Name],

I hope this email finds you well. I'm writing to request a small update to my profile on the [Moskowitz Lab/Department] website.

I've recently launched my professional portfolio website at https://zohebkhan1.github.io to showcase my research and bioinformatics work at the lab. Would it be possible to add this link to my profile on the lab's people page?

The link could be added as:
- "Personal Website" or
- "Zoheb Khan - Portfolio"

This would help colleagues and potential collaborators find my work and publications more easily.

Thank you for your time and assistance.

Best regards,
Zoheb Khan
Bioinformatician, Moskowitz Lab
```

### B. Google Scholar Profile Update

1. Go to: https://scholar.google.com/citations?user=2gFbtqIAAAAJ&hl=en
2. Click "Edit" button (pencil icon)
3. Add your website URL in the "Homepage" field: `https://zohebkhan1.github.io`
4. Click "Save"

### C. ORCID Profile Update

1. Log into your ORCID account at https://orcid.org
2. Click "Edit" on your profile
3. Add website under "Websites & Social Links"
4. Enter: `https://zohebkhan1.github.io`
5. Label it as "Personal Website"
6. Save changes

**If you don't have an ORCID:**
1. Create one at https://orcid.org/register
2. It's essential for academic visibility
3. Add all your publications
4. Link to your website

### D. ResearchGate Profile Update

1. Log into ResearchGate
2. Go to your profile
3. Click "Edit profile"
4. Add website URL in the "Websites" section
5. Save changes

### E. LinkedIn Profile Update

1. Log into LinkedIn
2. Edit your profile
3. Under "Contact Info" add website
4. Choose "Personal Website" as type
5. Enter: `https://zohebkhan1.github.io`
6. Save

### F. GitHub Profile Update

1. Go to https://github.com/ZohebKhan1
2. Click "Edit profile"
3. Add website URL in the "Website" field
4. Also add to your profile README if you have one
5. Save changes

## 🔍 Step 3: Quick SEO Checks

### Verify Everything is Working:

1. **Test Rich Results:**
   - Go to: https://search.google.com/test/rich-results
   - Enter your URL
   - Check for any errors

2. **Test Mobile Friendliness:**
   - Go to: https://search.google.com/test/mobile-friendly
   - Enter your URL
   - Should pass all tests

3. **Check Page Speed:**
   - Go to: https://pagespeed.web.dev/
   - Enter your URL
   - Aim for 90+ score

4. **Validate Structured Data:**
   - Go to: https://validator.schema.org/
   - Paste your HTML
   - Check for errors

## 📊 Step 4: Monitor and Track

### Week 1 Tasks:
- [ ] Google Search Console verified
- [ ] Sitemap submitted
- [ ] Indexing requested
- [ ] All profile backlinks updated
- [ ] Lab website link requested

### Week 2 Check:
- [ ] Check Search Console for crawl errors
- [ ] Verify all backlinks are live
- [ ] Google your name - check ranking
- [ ] Review any Search Console messages

### Ongoing:
- Update content monthly
- Check Search Console weekly initially
- Monitor which keywords bring traffic
- Add new publications/projects as completed

## 🎯 Success Metrics

You'll know Phase 1 is successful when:
1. ✅ Site appears in Search Console as verified
2. ✅ Sitemap shows as "Success" status
3. ✅ No crawl errors reported
4. ✅ All academic profiles link to your site
5. ✅ Searching "Zoheb Khan University of Chicago" shows your site in results

## ⚠️ Important Notes

1. **DO NOT** spam request indexing - once is enough
2. **DO NOT** buy backlinks or use link farms
3. **DO** be patient - SEO takes 2-4 weeks minimum
4. **DO** keep content fresh with regular updates
5. **DO** ensure ORCID and LinkedIn URLs are added to the JSON-LD schema once you have them

## 📝 Notes Section
Use this space to track your progress:

- Google Verification Code: _________________
- Date Submitted to Search Console: _________________
- Date Lab Website Updated: _________________
- First Google Search Appearance: _________________
- Notes: _________________

---

**Next Steps:** Once all Phase 1 items are complete and you see your site appearing in Google searches, we can move to Phase 2 for content optimization and advanced features.