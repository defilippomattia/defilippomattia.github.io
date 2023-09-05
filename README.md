# Introduction

Repository for my personal website https://defilippomattia.com/

# Add new post

1. Copy content of `<REPO_ROOT>/content/posts`

2. Change name of the folder (this will be the URL of the post)

3. Change `index.md`

4. Run `hugo server -D` (will start local server, usually at `http://localhost:1313/`)

5. Check if everything is ok

6. Commit and push (changes will be automatically deployed)

# Update CV

1. Go to overleaf.com and edit the .tex file (If starting from scratch, create new project and add `de-fillippo-mattia-cv.tex` and `resume.cls` from this repo)

2. Copy changes from overleaf files to `de-fillippo-mattia-cv.tex` and `resume.cls` in this repo (optional, but in case overleaf goes down or something)

3. Download PDF and store it in `<REPO_ROOT>/static/cv.pdf`
