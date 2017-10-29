# Hugo project for Serval Project Blog
A [Hugo](https://gohugo.io) project for the 
[Serval Project](http://www.servalproject.org/).

## Setting up
1. Install [Hugo](https://gohugo.io) (available in the package managers of OSX
   and most Linuxes).
2. Clone this repository with the `--recursive` option (to also get the theme).
3. Enter the repository directory and run `hugo`.
4. Upload the contents of the `public` directory to your web server.

## Authoring articles
- Articles are in [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
  and are stored in the `content` directory.
- Each article must have the following meta-data at the top:
```
+++
date = "YYYY-MM-DD"
title = "Article Title"
author = "Article Author"
+++

```
- Place images and static files in the `static` directory (treat this as the
  root for their reference URIs).
- To preview articles locally, run `hugo serve`.
- To generate the site for deployment, run `hugo`. The files to be placed on the
  server are generated in the `public` directory.

## Notes
- Articles before October 2017 are dumped in their original html format with
  some meta-data in their head. Their images reference the original URL. In the
  future, the old images must be migrated.
- Articles before October 2017 were migrated using an automated script, so may
  have some errors.
- During development, a test server is running [Here](https://comp2722.com).
  When deploying to a different URL, update the `baseurl` property in
  `config.toml`
