---
id: 343
title: Library Folders and How to remove macOS Trojans
date: 2018-08-03T21:54:11+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=343
permalink: /library-folders-and-how-to-remove-macos-trojans/
image: /wp-content/uploads/2018/08/macOS-Trojans-Header.png
categories:
  - Malware
tags:
  - Library Folder
  - Mac OS X
  - macOS
  - Malware
  - OS X
  - Trojan
---
<img class="size-medium wp-image-351 aligncenter" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-Trojans-Header.png?resize=300%2C225" alt="macOS Trojans Header Image" width="300" height="225" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-Trojans-Header.png?resize=300%2C225 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-Trojans-Header.png?resize=768%2C576 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-Trojans-Header.png?w=800 800w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />

Since I started using macOS (formerly Mac OS X then OS X) over 10 years ago with 10.4 Tiger, the Mac&#8217;s marketshare has increased a number of times over predictions of a flood of Mac viruses increased with it. The apocalyptic scenarios presented by a lot of these predictions has, thankfully, not materialised, but one thing I have noticed from my time supporting Macs has been the increase in Mac Trojans.

Trojans on the Mac is not a recent phenomenon and can remember when a <a href="https://www.macworld.com/article/1138380/iworktrojan.html" target="_blank" rel="noopener">modified installer of Apple&#8217;s iWork &#8217;09 suite</a> was packaged with a Trojan, burning people who wanted iWork but didn&#8217;t want to pay. More recently in 2015, <a href="https://en.wikipedia.org/wiki/XcodeGhost" target="_blank" rel="noopener">Xcode was packaged</a> with malicious software, prompting warnings that software should only be downloaded via Apple&#8217;s official channels.

The increase I have personally seen recently all involve a variation on the same process. Either a web page or a pop-up will state that your Mac is infected with a virus and that you should call the number listed within a particular time frame. To make matters worse there is usually some sort of method used to prevent the page being closed (one way I have seen used is to generate a print dialog over and over), to add more urgency an irritating high pitched noise may be emitted. My theory on how these pages are accessed by the user are that they are possibly from a malicious ad on a webpage; have seen people come across them browsing through a variety of content.

After seeing people and removing any Trojans they have on their Mac I&#8217;m usually asked how they avoid these programs getting onto their Mac in future my advice is always similar; always check what program is asking for your administrator password, be cautious installing new programs, and if you receive any pop-ups stating that your device has a virus, close the lid and get someone trusted to check it over. But how can these Trojans be removed?

# macOS Library Folders

One of the most important pieces of knowledge I have learnt regarding macOS is the difference between its &#8220;Library&#8221; folders.

<h2 style="text-align: center;">
  User Library
</h2><figure id="attachment_356" aria-describedby="caption-attachment-356" style="width: 640px" class="wp-caption aligncenter">

<img class="wp-image-356 size-large" src="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-User-Library.png?resize=640%2C299" alt="" width="640" height="299" srcset="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-User-Library.png?resize=1024%2C479 1024w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-User-Library.png?resize=300%2C140 300w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-User-Library.png?resize=768%2C359 768w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-User-Library.png?w=1280 1280w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-User-Library.png?w=1920 1920w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> <figcaption id="caption-attachment-356" class="wp-caption-text">The Finder screenshot above shows The structure going from the main hard drive, &#8220;Macintosh HD&#8221;, drilling down to the user Library folder in column view (Macintosh HD > Users > Library).</figcaption></figure> 

<h2 style="text-align: center;">
  Root Library
</h2><figure id="attachment_346" aria-describedby="caption-attachment-346" style="width: 640px" class="wp-caption aligncenter">

<img class="wp-image-346 size-large" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-System-Library.png?resize=640%2C395" alt="macOS Root Library Screenshot" width="640" height="395" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-System-Library.png?resize=1024%2C632 1024w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-System-Library.png?resize=300%2C185 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-System-Library.png?resize=768%2C474 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-System-Library.png?w=1280 1280w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> <figcaption id="caption-attachment-346" class="wp-caption-text">This screenshot shows the structure going from the main hard drive, &#8220;Macintosh HD&#8221;, drilling down to the initial Library folder in column view (Macintosh HD > Library).</figcaption></figure> 

&nbsp;

<h2 style="text-align: center;">
  System Library
</h2><figure id="attachment_349" aria-describedby="caption-attachment-349" style="width: 640px" class="wp-caption aligncenter">

<img class="wp-image-349 size-large" src="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-System-Library-Folder.png?resize=640%2C314" alt="macOS System Library Folder" width="640" height="314" srcset="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-System-Library-Folder.png?resize=1024%2C502 1024w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-System-Library-Folder.png?resize=300%2C147 300w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-System-Library-Folder.png?resize=768%2C376 768w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-System-Library-Folder.png?w=1280 1280w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/08/macOS-System-Library-Folder.png?w=1920 1920w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> <figcaption id="caption-attachment-349" class="wp-caption-text">The system library is visible when navigating to Macintosh HD > System > Library</figcaption></figure> 

In all cases a Library folder contains files that are used for the operations of the Mac&#8217;s processes and applications, but what changes between them all is their scope. The data within the User Library folder only applies to the user it is located within. This means that if any of the files in here become an issue, at their worst they should only affect that user and so a user could move all their data to a new user account and carry on as normal.

The Root Library folder is wider in scope. The data in here can affect all user accounts and is usually where Malware will install files in addition to putting it into the User Library folder as it can then affect all users on the Mac, making it more effective for the malware author.

Initially it may not seem as though the Root and System library folders will be much different, but as a general rule the System Library contains more &#8216;system&#8217; level stuff that is created and managed by Apple rather than the greater number of third party created files in the Root Library. It is quite rare that applications will need to place objects within the System Library folder, so if malware affects this folder it makes it easier to perform an erase and reinstall, but I have yet to come across a Trojan that puts anything here.

# Removing a Trojan from macOS

After quitting the running app if possible, an initial step in removing the Trojan is to remove it from the applications folder at

/Applications

Navigate to the user folder (~/Library) and first of all choose the &#8220;Application Support&#8221; folder and find any folder with the malicious applications name and remove it. Something to bear in mind is that some apps hide their system files by giving them a different name so if you have a name in their you don&#8217;t recognise do some research to check if it&#8217;s the Trojan in disguise. Next navigate to &#8220;LaunchAgents&#8221; and remove any suspicious start up processes.

Next, move to the Root Library folder and again navigate to &#8220;Application Support&#8221; and &#8220;LaunchAgents&#8221; and remove suspicious files there. Within the Root Library there is also &#8220;LaunchDaemons&#8217;, have a browse and clear anything relating to the Trojans.

Additionally within the User Library folder there is also a &#8220;Caches&#8221; folder. This will contain cache data and so without the App this will effectively become dormant data, but if want to obliterate all trace of the malware, delete the data here.