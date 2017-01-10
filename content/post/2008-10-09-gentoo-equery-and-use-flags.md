---
title: 'Gentoo: equery and USE flags'
author: matthew
layout: post
date: 2008-10-09T17:47:37+00:00
url: /2008/10/gentoo-equery-and-use-flags/
---
Running:
```bash
equery depends jdk`
```
Returns:
```
dev-lang/swig-1.3.31 (java? virtual/jdk)
media-libs/pdflib-7.0.2_p8 (java? >=virtual/jdk-1.4)
```
However, "-java" is set for pdflib:
```bash
emerge -pv pdflib
```
```
These are the packages that would be merged, in order:
Calculating dependencies... done!
[ebuild R ] media-libs/pdflib-7.0.2_p8 USE="perl python -cxx -doc -java -tcl" 0 kB
```

"java?" appears to mean that it depends on it IF the java USE flag is set. I couldn&#8217;t find this documented anywhere, so I&#8217;m documenting it here.