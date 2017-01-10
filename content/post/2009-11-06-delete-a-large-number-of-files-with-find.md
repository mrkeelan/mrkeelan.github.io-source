---
title: Delete a Large Number of Files with Find
author: matthew
layout: post
date: 2009-11-06T00:19:57+00:00
summary: If you ever come across a directory full of so many files, you can't run an ls on it, here is how to delete a bunch of them, using find.
url: /2009/11/delete-a-large-number-of-files-with-find/
---
If you ever come across a directory full of so many files, you can't run an ls on it, here is how to delete a bunch of them, using find.

I recently had to delete all the gzipped files in /var/log because something was misconfigured and things went crazy.

```bash
find /var/log/ -iname "*.gz" -exec rm {} \;
```
