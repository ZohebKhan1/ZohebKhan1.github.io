# Quick Start Guide - Deploy SEO in 15 Minutes

## 🚨 CRITICAL FIRST STEP

**DELETE these files from repository root** (they break Hugo):
```bash
rm index.html robots.txt sitemap.xml
```

---

## ✅ 3-Step Deployment

### Step 1: Test (5 min)
```bash
cd template
hugo server -D
# Open: http://localhost:1313
# Check: View source for JSON-LD structured data
```

### Step 2: Deploy (5 min)
```bash
cd ..
rm index.html robots.txt sitemap.xml
git add template/
git rm index.html robots.txt sitemap.xml
git commit -m "Hugo SEO implementation"
git push
```

### Step 3: Verify (5 min)
- Wait 10 minutes
- Visit: https://zohebkhan1.github.io
- Check source for: `<script type="application/ld+json">`
- Test: https://search.google.com/test/rich-results

---

## 📋 What Was Implemented

| File | Location | Purpose |
|------|----------|---------|
| `robots.txt` | `template/static/` | Custom bot rules |
| `custom_head.html` | `template/layouts/partials/` | Meta tags + JSON-LD |
| `params.yaml` | `template/config/_default/` | SEO config |

---

## 🎯 Next Actions (Priority Order)

### Today:
1. ✅ Delete root-level HTML/XML files
2. ✅ Test and deploy
3. ✅ Verify live site works

### This Week:
1. ✅ Google Search Console setup
2. ✅ Update Google Scholar profile
3. ✅ Update GitHub profile
4. ✅ Request lab website link

### This Month:
1. ✅ Create ORCID
2. ✅ Monitor Search Console
3. ✅ Check rankings weekly

---

## 📖 Full Documentation

- **Step-by-step:** `PHASE1_HUGO_CHECKLIST.md`
- **Technical guide:** `HUGO_SEO_IMPLEMENTATION_GUIDE.md`
- **Overview:** `SEO_IMPLEMENTATION_SUMMARY.md`

---

## ⚠️ Troubleshooting

**Site broken?**
- Verify root-level index.html is deleted
- Check GitHub Actions for errors

**Custom head not showing?**
- Clear browser cache (Ctrl+Shift+R)
- Check: `template/layouts/partials/custom_head.html` exists

**robots.txt not working?**
- Verify: `template/static/robots.txt` exists
- Build locally: `hugo` then check `public/robots.txt`

---

## 🏆 Success Timeline

- **Week 1:** Google Search Console verified
- **Weeks 2-3:** Appears in searches
- **Month 1:** Ranking #1 for your name

---

**Start here:** Follow `PHASE1_HUGO_CHECKLIST.md` step-by-step! 🚀
