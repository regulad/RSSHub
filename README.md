# regulad/RSSHub: build branch

This branch holds only the build pipeline, and is the repository's default
branch, so that GitHub reads its workflow and its `.github/settings.yml`. The
source is upstream's, on the other branches:

- `master` is [DIYgod/RSSHub](https://github.com/DIYgod/RSSHub)'s `master`,
  untouched.
- The other branches, such as `feat/asus-rog-support`, carry changes on their
  way upstream as pull requests.

`.github/workflows/build.yml` builds a source ref with RSSHub's own
`Dockerfile`: the ordinary image, without Chromium, for `linux/amd64`. A manual
run with `push` ticked pushes it to `ghcr.io/regulad/rsshub:<commit>`, tagged
with the source commit's full hash as upstream's per-commit images are, so a
change can run before upstream merges it:

```sh
gh workflow run build.yml -R regulad/RSSHub -f ref=feat/asus-rog-support -f push=true
```

Upstream: https://github.com/DIYgod/RSSHub
