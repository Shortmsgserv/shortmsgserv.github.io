---
id: 286
title: 'Hack the Box &#8211; Bashed User Own'
date: 2018-04-30T14:09:53+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=286
permalink: /hack-the-box-bashed-user-own/
image: /wp-content/uploads/2018/04/Bashed-Header.png
categories:
  - Exploits
tags:
  - Arrexel
  - Bashed
  - Hack the Box
  - Linux
  - Nmap
  - phpbash
  - User Own
---
<img class="aligncenter wp-image-290 size-medium" src="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Bashed-Header.png?resize=300%2C225" alt="Bashed Header Image" width="300" height="225" srcset="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Bashed-Header.png?resize=300%2C225 300w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Bashed-Header.png?resize=768%2C576 768w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Bashed-Header.png?w=800 800w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />

For quite sometime now I&#8217;ve been wanting to publish the write-up to my first successful hack on <a href="https://www.hackthebox.eu" target="_blank" rel="noopener">Hack the Box</a> but as part of their terms of service you aren&#8217;t allowed to publish your write-up until that machine has been retired. Now that the Bashed machine has been retired I finally can. If you haven&#8217;t already I&#8217;d recommend signing up to Hack the Box to build your hacking skills; entry to the site is not as simple as entering your details to get your account, you have to do a little work first.

The particular machine I started off with first is the Bashed machine by Arrexel. With all the machines I&#8217;ve at least tested, if not hacked successfully I&#8217;ve tried to find out more information about them. The information page on Hack the Box lists what OS the machine is running, but little else so I always start by running an Nmap scan using the command

_$ nmap -sV 10.10.10.68_

The addition of -sV asks Nmap to try and ascertain the version of the service it finds running which for Bashed generated

_80/tcp open http Apache httpd 2.4.18 ((Ubuntu))_

As the results of the scan showed it to be a web server within Firefox I typed the address 10.10.10.68 to see if any useful information was shown on the webpage. This provided me a small hint of what I&#8217;d need to crack the machine, but I still needed to find out more. One of the first tools I use to find interesting areas on web servers is the http-enum script within Nmap. To use command I entered

_$ nmap &#8211;script http-enum 10.10.10.68_

returning

80/tcp open http  
| http-enum:  
| /css/: Potentially interesting directory w/ listing on &#8216;apache/2.4.18 (ubuntu)&#8217;  
| /dev/: Potentially interesting directory w/ listing on &#8216;apache/2.4.18 (ubuntu)&#8217;  
| /images/: Potentially interesting directory w/ listing on &#8216;apache/2.4.18 (ubuntu)&#8217;  
| /js/: Potentially interesting directory w/ listing on &#8216;apache/2.4.18 (ubuntu)&#8217;  
| /php/: Potentially interesting directory w/ listing on &#8216;apache/2.4.18 (ubuntu)&#8217;  
|_ /uploads/: Potentially interesting folder

Luckily this isn&#8217;t too many folders and so I manually browsed though them looking for interesting material, finding that most were not that useful apart from /dev. Inside /dev are two files phpbash.min.php and phpbash.php. phpbash is an interactive web shell created by Arrexel and is available on their <a href="https://github.com/Arrexel/phpbash" target="_blank" rel="noopener">Github page</a> if you want to use it elsewhere. If this was an organisation it is unlikely (although perhaps not impossible) that they would leave a web shell available for public use, but for Hack the Box it is there and never look a gift horse in the mouth. If you were looking to use this on a server you are pen testing, you would have to find a way of uploading the shell first.

Phpbash.php will show a shell that will likely be familiar; Arrexel states on the Github page it is designed in the Kali colours to make it recognisable. My first command was to see if I could navigate out of the directory I started entering

$ cd /

surprisingly I managed to leave that directory so typed

$ ls

to see what other files were available to browse at this level.

<img class="aligncenter wp-image-289 size-large" src="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Bashed-Directories.png?resize=640%2C581" alt="Hack the Box Bashed Directories" width="640" height="581" srcset="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Bashed-Directories.png?resize=1024%2C930 1024w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Bashed-Directories.png?resize=300%2C272 300w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Bashed-Directories.png?resize=768%2C697 768w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/Bashed-Directories.png?w=1324 1324w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> 

As I was aiming to get the &#8216;User Own&#8217; this I needed to find where the hash was located. To quickly find this it helps to have a basic knowledge of the file structure of Linux. I only have a knowledge in the areas where it is similar to macOS; so is only useful to a limit. macOS places all its users within a &#8216;Users&#8217; directory and each user&#8217;s directory is referred to as their &#8216;home&#8217; directory. macOS does contain a &#8216;usr&#8217; directory which is in our results list (apologies as usr, var and vmlinuz are not shown in the results above), but on macOS this directory is hidden and is different to the &#8216;Users&#8217; directory that is not hidden. This leaves &#8216;home&#8217; as the most likely lead and so I navigate to it

$cd /home

this contained two users &#8216;arrexel&#8217; and &#8216;scriptmanager&#8217;. As Arrexel is the creator of this machine this is likely to be set as the main user on the box, so I navigate into it and find a user.txt file and viewed the contents with

$ cat user.txt

giving me the user own hash.

# Lessons Learnt

The write-up I&#8217;ve done makes it appear as though I had got from start to user own in about 5 minutes, but I can honestly say this took me around 10 hours as I tried all sorts of different techniques thinking that it would be far more complicated than it was. This was also the first time I&#8217;d attempted to hack into a machine and so am likely to attempt or adapt this method first with my subsequent hacks. This has also also shown me that persistence will pay off and a technique that might seem like it was useless to perform, may actually be useful when adapted later.

Unfortunately with Bashed I have never managed to get the root own, but have done this with another machine on Hack the Box called Nibbles. Once Nibbles has been retired I look forward to publishing the write-up and the lessons I have learnt from it.