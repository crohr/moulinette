# moulinette
Turn GitHub issues into blog posts

## How it works

On issue created, a github action workflow is launched to:
*   fetch the issue
*   if the issue doesn't have the `published` label, skip it
*   create a new file with the corresponding markdown content in the `pages/<issue-number>-<issue-title-slugified>` directory (configurable)
*   if images are present in the markdown, it will fetch them and store them locally in `assets/images/<issue-number>/<image-name>`. Markdown content is then replaced to include the new image path.
*   execute the page builder, if any (`bin/build`)
*   commit the build folder (default: `build/`) to gh-pages and push

On issue title changed:
* add redirect rule from old path to new path (easy to do with cloudflare pages)

On issue `published` label removed, or issue removed:
* remove the corresponding page, rebuild and push

On issue body changed:
* same as issue created.

## Features

* custom domain support (with cloudflare pages)
* redirects (with cloudflare pages)
* fetches markdown images and store them locally
