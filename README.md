# DARTH Docs – Editing & Deployment Instructions

This repository contains the DARTH documentation built with MkDocs and deployed to GitHub Pages.

There are two sites:

1. Main DARTH documentation site (full navigation)  
   https://unsw-ceem.github.io/DARTH-docs/

2. Standalone EDP page (EDP-only content, separate build)  
   https://unsw-ceem.github.io/DARTH-docs/edp-docs/edp/

------------------------------------------------------------

1. Get the project locally

Clone the repository and enter it:

    git clone https://github.com/UNSW-CEEM/DARTH-docs.git
    cd DARTH-docs

------------------------------------------------------------

2. Edit documentation content

All documentation content lives in the docs/ folder.

Each Markdown file corresponds to a page on the site.

Example structure:

    docs/
      index.md              ← Home page
      tables_summary.md
      ausgrid300.md
      solar_analytics_2019.md
      pv_bushfire.md
      victorian_consumers.md
      edp.md                ← EDP page (shared)
      accessweb.md
      accessssh.md

Important note about EDP:

- docs/edp.md is used by:
  - the main DARTH site
  - the standalone EDP site
- Editing this file updates both, once rebuilt and deployed.

Open any .md file in your editor and make your changes.

------------------------------------------------------------

3. Preview changes locally

Preview the main DARTH site:

    mkdocs serve -f mkdocs.yml

Open in your browser:

    http://127.0.0.1:8000/

Preview the standalone EDP site:

    mkdocs serve -f mkdocs-edp.yml

Open in your browser:

    http://127.0.0.1:8000/

Both previews auto-refresh when files are saved.

------------------------------------------------------------

4. Commit your Markdown changes

Once you are happy with your edits:

    git add docs
    git commit -m "Update documentation: short description"
    git push origin main

This updates the source content, but does not publish the site yet.

------------------------------------------------------------

5. Deploy the sites

A. Deploy the main DARTH site

    mkdocs gh-deploy -f mkdocs.yml

This builds and publishes the main site to GitHub Pages.

------------------------------------------------------------

B. Deploy the standalone EDP site

The EDP site is built separately and copied into the main site output.

    rm -rf site-edp-temp
    mkdocs build -f mkdocs-edp.yml -d site-edp-temp

    rm -rf site/edp-docs
    mkdir -p site/edp-docs
    cp -r site-edp-temp/* site/edp-docs/

    mkdocs gh-deploy -f mkdocs.yml --dirty

------------------------------------------------------------

6. Commit standalone site configuration

The standalone site configuration is tracked in Git.

After deploying the EDP site:

    git add mkdocs-edp.yml site/edp-docs
    git commit -m "Update standalone EDP site"
    git push origin main

------------------------------------------------------------

7. Live URLs

Main DARTH site:
https://unsw-ceem.github.io/DARTH-docs/

Standalone EDP page:
https://unsw-ceem.github.io/DARTH-docs/edp-docs/edp/

------------------------------------------------------------

Important rules:

- Do not manually edit the gh-pages branch
- Do not commit random changes in site/
- Only commit site/edp-docs/ when updating the standalone EDP site
- Always deploy before committing generated standalone files
