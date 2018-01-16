# Hublin Documentation website

[![Build Status](https://ci.linagora.com/linagora/lgs/openpaas/hublin-doc/badges/master/build.svg)](https://ci.linagora.com/linagora/lgs/openpaas/hublin-doc/)

This is the documentation repository for [https://linagora.github.io/hublin-doc](https://linagora.github.io/hublin-doc).

## Develop

```
$ git clone https://github.com/linagora/hublin-doc.git
$ cd hublin-doc
```

The Web site is built using [jekyll](https://jekyllrb.com/). You can install jekyll, all its dependencies, cry, or simply run in Docker:

```
docker run --rm --label=jekyll --volume=$(pwd):/srv/jekyll -it -p 4000:4000 jekyll/jekyll jekyll serve
```

Open the browser on http://localhost:4000. Once some changes on the sources are detected, Jekyll will rebuild the Web site, you will just have to refresh your browser to get the new page.

### Tips and Tricks

#### Adding a ToC to a page

Thanks to [kramdown](https://github.com/gettalong/kramdown), which is the default markdown converter in latest Jekyll version, one can add a ToC to any page just with the following block

```
* Here is the ToC, this line is needed to generate...
{:toc}
```

Note that the first line is required, it will not be displayed in the page, but ToC will not be generated if not set. For all the ToC options, have a look [here](https://kramdown.gettalong.org/converter/html.html#toc).

#### Category order

To order categories in sidebar, prefix the category name with a number, for example in a post metadata:

```
---
title: Installation
category: 1. Quick start
order: 1
---
```

The category `Quick start` then has order 1.

### Commits

Please send your changes as pull-requests following the Hublin coding rules.

### Push changes on https://linagora.github.io/hublin-doc

You have nothing to do... Once your code has been merged into master, the repository is built on Gitlab then deployed to `gh-pages` branch on [GitHub repository](https://github.com/linagora/hublin-doc). The Github Pages then serves the static content from `gh-pages` branch.
