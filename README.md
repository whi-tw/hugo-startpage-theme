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

https://tnwhitwell.github.io/hugo-startpage-theme/

## Offline Use

The theme specifies and includes an appcache manifest for offline use / quick launch.

This is always included at the moment, but will be controllable / disableable via `config.toml` eventually.

For content changes to be applied, this manifest ***must*** be updated on each build.

Suggested way to get this updated is by running:

```bash
hugo
CURRENT_REVISION=$(git rev-parse --short HEAD)
sed -i "s/COMMIT_SHA/${CURRENT_REVISION}/" public/startpage.appcache
```

This will ensure that the manifest is updated on each build so the cache is rebuilt by the browser after building.

### Fixing a prematurely cached site
If the site is cached before you are ready, either:

1. add a comment to the generated startpage.appcache (changing one character will work)
2. Empty the cache on your browser, using [Andy Gup's instructions](http://www.andygup.net/deleting-an-html-application-cache/).
