---
id: 231
title: The Problem with Updates
date: 2018-03-04T21:30:32+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=231
permalink: /the-problem-with-updates/
image: /wp-content/uploads/2018/03/Software-Updates.png
categories:
  - Software
tags:
  - Chrome OS
  - Flash
  - iOS
  - macOS
  - Snake
  - Software Updates
  - WannaCry
---
<img class="aligncenter size-medium wp-image-232" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Software-Updates.png?resize=300%2C225" alt="Software Update Header Image" width="300" height="225" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Software-Updates.png?resize=300%2C225 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Software-Updates.png?w=640 640w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />

I&#8217;ve come across a number of people recently who have installed a piece of malicious software <a href="https://blog.malwarebytes.com/threat-analysis/2017/05/snake-malware-ported-windows-mac/" target="_blank" rel="noopener">called Snake</a> that disguises itself as an Adobe Flash installer. This isn&#8217;t the first piece of trojan software that has affected the Mac and from memory can remember malicious software being packaged with Apple&#8217;s <a href="https://www.macworld.com/article/1138380/iworktrojan.html" target="_blank" rel="noopener">iWork</a> and <a href="https://www.macrumors.com/2015/09/20/xcodeghost-chinese-malware-faq/" target="_blank" rel="noopener">Xcode</a> software previously.

What I did notice was that in each of these cases the users affected were running substantially outdated versions of their software; macOS 10.10 or lower. As part of the functionality of Gatekeeper in macOS there is a feature called XProtect which keeps a record of known signatures for malware to prevent its installation. From <a href="https://eclecticlight.co/2018/01/17/apple-has-pushed-updates-to-xprotect-and-mrt-security-data/" target="_blank" rel="noopener">what I can tell</a> the updates to this signature recognition only stretch back to macOS 10.11 El Capitan (at that point called OS X 10.11 El Capitan).

It&#8217;s arguable that if these users had kept their software up-to-date, they would not have been affected by this trojan, but what this does expose is how most users are not conscious about keeping their systems updated. Most users are only using their computers as a tool and if they had to add remaining aware of the latest software updates and how it will affect them to their list of things to remember, they would be left with little time of their own.

Automatic updates do remedy this situation somewhat, but they can introduce other issues. Most are opt-in and users may skip past the message asking them to turn it on (I have lost count of the amount of times where I&#8217;ve quickly tapped &#8220;Okay&#8221; on a message and afterwards wondered what the message said). If the updates are installed automatically, what impact will it have on the software currently installed. Major operating system updates can sometimes break frequently used software or hardware, breaking trust in automatic updating.

# Wannacry

The impact of not remaining updated can be huge and was most clearly demonstrated with the recent <a href="https://en.wikipedia.org/wiki/WannaCry_ransomware_attack" target="_blank" rel="noopener">Wannacry</a> attack. When the standard support period ended for Windows XP, the UK government <a href="https://www.theguardian.com/technology/2014/apr/07/uk-government-microsoft-windows-xp-public-sector" target="_blank" rel="noopener">paid Microsoft</a> around £5.5 million to continue to provide updates for a further twelve months. It was felt that this would give government departments enough time to plan and migrate to newer, supported operating systems. In 2015 shortly before the agreement ended, the assessment was that a large number of departments still had yet to migrate their systems. It was felt that the agreement had simply given the departments a feeling of complacency; if the software was still being updated, why upgrade. The government <a href="http://uk.businessinsider.com/why-the-uk-government-stopped-paying-for-windows-xp-2017-5" target="_blank" rel="noopener">decided</a> that the only way to ensure departments upgraded was to sign no further agreements. If departments knew it would not be updated, they would upgrade.

This game of bluff did not end well. When Wannacry was released into the wild, one prominent government department affected was the <a href="https://www.telegraph.co.uk/news/2017/05/13/nhs-cyber-attack-everything-need-know-biggest-ransomware-offensive/" target="_blank" rel="noopener">NHS</a>. A number of different areas were affected with NHS data encrypted and unaccessible, people resorted to pen and paper and patients were subject to significant delays in care.

# Encouraging Updates

Wannacry represents an extreme in what can happen when updates aren&#8217;t applied to a system, but the challenge remains how do software developers encourage users to keep their software current. Forced updates can cause incompatibility, but no updates can result in data loss. One system that has increased the number of users updating is Google&#8217;s Chrome OS. In simple terms Chrome OS mainly exists as a web browser so has removed a large amount of complexity, allowing operating system updates to be completed frequently and without user interaction. Most operating systems have more complexity however and may not be practicable to take such a cavalier attitude to updates.

An operating system that I think does have a good result in encouraging users to update is iOS with 25% of users installing the latest version, iOS 11, one week after release. I think one reason Apple have such success with their updates is that generally with each major release they offer a large number of new, compelling features to users and with their minor release a factor that encourages upgrading is usually when they include additional emoji. Whatever the method developers need to ensure that they encourage updating by making the process as simple as possible, regardless of what encouragement they offer.

&nbsp;