---
id: 545
title: Understanding Subnet masks and CIDR Notation
date: 2019-05-19T15:32:34+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=545
permalink: /understanding-subnet-masks-and-cidr-notation/
image: /wp-content/uploads/2019/05/CIDR-Header.png
categories:
  - Networking
tags:
  - CIDR
  - CIDR Notation
  - IETF
  - IP Address
  - Subnet
  - Subnet Mask
---
If you&#8217;ve ever set up any device that has even a basic form of networking, it&#8217;s quite likely that at some point you&#8217;ve interacted with an IP Address. One field in the configuration of an IP Address that does not seem to have a clear reason for existing is the subnet mask field. I could confidently guess that most users have only ever entered one value (255.255.255.0) and wouldn&#8217;t see the need to enter any other.

If you&#8217;ve ever used Nmap you may seen the use of CIDR notation when scanning a network, the **/XX** (192.168.0.1/24) at the end of an IP Address is the direction to scan a specific subnet.

This blog post will explore why you might need a different subnet mask and understanding the two main ways they are written. First though I think it would be helpful to understand how binary; and by extension; IP Addresses are written.

## The structure of a Binary number

One byte is made up of eight bits, with a bit being a singular one or zero. The use of eight bits is also shared with an IPv4 address which also uses four eight bit binary digits to construct an IP Address. The chart below shows the binary representation of the number 193.

<table class="wp-block-table is-style-regular">
  <tr>
    <td>
      128
    </td>
    
    <td>
      64
    </td>
    
    <td>
      32
    </td>
    
    <td>
      16
    </td>
    
    <td>
      8
    </td>
    
    <td>
      4
    </td>
    
    <td>
      2
    </td>
    
    <td>
      1
    </td>
  </tr>
  
  <tr>
    <td>
      1
    </td>
    
    <td>
      1
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
      1
    </td>
  </tr>
</table>

Using the example above it&#8217;s possible to see how the binary digits are set to one for the bits 128, 64 and 1. Adding these numbers together gets the result 193. You can adapt this to achieve any number up to 255 which is the highest value you can assign for an IP Address or subnet mask. 

## Why is a Subnet needed?

In a home setting an subnet is unlikely to be needed, but within a larger organisation can be immensely beneficial. For example, to make it easier to manage a network if departments are organised into separate smaller networks a subnet can be implemented to separate sales, marketing and finance sections of a business, without placing the machines on a physically separate network. Keeping devices on a separate network can also reduce network latency and congestion as less devices will be broadcasting on a section of network and can also help isolate security threats to the smaller section of network.

## Deciphering Subnet Mask

If you need to implement a subnet mask on a network you&#8217;ll need to update all the devices on your network to use a static IP Address and modify the subnet mask in settings to the correct numbers. But what should be entered as a subnet mask. 

The mask needed will depend on the size of the subnet required. This chart from shows all the valid subnet values.<figure class="wp-block-image">

<a href="https://tools.ietf.org/html/rfc1878" target="_blank" rel="noreferrer noopener"><img src="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2019/05/RFC-1878-Subnet-chart.png?fit=640%2C691&ssl=1" alt="Chart from the Internet Engineering Task force outlining valid subnet masks as part of the standard RFC 1878." class="wp-image-561" srcset="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2019/05/RFC-1878-Subnet-chart.png?w=1172 1172w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2019/05/RFC-1878-Subnet-chart.png?resize=278%2C300 278w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2019/05/RFC-1878-Subnet-chart.png?resize=768%2C828 768w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2019/05/RFC-1878-Subnet-chart.png?resize=949%2C1024 949w" sizes="(max-width: 640px) 100vw, 640px" /></a></figure> 

For any home network you&#8217;ll likely only be able to assign class C IP address to a device so will only be able to utilise subnet masks that modify the final octet (255.255.255.XXX). Larger organisations may have access to different classes of IP so will be able to utilise subnet masks higher up the chart.

So if we took the subnet mask 255.255.255.192 as an example we can see how this would affect a network. This mask from the chart above shows that a single network with this mask will be left with 64 addresses however, the first and last IP Addresses of any network are not able to be used; the first is used to specify a network but no host, and the last is used to broadcast to every host on the network . So if the network we were implementing this on was a standard home network range we would be left with the available IP addresses:

  * 192.168.0.1 &#8211; 192.168.0.62
  * 192.168.0.65 &#8211; 192.168.0.126
  * 192.168.0.129 &#8211; 192.168.0.190
  * 192.168.0.193 &#8211; 192.168.0.254

To write an IP Address and its subnet in full would become quite laborious so the short version to denote an IP Address on the network would be 192.168.0.45/26. So when using Nmap and typing XXX.XXX.XXX.XXX/24 we&#8217;re asking it to scan that IP address plus any others on that network using the subnet mask 255.255.255.0.