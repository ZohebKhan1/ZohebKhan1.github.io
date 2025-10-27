# One-Shot Prompt for Claude Code to Build Academic Website

Copy and paste this entire prompt into Claude Code:

---

I need you to create my personal academic website using the template from https://github.com/prasenjit52282/prasenjit52282.github.io. Here's my information:

**Personal Details:**
- Name: Zoheb Khan
- Position: Bioinformatician at Moskowitz Lab, The University of Chicago
- Email: zohebk@uchicago.edu
- Education: B.A. in Genetics, University of Chicago (June 2022)
- Lab Website: https://moskowitzlab.uchicago.edu/
- GitHub username: [zohebkhan1]
- Google Scholar: [https://scholar.google.com/citations?user=2gFbtqIAAAAJ&hl=en]
- ResearchGate: [https://www.researchgate.net/profile/Zoheb-Khan-7]
- GitHub Profile: [https://github.com/ZohebKhan1]

**Bio:**
Zoheb Khan is a Bioinformatician at the Moskowitz Lab at The University of Chicago, where he applies advanced computational methods to understand complex biological systems. His research focuses on bulk RNA-seq analysis in the context of developmental biology, with particular emphasis on Trisomy 21/Down syndrome, cardiac development, and hedgehog signaling pathways. With expertise in iPSC cortical neuron differentiation and neural crest cell development, he employs cutting-edge bioinformatics tools including DESeq2, maSigPro, and GSEA pathway analysis.

**Research Interests:**
- Bulk RNA-seq analysis
- Developmental biology
- Trisomy 21/Down syndrome research
- Cardiac development
- Hedgehog signaling pathways
- iPSC cortical neuron differentiation
- Neural crest cell development
- ATAC-seq analysis
- Time-series RNA-seq data analysis

**Technical Skills:**
- RNA-seq Analysis: DESeq2, maSigPro, edgeR, limma
- Data Processing: VST normalization, CPM filtering, apeglm shrinkage
- Pathway Analysis: GSEA, GO term enrichment
- Visualization: pheatmap, ggplot2, z-score winsorization
- Programming: R, Bioconductor
- Workflow Management: Nextflow, nf-core pipelines
- HPC: SLURM job scheduling

**Profile Photo:** Located at `src/personal_photo.png`

**Instructions:**
1. Clone the prasenjit52282 template repository
2. Remove the original git history and initialize a new repository
3. Update ALL configuration files with my information:
   - config.yaml (title, baseURL)
   - config/_default/params.yaml (all personal details, contact info, organization)
   - content/authors/admin/_index.md (complete bio, education, interests, social links)
   - Copy my photo from src/personal_photo.png to content/authors/admin/avatar.jpg
4. Remove ALL example publications from content/publication/
5. Update the navigation menu in config/_default/menus.yaml to include: Home, Publications, Projects, Contact
6. Remove any demo content and replace with my information
7. Create a new GitHub repository named [MY_GITHUB_USERNAME].github.io
8. Push all changes to the new repository
9. Enable GitHub Pages (Settings > Pages > Deploy from main branch)

**Important replacements:**
- Replace all instances of "Prasenjit Manna" with "Zoheb Khan"
- Replace all previous affiliations with "Moskowitz Lab, The University of Chicago"
- Update all social media links with my actual URLs (once I provide them)
- Ensure dark mode is enabled
- Keep the clean, minimalist design

Please execute these steps sequentially and let me know when the website is ready. The final website should be live at https://[ZohebKhan1].github.io

---

## Before Using This Prompt:

Replace these placeholders with your actual information:
- [ZohebKhan1] - Your GitHub username
- [https://scholar.google.com/citations?user=2gFbtqIAAAAJ&hl=en] - Your Google Scholar profile URL
- [https://www.researchgate.net/profile/Zoheb-Khan-7] - Your ResearchGate profile URL  
- [https://github.com/ZohebKhan1] - Your GitHub profile URL

## Additional Notes:

1. Make sure you have your profile photo ready at `src/personal_photo.png`
2. Have any publications ready to add (title, authors, journal, year, DOI, abstract)
3. Prepare descriptions of 2-3 research projects if you want to include them
4. Be ready to provide GitHub credentials when Claude Code asks