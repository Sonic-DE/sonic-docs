# Sonic-DE documentation

User and developer documentation for Sonic-DE, published on [sonicde.org](https://sonicde.org).

This repository is the only place the documentation is written. The site reads it from
GitHub (the Winter CMS docs plugin downloads this repository's archive) and renders the
Markdown; pages are never edited on the site itself.

## Layout

```
toc.yaml               table of contents: the site's navigation and page order
home.md                the documentation's front page
getting-started/
  building.md          building Sonic-DE with sonicde-builder
  dependencies.md      the packages each platform needs
  troubleshooting.md
user/                  guides for people using Sonic-DE
developer/             guides for people developing Sonic-DE and its apps
LICENSE
```

## Writing pages

- One Markdown file per page. Add every new page to `toc.yaml`, or it won't appear in the
  site's navigation.
- Link to other pages with relative paths, as they sit in this repository.
- Write instructions from what Sonic-DE actually does: the builder's scripts, the source.
  Only document a platform or a step once it has been built or tested there.
- The site shows an "Edit this page" link to the page's file here.

## Pages adapted from KDE

Some pages are adapted from KDE documentation (application handbooks, develop.kde.org,
UserBase). An adapted page keeps its attribution and is released under the same licence as
its source. Content licensed only under the GFDL stays under the GFDL. The licence is tracked
per page; don't assume one licence for every page.

## API reference

The API reference for the Sonic-DE libraries isn't written here. It's generated from the
source code's documentation comments and published separately.

## Licence

Original content is licensed under [CC BY-SA 4.0](LICENSE), which matches the KDE content
it is published alongside. Adapted pages state their own licence where it differs.
