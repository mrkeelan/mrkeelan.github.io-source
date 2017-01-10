---
title: How To Run Multiple IIS WebSites on Windows XP
author: matthew
layout: post
date: 2009-01-07T23:20:23+00:00
excerpt: |
  IIS in Windows XP will not let you create more than one web site.
  To get around that you can use a commandline tool to copy the default site.
  Run the following from a DOS prompt:
  
  &gt; cd c:\Inetpub\AdminScripts
  &gt; cscript adsutil.vbs COPY W3SVC/1 W3...
url: /2009/01/how-to-run-multiple-iis-websites-on-windows-xp/
enclosure:
  - |
    |
        
        
        
syndication_source:
  - 'matthew&#039;s blog'
syndication_source_uri:
  - http://matthewkeelan.com/drupal/blog/1
syndication_source_id:
  - http://matthewkeelan.com/drupal/blog/1/feed
"rss:comments":
  - 'http://matthewkeelan.com/drupal/node/31#comments'
syndication_feed:
  - http://matthewkeelan.com/drupal/blog/1/feed
syndication_feed_id:
  - 1
syndication_permalink:
  - http://matthewkeelan.com/drupal/node/31
syndication_item_hash:
  - 21ce51f51d0f6b8ef81f06dbfdd49a2f

---
IIS in Windows XP will not let you create more than one web site.

To get around that you can use a commandline tool to copy the default site.
  
Run the following from a DOS prompt:
  
`IIS in Windows XP will not let you create more than one web site.

To get around that you can use a commandline tool to copy the default site.
  
Run the following from a DOS prompt:
  
` 

Now you can modify the copy as you want. The catch is that only one site can be running at a time, so you&#8217;ll need to stop one, and start the other to switch sites. This works fine for development purposes though.

I found this info here: [http://www.bobshowto.com/iis_servers.htm][1]

 [1]: http://www.bobshowto.com/iis_servers.htm "http://www.bobshowto.com/iis_servers.htm"