# manish-bilore.github.io

Quarto site. Landing page, a listing of work, a CV page. Nothing else.

## Add a project

1. Copy the block in `_templates/new-project.yml` into `projects.yml` and fill it in.
2. If the project has no site of its own, also copy `_templates/new-project.qmd`
   into `projects/<slug>.qmd` and point `path:` at it.
3. Put its hero image in `images/`. Keep files under ~500 kB — crop the
   whitespace off plot exports and save photographic images as JPEG.
4. Commit. The Action renders and publishes.

## Update a project

Edit its block in `projects.yml`. Bump `date:` if you want it to move back to
the top of the list.

## The CV PDF

`cv.qmd` links to `files/ManishBilore-CV.pdf`. That exact path and filename, or
the Download button 404s. Replace the file to update the download; nothing else
needs changing.

## Large files

`files/ManishBilore-MTech-InSAR-subsidence.pdf` is ~19 MB. Fine to commit once;
if it ever gets revised repeatedly, move it to Git LFS or attach it to a release
instead of re-committing versions into history.

## Local preview

    quarto preview

## First deploy

    git checkout --orphan gh-pages && git rm -rf . && \
      touch .nojekyll && git add .nojekyll && \
      git commit -m "init gh-pages" && git push origin gh-pages && \
      git checkout main

Then in Settings → Pages, set the source to branch `gh-pages`, folder `/`.
After that every push to `main` republishes.

## Add a notes/blog section later

    mkdir notes
    cat > notes.qmd <<'YAML'
    ---
    title: "Notes"
    listing:
      contents: notes
      type: default
      sort: "date desc"
      feed: true
    ---
    YAML

Add `- text: "Notes"` / `href: notes.qmd` to the navbar in `_quarto.yml`.
Put at least one `.qmd` in `notes/` before rendering.
