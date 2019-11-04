---
id: 274
title: Cracking WEP Encryption
date: 2018-04-09T17:14:26+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=274
permalink: /cracking-wep-encryption/
image: /wp-content/uploads/2018/04/WEP-Decryption-Header.png
categories:
  - Aircrack-ng
  - Wireshark
tags:
  - Aircrack
  - Aircrack-ng
  - Brute Force
  - Decryption
  - Encryption
  - IEEE 802.11
  - Packet Capture
  - WEP
  - Wifi
  - Wireshark
  - WPA
  - WPA2
---
<img class="size-medium wp-image-277 aligncenter" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/WEP-Decryption-Header.png?resize=300%2C225" alt="WEP Decryption Header" width="300" height="225" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/WEP-Decryption-Header.png?resize=300%2C225 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/WEP-Decryption-Header.png?resize=768%2C576 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/04/WEP-Decryption-Header.png?w=800 800w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />

Recently I was tasked with cracking the WEP Encryption of a sample capture generated using Wireshark. With a sample capture provided this didn&#8217;t take long and thought I&#8217;d do a quick tutorial on how I did it.

## NOTE:

A warning is usually appended to any article concerning the capture of packets on a network and this is no different. Never connect to a network (such as public Wi-fi) and capture packets from users who are unaware their data is being captured. Not only is this unethical, but is likely a criminal offence.

## Tools You Will Need

If you&#8217;ve already have sample capture (in a Wireshark readable format) the only thing you&#8217;ll need to install is <a href="https://www.wireshark.org" target="_blank" rel="noopener">Wireshark</a> and <a href="https://aircrack-ng.org" target="_blank" rel="noopener">Aircrack-ng</a>. Again I&#8217;m on macOS have have <a href="http://brew.sh" target="_blank" rel="noopener">Homebrew installed</a> so installed Wireshark in terminal using the command

_$ brew install wireshark_

and for Aircrack-ng ran the command

_$ brew install aircrack-ng_

## Cracking the Capture

Initially my capture was in Wireshark&#8217;s newer .pcapng format whereas Aircrack-ng will only accept the older .pcap format. If this is the case for you, import your capture into Wireshark and save a copy as the older format to be used with Aircrack-ng.

In terminal typing Aircrack-ng will show you that it needs a command structure of _$ aircrack-ng [options] <.cap / .ivs file>_ so I entered the command:

_$ aircrack-ng -a 1 /myfilepath/mycapture.pcap_

The key part of that command is likely the &#8220;-a 1&#8221; section. -a informs Aircrack to perform force attack mode and the &#8220;1&#8221; informs Aircrack what type of encryption it used (1 being WEP, 2 being WPA-PSK).

With the command entered Aircrack makes light work of the data and provided me with the WEP encryption key within 10 seconds. With your encryption key in hand move over to Wireshark and open your captured data.

Wireshark can use your cracked key to decrypt the data and allow you to view and manipulate the data captured. Go to _Wireshark > Preferences_ and expand the &#8220;Protocols&#8221; section. Navigate to IEEE 802.11, tick Enable decryption then click &#8220;Edit&#8221; and add your WEP key to the list. As a result of doing this you&#8217;ll be able to see all of the data in the clear. As part of my task I was also asked to see if any sensitive data was being broadcast which I did by clicking on a TCP entry, right clicking and choosing _Follow > TCP Stream_.

## Conclusions

While it has been common knowledge for a number of years that WEP just doesn&#8217;t provide good enough security for a wireless network anymore, that I managed to obtain the encryption key from a sample stream with ten seconds serves to underline that point.

WPA2 is widely accepted as the bare minimum for securing a Wifi networks but, as should be the case, there are even stronger security types <a href="https://www.darkreading.com/endpoint/wi-fi-alliance-launches-wpa2-enhancements-and-debuts-wpa3/d/d-id/1330762" target="_blank" rel="noopener">currently in development</a> for WiFi so hopefully ensuring that Wireless networking remains an option for organisations.