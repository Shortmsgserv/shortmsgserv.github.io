---
id: 215
title: Is Nowhere Safe from Cryptomining?
date: 2018-02-12T20:55:35+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=215
permalink: /is-nowhere-safe-from-cryptomining/
image: /wp-content/uploads/2018/02/Monero-Featured-Image.png
categories:
  - Scripts
tags:
  - Crypto
  - Cryptocurrency
  - Cryptomining
  - mining
  - Scott Helme
  - Subresource Integrity
---
<img class="aligncenter size-medium wp-image-223" src="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/02/Monero-Featured-Image.png?resize=300%2C225" alt="Monero Logo" width="300" height="225" srcset="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/02/Monero-Featured-Image.png?resize=300%2C225 300w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/02/Monero-Featured-Image.png?w=640 640w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />

Not a week goes by without something else being infected with some form of crypto-currency mining software recently; in December one of Starbucks&#8217; Buenos Aires locations was <a href="http://www.bbc.co.uk/news/technology-42338754" target="_blank" rel="noopener">identified</a> as hijacking customer computers to mine Monero when they connected to in-store WiFi; and YouTube recently <a href="http://www.telegraph.co.uk/technology/2018/01/29/youtube-shuts-hidden-crypto-jacking-adverts/" target="_blank" rel="noopener">remedied</a> a vulnerability that would allow crypto mining scripts to be placed in ads it served. Yesterday it was found that a large number of government websites were found to have been hijacked to serve the Monero mining script, Coinhive.

The exploit was initially <a href="https://twitter.com/Scott_Helme/status/962684239975272450" target="_blank" rel="noopener">spotted</a> by security consultant Scott Helme who first noticed the script running on the <a href="https://ico.org.uk" target="_blank" rel="noopener">ICO website</a>. It wasn&#8217;t long before it was noticed that this script was not only running on the ICO&#8217;s website, but many other government websites including the Queensland Government website, several NHS websites, and the US Courts website.

Within a short space of time it was found that the source of the vulnerability was a plug-in by Texthelp called <a href="https://www.texthelp.com/en-gb/products/browsealoud/" target="_blank" rel="noopener">BrowseAloud</a> which assists with the accessibility of websites. It was found that this plug-in had somehow allowed another party to discreetly inject their Coinhive script into this plug-in, this meant that any of the websites who implemented BrowseAloud would find their users would trigger the script when they visited one of the affected websites.

This episodes really exemplifies why anyone creating software also needs to consider the security of any third party involved. It was likely noticed by the person who implemented this script that by exploiting BrowseAloud, they could multiply the effect of their vulnerability to what could be thousands of websites; and with the potential of crypto-currencies to rise again in price, the hacker could be looking at a significant return on their investment.

Currently we don&#8217;t know how the attacker managed to inject their code into the BrowseAloud plug-in, but the recommendation by Scott Helme was to implement <a href="https://scotthelme.co.uk/subresource-integrity/" target="_blank" rel="noopener">Subresource Integrity</a> which compares the hash of an object loaded to what the website was expecting, which would have mitigated the effect of the loophole this script was taking advantage of (a longer explanation is available on the <a href="https://www.w3.org/TR/SRI/" target="_blank" rel="noopener">W3C website</a>). While this script was relatively harmless in terms of affect on a user (no loss of data, simply a loss of processing power while that website was open) the potential for this loophole to be exploited for more nefarious purposes is clear and so it is paramount that third party involvement will need to be kept in mind when designing software.