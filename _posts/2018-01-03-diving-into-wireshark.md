---
id: 158
title: Diving into Wireshark
date: 2018-01-03T21:02:16+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=158
permalink: /diving-into-wireshark/
image: /wp-content/uploads/2018/01/Wireshark-Icon.png
categories:
  - Wireshark
tags:
  - Public Wifi
  - Wifi
  - Wireshark
---
<img class="aligncenter size-full wp-image-160" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/01/Wireshark-Icon.png?resize=640%2C480" alt="Wireshark Header Image" width="640" height="480" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/01/Wireshark-Icon.png?w=640 640w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/01/Wireshark-Icon.png?resize=300%2C225 300w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" />

Public wifi networks are now so prevalent that they have become relied upon by people for a high percentage of their data usage. With the amount of data now consumed on peoples mobiles and the sometimes stingy data packages offered by carriers; public wifi is sometimes used as a the main internet connection on a mobile device. However, this widespread use comes with major downsides as public wifi is largely unencrypted and has little safeguards.

One of the issues with using public wifi is not solely that the network itself has no encryption,  but that the applications on the device may use poor security practices which expose user data to everyone else on the network.

<a href="https://www.wireshark.org" target="_blank" rel="noopener">Wireshark</a> is a highly useful tool for inspecting the traffic within a network in order to find any potential security issues. Wireshark will show the packets being sent and received on your network and the data contained within them. In order to get started I loaded Wireshark onto my Mac and allowed it to capture the data from my home network.

When using Wireshark it’s important to ensure your network adaptor is running in promiscuous mode. On my Mac I just made sure that “Capture packets in promiscuous mode” is ticked within capture preferences, but other operating systems may require more work to turn this mode on. Promiscuous mode simply means that instead of your network interface ignoring packets not meant for your device, all packets will be collected and sent for processing.

The likely event if you perform a scan of your local network is that you’ll end up with a large stream of data in a short period of time. Nowadays it is almost expected that even the most simple data is sent over an encrypted connection, so hopefully you won’t be able to find a mass of sensitive unencrypted data moving across your network.

If your network is similar to mine most of the data being moved across your home network will be related to discovery. For instance, I have a large number of packets asking who has this IP address?  Tell this IP address, which is related to the Address Resolution Protocol (ARP). There are also a number originating from the Dropbox apps built in LAN sync functionality. These packets contain information listing the version of the sync protocol as well as the host name it uses.

The mass of data Wireshark will present can be overwhelming, but it has a display filter which will come in handy to restrict data to any pertinent information you may be searching for. The thing to bear in mind is the search will require queries to be entered in a specific format for the desired information to be shown. For ease Wireshark contains an expression builder which allows you to search for the specific data you need and build your search query.

Overall the data on my network appears to largely be quite uninteresting, but the Wireshark website contains a number of <a href="https://wiki.wireshark.org/SampleCaptures" target="_blank" rel="noopener">sample captures</a> that allows you to get to grips with the behaviour of specific protocols and applications. A key thing to remember is to not actually use Wireshark on a public wifi network as this will likely be at minimum a breach of the networks terms of service if not illegal under the Computer Misuse Act.

From my exploration of Wireshark it is obviously a powerful tool and incredibly useful for a number of reason such as a specific application broadcasting data in an unencrypted form, or something more malicious that may well be sending information externally, among others.