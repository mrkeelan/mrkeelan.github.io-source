---
title: Batch thumbnail creation with ImageMagick
author: matthew
layout: post
date: 2009-04-09T20:08:11+00:00
summary: quickly create thumbnails from all jpg files in a directory, using a 1-line command.
url: /2009/04/batch-thumbnail-creation-with-imagemagick/
categories:
  - technology
tags:
  - imagemagick
  - graphics
  - thumbnails

---
command to create thumbnails from all jpg files in a directory:
```bash
find *.jpg -maxdepth 0 -print -exec convert "{}" -resize 120x160 "thumbnails/{}" \;
```