# KomMonitor Page
KomMonitor GitHub.io Page.
## Dev Setup
For local testing:
```
docker run --rm \
  --volume="$PWD/docs:/srv/jekyll" \
  --publish 4000:4000 \
  --publish 35729:35729 \
  -it jekyll/jekyll:pages \
  jekyll serve --livereload --force_polling
```
