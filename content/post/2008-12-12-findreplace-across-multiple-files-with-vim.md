---
title: Find/Replace across multiple files with Vim
author: matthew
layout: post
date: 2008-12-12T17:34:10+00:00
url: /2008/12/findreplace-across-multiple-files-with-vim/

---
Here is a quick way to find an replace one string with another across multiple files using vim.
  
Open all the files:
```bash
vim file1.txt file2.txt file3.txt
```
Run this command:
```vim
argdo %s/original string/replacement string/gc | wn
```

This can be very useful, say if you have a static html site, and need to replace an old email address with a new one across all the pages.