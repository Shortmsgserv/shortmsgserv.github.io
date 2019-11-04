---
id: 21
title: Setting Up
date: 2017-11-07T13:42:47+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=21
permalink: /setting-up/
categories:
  - Uncategorized
tags:
  - Homebrew
  - Kali
---
<p style="text-align: left">
  As a template I&#8217;ve been following <i><a href="https://www.nostarch.com/pentesting" target="_blank" rel="noopener">Penetration Testing: A Hands-On introduction to Hacking</a> </i>by Georgia Weidman, so have been attempting to install the tools mentioned in the book. The major one being <a href="https://www.kali.org" target="_blank" rel="noopener">Kali Linux</a>. Pairing this with the free <a href="https://www.virtualbox.org" target="_blank" rel="noopener">Virtual Box</a> on my MacBook Air is a great way of still being able to use macOS and all the tools I have on it without having to either buy another computer or reboot to a different operating system all the time.
</p>

<p style="text-align: left">
  However, a massive lesson from this has been that I&#8217;ll need to invest in my tools, as my nearly five year old MacBook Air with only 128GB storage is rapidly filling up. To solve this problem I purchased an external hard drive; but quickly found not only was it slow using this method, in the process of moving it back and forth between the external drive and internal; once Kali was back on my Mac it would no longer boot.
</p>

<p style="text-align: left">
  Setting up Kali the second time really helped me solidify installing things using terminal rather than a GUI (the most frustrating experience was installing Android studio which surprised me coming from a major company like Google).
</p>

<p style="text-align: left">
  In the book a Smartphone Penetration Testing Framework is also mentioned, but after much searching on the internet I&#8217;ve been unable to find it. There is a lesson in this problem though. The book was first published in 2014 and looking at the changes that have happened since then, being locked into following the book probably isn&#8217;t the best idea. While I&#8217;ll use the book as a guide for what to study and follow it for tips and ideas, I&#8217;ll look online as well as investigate personally into more up to date methods as I work through it.
</p>

<h2 style="text-align: left">
  Homebrew
</h2>

<p style="text-align: left">
  A good friend recommended a package manager for macOS called <a href="https://brew.sh" target="_blank" rel="noopener">Homebrew</a> which I cannot explain how good I felt after using it. I&#8217;d tried to install a number of different tools solely using terminal and installing directly from source, but from one installation came many. I found that installing one tool would require a number of dependencies (and perhaps those tools required their own dependencies like electronic <a href="https://en.wikipedia.org/wiki/Matryoshka_doll" target="_blank" rel="noopener">matryoshka dolls</a>), but Homebrew makes it easy. As Homebrew installs the tool you want; you can see as it pulls any dependency that tool needs as well. Combined with <a href="http://brewformulas.org" target="_blank" rel="noopener">Brew Formulas</a> to find out what you can install with Homebrew saves a massive amount of time.
</p>