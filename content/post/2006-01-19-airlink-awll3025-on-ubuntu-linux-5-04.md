---
title: Airlink+ AWLL3025 on Ubuntu Linux 5.04
author: matthew
layout: post
date: 2006-01-19T06:21:03+00:00
categories:
  - technology
tags:
  - ubuntu
  - airlink
  - wifi
---
Note: I&#8217;m writing this mostly from memory, will go back and check, and update this to make sure it&#8217;s completely correct.

The [Airlink+ AWLL3025][1] is a cheap 802.11g USB adapter.

Open Source Linux drivers for this adapter, however they aren&#8217;t usually included with any distro that I have seen, so you&#8217;ll need to compile them from source.

It seems the source files are not hosted on sourceforge anymore.

[http://zd1211.ath.cx/][2] is the homepage for the zd1211 driver project.

[Here][3] is a direct link to the files.

I got zd1211-driver-r38.tgz because i read that it worked with the kernel.

I like to save files for compiling into my home directory, under a sub directory src.

Go to whereever you saved it. 

<div class="code">
  cd /home/matt/src/ <br /> tar &#8211;gzip -xvf zd1211-driver-r38.tgz <br /> cd zd1211-driver-r38<br /> vi Makefile
</div>

edit the variables to match your linux source directory.

Get needed software from the Ubuntu Repository: 

<div class="code">
  sudo apt-get install build-essential<br /> sudo apt-get install linux-headers<br /> sudo apt-get install linux-source-2.6.10-5-i386
</div>

Unpack the linux kernel source: 

<div class="code">
  cd /usr/src<br /> sudo tar &#8211;bzip2 -xvf linux-source-2.6.10-5-i386.gz
</div>

Create some necessary symbolic links: 

<div class="code">
  ln -s /usr/src/linux-source-2.6.10-5-i386 /usr/src/linux<br /> ln -s /usr/src/linux/ /lib/modules/2.6.10-5-i386/build
</div>

<div class="code">
  cd /home/matt/src/zd1211-driver-r38<br /> make<br /> make install
</div>

now edit a few files

edit /etc/modprobe.d/aliases
  
add the line: 

<div class="code">
  alias wlan0 zd1211
</div>



edit /etc/network/interfaces 

<div class="code">
  iface wlan0 inet dhcp
</div>



Load the module: 

<div class="code">
  modprobe -i zd1211<br /> lsmod | grep zd1211
</div>



You should see the module loaded.

At this point in connected to my neighbors &#8216;linksys&#8217; open network.
  
Tomorrow i will fix it to connect to my WEP protected network.

 [1]: http://www.airlinkplus.com/wireless/awll3025.htm "Airlink+ AWLL3025"
 [2]: http://zd1211.ath.cx/ "http://zd1211.ath.cx/"
 [3]: http://zd1211.ath.cx/download "http://zd1211.ath.cx/"