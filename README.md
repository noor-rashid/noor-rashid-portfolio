# Noor Rashid - ML Portfolio

Minimal Quarto-based portfolio site ready for project documentation as they're completed.

**Live Site:** [yourusername.github.io/noor-rashid-portfolio](https://yourusername.github.io/noor-rashid-portfolio) *(after deployment)*

---

## Current Status

**Phase:** Portfolio skeleton deployed, projects under development

This is a clean slate portfolio ready to showcase production ML projects as they're completed. The site infrastructure is deployment-ready; content will be added iteratively.

---

## Project Structure

```
noor-rashid-portfolio/
├── _quarto.yml              # Site configuration
├── index.qmd                # Landing page (coming soon message)
├── about.qmd                # Personal bio
├── styles.css               # Academic light mode styling
├── assets/                  # Images, logos, favicon
├── projects/                # (Empty - ready for real projects)
└── README.md
```

---

## Setup & Local Development

### Prerequisites
- **Quarto CLI:** [Install Quarto](https://quarto.org/docs/get-started/)

### Installation

1. **Create project directory**
   ```bash
   mkdir noor-rashid-portfolio
   cd noor-rashid-portfolio
   ```

2. **Add the core files** (from this bundle)
   - Copy each FILE section above into its respective filename
   - Create empty `assets/` directory: `mkdir assets`

3. **Preview the site locally**
   ```bash
   quarto preview
   ```
   Opens live preview at `http://localhost:XXXX`

4. **Build the static site**
   ```bash
   quarto render
   ```
   Output appears in `_site/` directory

---

## Customization Checklist

Before deploying:

- [ ] **_quarto.yml:** Update GitHub/LinkedIn/email links with your actual URLs
- [ ] **about.qmd:** Fill in Oxford degree details, interests, background
- [ ] **assets/:** Add optional logo (`logo.png`) and favicon (`favicon.png`) 
  - If you don't have these, remove the logo/favicon lines from `_quarto.yml`
- [ ] **index.qmd:** Adjust bio and tech stack to match your actual skills

---

## Deployment to GitHub Pages

### Step 1: Create GitHub Repository
```bash
# In your local project directory
git init
git add .
git commit -m "Initial portfolio skeleton"
gh repo create noor-rashid-portfolio --public --source=. --push
# Or create repo manually on GitHub and push
```

### Step 2: Deploy
```bash
quarto publish gh-pages
```

Follow prompts to authenticate. Your site will be live at:  
`https://yourusername.github.io/noor-rashid-portfolio`

### Step 3: Enable GitHub Actions (Optional Auto-Deploy)
Create `.github/workflows/publish.yml`:

```yaml
name: Publish Quarto Site

on:
  push:
    branches: [main]

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v3
      
      - uses: quarto-dev/quarto-actions/setup@v2
      
      - name: Render and Deploy
        run: quarto publish gh-pages --no-prompt --no-browser
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Now every push to `main` auto-deploys your site.

---

## Adding Your First Real Project

When you complete a project (e.g., `recommendation-system`):

1. **Create project folder:**
   ```bash
   mkdir -p projects/recommendation-system
   ```

2. **Add documentation files:**
   ```
   projects/recommendation-system/
   ├── index.qmd             # Overview linking to GitHub repo
   ├── problem-statement.qmd # Business context
   ├── data.qmd              # ETL, feature engineering
   ├── modelling.qmd         # Algorithm, training
   ├── deployment.qmd        # API, Docker, K8s
   ├── monitoring.qmd        # Drift detection, alerts
   ├── results.qmd           # A/B tests, metrics
   └── assets/               # Screenshots, plots
   ```

3. **Update `_quarto.yml` navbar:**
   ```yaml
   - text: "Projects"
     menu:
       - text: "Recommendation System"
         href: projects/recommendation-system/index.qmd
   ```

4. **Update `index.qmd`:** Replace "Coming Soon" card with actual project card

5. **Test and deploy:**
   ```bash
   quarto preview  # Check locally
   git add .
   git commit -m "Add recommendation system project"
   git push        # Auto-deploys via GitHub Actions
   ```

---

## Assets (Optional)

**Logo:** Create a simple 200x50px PNG with your initials or name  
**Favicon:** 32x32px icon (can use same logo, scaled down)  

If you don't have these, remove from `_quarto.yml`:
```yaml
# Remove or comment out:
logo: assets/logo.png
favicon: assets/favicon.png
```

---

## Tech Stack

- **Quarto:** Static site generator with academic styling
- **GitHub Pages:** Free hosting with CI/CD
- **Cosmo Theme:** Bootstrap-based light theme

---

## Next Steps

1. Deploy this skeleton to GitHub Pages TODAY (gets your URL live)
2. Start building your first production ML project
3. Document as you go using the project structure above
4. Update portfolio with real work incrementally

---

## Questions?

Reach out via [email](mailto:your.email@example.com) or open an issue in this repo.


