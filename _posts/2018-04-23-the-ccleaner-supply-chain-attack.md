---
id: 280
title: The CCleaner Supply Chain Attack
date: 2018-04-23T21:40:02+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=280
permalink: /the-ccleaner-supply-chain-attack/
image: /wp-content/uploads/2018/04/Third-Party-Software-Header.png
categories:
  - Software
tags:
  - Adobe
  - Apple
  - Avast
  - CCleaner
  - Flash
  - Software
  - Third Party
  - Third-Party Software
---
<img class="size-medium wp-image-281 aligncenter" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Third-Party-Software-Header.png?resize=300%2C225" alt="Third Party Software Header Image" width="300" height="225" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Third-Party-Software-Header.png?resize=300%2C225 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Third-Party-Software-Header.png?resize=768%2C576 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Third-Party-Software-Header.png?w=800 800w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />

This week Avast <a href="https://www.wired.com/story/inside-the-unnerving-supply-chain-attack-that-corrupted-ccleaner/" target="_blank" rel="noopener">disclosed</a> exactly how its <a href="https://www.ccleaner.com" target="_blank" rel="noopener">CCleaner</a> software was compromised in September last year. Avast found that the attackers logged into a TeamViewer remote desktop account on a Piriform developers computer (Piriform being the company that created CCleaner that was acquired by Avast shortly before the disclosure).

With access to the remote desktop account the attackers gained access to other computers eventually installing a piece of malware called ShadowPad, part of which contains a key logger. With the information gleaned from this the attackers were able to work their way into Piriform&#8217;s development systems and eventually give themselves the ability to manipulate the downloadable CCleaner file.

A more extensive explanation is contained within the Wired article I&#8217;ve linked to, but the reason I&#8217;ve blogged is because I think this highlights the risks with third-party software. Working within technical support on a daily basis I see multiple people come to me with varying types of third party software installed and most people install a large number of third party software without question. For sometime though I have tried to refrain myself from installing third party software.

Shortly after the iPhone&#8217;s release when Apple faced intense pressure to allow Adobe&#8217;s Flash to work on iOS devices Steve Job&#8217;s released his &#8220;<a href="https://www.apple.com/hotnews/thoughts-on-flash/" target="_blank" rel="noopener">Thoughts on Flash</a>&#8221; letter which outlined his reasoning for not allowing Flash on iOS. An example Steve Jobs used was that &#8220;_Symantec recently highlighted Flash for having one of the worst security records in 2009. We also know first hand that Flash is the number one reason Macs crash_&#8220;; I also think I remember the point that Flash being the number one reason Macs crash being said again during a presentation regarding macOS, but haven&#8217;t been able to find the video.

Since that point in 2009 I&#8217;ve restricted myself installing third-party software and plug-ins as liberally as I did before that. I&#8217;ve now come to think that with each piece of software installed I&#8217;m increasing the number of possible attack vectors an attacker can use to attack my machine; both Flash and the ever popular Acrobat contain a <a href="https://helpx.adobe.com/uk/security.html" target="_blank" rel="noopener">not insignificant amount</a> of security advisories on Adobe&#8217;s website.

Initially I may seem unreasonable, perhaps puritanical with regards to my attitude toward third-party software, as though I never install anything that isn&#8217;t part of a standard operating system installation and expect software to have zero security issues, I assure you that is not the case. Security issues will always be found in software and Flash and Acrobat&#8217;s long list of vulnerabilities [arguably] shows that Adobe heavily invests in finding security issues in their software and focuses on fixing them. And if macOS doesn&#8217;t contain the tool I need to what I need I&#8217;m more than open to installing something that does; among software I have installed is 1Password, VirtualBox, Postgres and Scrivener among others.

What I am advocating is a more considered approach to installing third-party software. Do you really need to install Flash given that most internet video is HTML5 video now? Could you just use the built in PDF reader instead of installing Acrobat Reader? Perhaps your computer isn&#8217;t cluttered enough to install that cache cleaner software? The answer to the question will depend on what the user is looking to do and their level of knowledge about what they&#8217;re installing.

&nbsp;