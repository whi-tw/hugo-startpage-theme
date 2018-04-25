# Startpage theme for hugo
## Instructions
Create data/links.yml in your site directory

This file takes the following format:

```yaml
---
- name: Some card title
  colour: blue # (a valid mdl color name)
  sections: # A section
  - links:
    - title: Google
      url: https://www.google.com
    - title: Bing
      url: https://www.bing.com/
  - links:
    - title: Hacker News
      url: https://news.ycombinator.com/
    - title: Reddit r/devops
      url: https://www.reddit.com/r/devops/
  - links:
    - title: Al Jazeera
      url: https://www.aljazeera.com/
```

## Demo Site (partially using the above links.yml)

* [GitHub Pages (most recent build)](https://tnwhitwell.github.io/hugo-startpage-theme/)
* [Hugo themes site (current release)](https://themes.gohugo.io/theme/hugo-startpage-theme/)

## Offline Use

The theme includes an appcache manifest for offline use / quick launch.

This is disabled by default, and can be enabled through the site parameters in `config.toml`:

```toml
[params]
    offline = true
```
If offline use is not desired or required, either omit the parameter (it is off by default) or set `offline = false`.

### Usage notes for offline-mode

For changes to your startpage to be applied after a build, this manifest ***must*** be modified on each build.

If your site is in a git repo, the suggested way to get this updated is by running the following after each successful build:

```bash
hugo
CURRENT_REVISION=$(git rev-parse --short HEAD)
sed -i "s/COMMIT_SHA/${CURRENT_REVISION}/" public/startpage.appcache
```

This will ensure that the manifest will be re-read by the browser, and all content re-cached.

### Fixing a prematurely cached site
If the site is cached before you are ready, the following will help:

1. Add a comment / modify the version string of the generated startpage.appcache (changing one character will work) and reload 
2. Build the site with `offline = false` and refresh the page
3. Empty the cache on your browser, using [Andy Gup's instructions](http://www.andygup.net/deleting-an-html-application-cache/).

## Acknowledgements
[@analbeard](https://github.com/analbeard) - for the inspiration to create the theme and guidance
