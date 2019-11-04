---
id: 415
title: 'Reduce How Often You&#8217;re Tracked with a Pi Hole'
date: 2018-12-08T20:33:34+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=415
permalink: /reduce-how-often-youre-tracked-with-a-pi-hole/
image: /wp-content/uploads/2018/12/Pi-Hole-Header.png
categories:
  - Tools
tags:
  - Ad
  - Ad Blocking
  - Ads
  - Cloudflare
  - DNS
  - Google Public DNS
  - Pi Hole
  - Raspberry PI
---
<figure class="wp-block-image"><img src="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/12/Pi-Hole-Header.png?w=640" alt="Pi Hole Article Header Image" class="wp-image-421" srcset="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/12/Pi-Hole-Header.png?w=800 800w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/12/Pi-Hole-Header.png?resize=300%2C157 300w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/12/Pi-Hole-Header.png?resize=768%2C401 768w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /></figure> 

Nearly all websites on the internet display ads to generate revenue. While I have nothing against people making money from the content on their websites, a number of the ad networks that are used contain an enormous amount of code designed to track browsing and target ads based on that browsing history. I feel quite uneasy when any organisation tries to gather an enormous amount of data about me so looked into creating a [Pi Hole](https://pi-hole.net) with my recently purchased [Raspberry Pi](https://thepihut.com/products/raspberry-pi-3-model-b-plus).

When a website makes a request for content it makes a request to a DNS translate an URL into an IP Address (apple.com translates into 17.172.224.47). A Pi Hole works by intercepting these requests and; if the URL is listed on one of its blacklists, blocking unwanted requests.

# Setting Up

Setting up a Pi Hole is easy; excluding download times it will take you around ten minutes. I decided to use Raspbian as my operating system and installed this first using [NOOBS](https://www.raspberrypi.org/documentation/installation/noobs.md); initially I needed a mouse, keyboard, and display connected but enabled VNC and SSH so I was able to control my Raspberry Pi remotely.

The Pi Hole [Github page](https://github.com/pi-hole/pi-hole/#one-step-automated-install) lists multiple ways of installing Pi Hole using the command line, but I used the method of cloning the repository from Git Hub and then using the install script.

<pre class="wp-block-code"><code>git clone --depth 1 https://github.com/pi-hole/pi-hole.git Pi-hole
cd "Pi-hole/automated install/"
sudo bash basic-install.sh</code></pre>

Once you have the install script running you&#8217;ll be shown a DOS style screen where you&#8217;ll be asked various questions; I&#8217;ll address some of the key ones.

### IP Address

A static IP address is required for a server, the installer will ask if you&#8217;d like to use its currently assigned IP address as its static IP address. Pi Hole will then assume that this will be its permanently assigned address, a key point to remember however is if you haven&#8217;t made this IP address a permanent assignment in your routers settings, your router may assign the Raspberry Pi a different IP at some point and your Pi Hole will stop working.

### Upstream DNS

The Upstream DNS provider is entirely down to choice and the Pi Hole installer does provide a list of the most popular ones such as [Google Public DNS](https://developers.google.com/speed/public-dns/) and; my choice of provider, [Cloudflare](https://1.1.1.1).

Once you&#8217;ve finished with the setup, if you&#8217;ve installed the web interface you&#8217;ll be able to easily view how much is blocked as well as what domains are most frequently blocked. 

To configure your devices to use your Pi Hole you have three major options:

  1. On each device change your DNS server in the devices settings to the Raspberry Pi&#8217;s IP Address
  2. On your router change the DNS server to the Pi; if all your devices currently look to the router for DNS information they&#8217;ll go though the Pi for their DNS information. 
  3. Configure your Pi Hole to also work as your DHCP server, meaning it instead of your router will assign IP addresses on your network

Option number three is probably the most complicated of all three and from what I have seen has no major advantage over option two. I chose to use option one as I have other users on my network and they would not find it easy to manage the Pi hole interface to resolve an issue with their browsing.

## Effects<figure class="wp-block-image">

<img src="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/12/Pi-Hole-Admin-Interface.png?fit=640%2C508&ssl=1" alt="" class="wp-image-420" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/12/Pi-Hole-Admin-Interface.png?w=1400 1400w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/12/Pi-Hole-Admin-Interface.png?resize=300%2C238 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/12/Pi-Hole-Admin-Interface.png?resize=768%2C609 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/12/Pi-Hole-Admin-Interface.png?resize=1024%2C812 1024w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/12/Pi-Hole-Admin-Interface.png?w=1280 1280w" sizes="(max-width: 640px) 100vw, 640px" /> </figure> 

The effects of a Pi Hole on browsing have been huge. As you can see from the screenshot of my dashboard around 20% of my DNS queries are usually blocked; my all time percentage sits at 19.6% and that was from an installation at the end of October. I have only had an issue with one website not loading properly and in the months since installation.

I&#8217;ve always been quite cautious so in terms of security I can&#8217;t point definitively to a reduction in Malware, but I can see the potential of including blocklists that focus around malicious domains rather than just ad networks.