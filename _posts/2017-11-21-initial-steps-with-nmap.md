---
id: 57
title: Initial Steps with Nmap
date: 2017-11-21T16:28:22+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=57
permalink: /initial-steps-with-nmap/
categories:
  - Nmap
tags:
  - Network Scanning
  - Nmap
  - Tools
---
Browsing through the many tools a good pen tester needs, nearly all other tools refer to <a href="http://nmap.org" target="_blank" rel="noopener">Nmap</a>. This isn’t surprising as at its core; Nmap is primarily about finding intelligence on a target, such as what services and ports are running and how aggressive the firewall protecting it, if any, may be.

While on the nmap.org website itself I believe there is a disk image readily available to install Nmap and its easier to use GUI front-end Zenmap, I’m looking to use the tools in their most useful form so installed Nmap using the command line. I did however use <a href="https://brew.sh" target="_blank" rel="noopener">Homebrew</a> to install this which I mentioned in my [Setting Up](http://shortmsgserv.co.uk/setting-up/) blog post to streamline the process by also grabbing any dependancies that a program needs.

This meant I was up and running with Nmap in minutes and able to run an initial scan relatively quickly to see what its initial output would be. I also had a read of the <a href="https://nmap.org/book/man.html" target="_blank" rel="noopener">Nmap reference guide</a> which lists the arguments Nmap uses, but with the mass of information this provides I think it more effective to learn by actually putting it into practice.

My plan to learn Nmap is to use old, out of date operating systems in [VirtualBox](https://www.virtualbox.org) and use those to build up my knowledge of spotting and investigating vulnerabilities, but for my initial learning I’ve scanned various devices on my home network to get used to the various features and syntax that Nmap uses. The first device I scanned was an AirPort Extreme that is my home router.

<img class="wp-image-69 size-large alignnone" src="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/nmap_initial_scan_web.png?resize=640%2C437" alt="Nmap Initial Scan" width="640" height="437" srcset="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/nmap_initial_scan_web.png?resize=1024%2C699 1024w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/nmap_initial_scan_web.png?resize=300%2C205 300w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/nmap_initial_scan_web.png?resize=768%2C524 768w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/nmap_initial_scan_web.png?w=1196 1196w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> 

This initial scan gives basic level output such as ports and services open and the devices MAC address (I’ve erased this in the image).  At the basic level Nmap is quite easy to understand showing what the ports that are open on a device, the protocol they use, and what services they’re running. With no Nmap arguments this output level is quite barebones with almost no information of what Nmap has actually done to find this information. Using the verbosity argument gives a greater output on what Nmap has actually done to find the information. Combining the verbosity argument with -O for Operating System detection provided a more detailed output of the steps Nmap took to detect the OS that was running on my Airport Extreme.

<img class="wp-image-70 size-large alignnone" src="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/nmap_verbose_os_scan.png?resize=640%2C791" alt="Nmap Verbose OS Scan" width="640" height="791" srcset="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/nmap_verbose_os_scan.png?resize=829%2C1024 829w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/nmap_verbose_os_scan.png?resize=243%2C300 243w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/nmap_verbose_os_scan.png?resize=768%2C948 768w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/nmap_verbose_os_scan.png?w=1364 1364w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/nmap_verbose_os_scan.png?w=1280 1280w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> 

Once I had these initial steps done I then thought I’d use Nmap in conjunction with one of the scripts in its database to check for a vulnerability. A common one which many systems are still affected by is <a href="http://heartbleed.com" target="_blank" rel="noopener">Heartbleed</a>. I thought I’d check to make sure my website host (<a href="https://www.siteground.co.uk" target="_blank" rel="noopener">Siteground</a>) had remedied any Heartbleed vulnerability. After running the built-in Nmap Heartbleed script I found that all SSL services were not vulnerable so can rest easy that my host has fully updated (perhaps a refund would be a good idea if they hadn’t updated after this much time).

Overall I’ve found that initially Nmap can seem daunting, but after taking the time to understand the structure for using arguments and also what the output it produces actually means Nmap does not seem as intimidating. That said I know I have only scratched the surface of Nmap and as I use it to do far more in-depth analysis, I may find the difficulty far greater.