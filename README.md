# DARTH Docs – Updating Instructions 

## 1.  Edit the docs 

### Get the project locally 

Download or clone the DARTH-docs repository to your computer: 

~~~
cd DARTH-docs
~~~

 

### All documentation content is in the docs/ folder. 

Each .md file corresponds to a page. 

Example: 

~~~
docs/index.md   ← Home page

	docs/overview.md
  
	docs/....... (the other pages of the DARTH DOCS)
~~~

### Open the Markdown file you want to update in your code editor  

Edit the file as needed.
	
	Note: Files like edp.md appear in both the main site and EDP site, so editing them updates both.

## 2.  Preview changes locally 

Before publishing, you can see how your changes will look in the browser: 

~~~
# Preview main DARTH site
mkdocs serve -f mkdocs.yml
# Open browser: http://127.0.0.1:8000/
~~~
~~~
# Preview EDP-only site
mkdocs serve -f mkdocs_edp_only.yml
# Open browser: http://127.0.0.1:8000/DARTH-docs/edp-docs/
~~~

- Changes you save in docs/ will automatically refresh in the browser. 

## 3. Commit changes 

Once you’re happy with edits: 

~~~
git add . 

git commit -m "Update [page name or summary]"
~~~
 

## 4. Push to GitHub 

~~~
git push
~~~

This updates the main branch with your latest Markdown edits. 

## 5. Deploy the site 

Publish the updated site to GitHub Pages: 

~~~
# Build the main site
mkdocs build -f mkdocs.yml -d site

# Build the EDP-only site
mkdocs build -f mkdocs_edp_only.yml -d site/edp-docs
~~~
~~~
 # Switch to gh-pages
git checkout gh-pages

# Copy main site to root
cp -r ../DARTH-docs/site/* .

# Copy EDP site to subfolder
mkdir -p edp-docs
cp -r ../DARTH-docs/site/edp-docs/* edp-docs/

# Commit and push
git add .
git commit -m "Update main and EDP sites"
git push origin gh-pages

# Return to main
git checkout main
~~~
## 6. Live URLS
Main DARTH site:
https://UNSW-CEEM.github.io/DARTH-docs/

EDP-only site:
https://UNSW-CEEM.github.io/DARTH-docs/edp-docs/

Editing shared files (edp.md and accessssh.md) automatically updates both sites after rebuilding.
