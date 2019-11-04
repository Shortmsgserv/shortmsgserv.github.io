---
id: 194
title: Reconstructing a Transmitted File
date: 2018-02-06T22:45:20+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=194
permalink: /reconstructing-a-transmitted-file/
image: /wp-content/uploads/2018/02/Finding-a-JPEG-Signature.png
categories:
  - Wireshark
tags:
  - File Reconstruction
  - File Signatures
  - Hex
  - Hex Fiend
  - Wireshark
---
[Previously](http://shortmsgserv.co.uk/diving-into-wireshark/) I&#8217;ve blogged about taking initial steps using Wireshark to inspect data within a network to see what data might be leaking on a network. If there does happen to be unencrypted information being transmitted on a network you may want to see exactly what that data is in order to know how important the data is that is being exposed. I&#8217;ve created a tutorial using Wireshark and a hex editor that will allow you to reconstruct a binary from raw transmitted data.

Once you have Wireshark loaded up, navigate to a site that does not use HTTPS and you should (albeit briefly) see the data from the website collected by Wireshark. I used a site called <a href="http://www.bonsaitreegardener.net" target="_blank" rel="noopener">bonsaitreegardener.net</a> which I know has a lot of images so it allowed me to easily reconstruct an image file.

Now you have the data within Wireshark, hit the stop capture button in the toolbar and enter &#8220;http&#8221; in the display filter box at the top which will restrict the output to mainly data from the website you chose. Right click &#8220;Follow&#8221; and choose TCP Stream. This will open a separate window with the full TCP output, we will need to change the output to Raw in the &#8220;Show and save data as:&#8221; drop-down box.

The data will change from having small aspects of legibility to being a stream of <a href="https://en.wikipedia.org/wiki/Hexadecimal" target="_blank" rel="noopener">hex</a> letters and numbers. It&#8217;s best to use a Hex editor to manipulate the stream as it will be displayed with a clear structure, as I use macOS I chose a hex editor called <a href="http://ridiculousfish.com/hexfiend/" target="_blank" rel="noopener">Hex Fiend</a>, but there are others out there so find the one that&#8217;s best for you. Copy the data across from Wireshark (right click and choose select all, then right click copy) and into your hex editor.

The mass of data can seem overwhelming and it can seem difficult to even get started in extracting a usable file from this data, but once you examine the file you&#8217;ll see that as long you can determine the file&#8217;s signature, it is relatively simple to extract the data. I used a <a href="https://www.garykessler.net/library/file_sigs.html" target="_blank" rel="noopener">list of signatures</a> by Gary Kessler which lists the defining characteristics of a file and as I already knew I had a large number of JPEG&#8217;s as part of the stream I ignored any other file signatures. In reality it would be likely you wouldn&#8217;t know the exact format information was being broadcasted in ahead of time.

<img class="aligncenter size-medium wp-image-207" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/02/Finding-a-JPEG-Signature.png?resize=300%2C237" alt="Finding a JPEG Signature within Hex Fiend" width="300" height="237" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/02/Finding-a-JPEG-Signature.png?resize=300%2C237 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/02/Finding-a-JPEG-Signature.png?resize=768%2C608 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/02/Finding-a-JPEG-Signature.png?w=800 800w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" /> 

According to Garry Kessler&#8217;s website a JPEG&#8217;s signature is  the hex characters FF D8 at the start of a file and FF D9 at the end, so within Hex Fiend I searched for the start and end characters in a block of hex text and then deleted all characters surrounding this block. When you have your block of hex, save the information within Hex Fiend using a name of your choice along with the extension of the file. This file should then be accessible and viewable.<figure id="attachment_204" aria-describedby="caption-attachment-204" style="width: 360px" class="wp-caption aligncenter">

<img class="size-full wp-image-204" src="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/02/Reconstructed-Image.jpg?resize=360%2C250" alt="Reconstructed Image" width="360" height="250" srcset="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/02/Reconstructed-Image.jpg?w=360 360w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/02/Reconstructed-Image.jpg?resize=300%2C208 300w" sizes="(max-width: 360px) 100vw, 360px" data-recalc-dims="1" /> <figcaption id="caption-attachment-204" class="wp-caption-text">My final reconstructed image</figcaption></figure> 

You could carry on sifting through the data to find even more JPEGs but this at least gives you an example to follow. There are also automated methods for extracting binaries from raw data, but like me you may find you understand how a piece of technology works if you know more about the foundations.