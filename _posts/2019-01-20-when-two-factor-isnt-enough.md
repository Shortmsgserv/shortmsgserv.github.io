---
id: 426
title: 'When two-factor isn&#8217;t enough.'
date: 2019-01-20T13:45:06+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=426
permalink: /when-two-factor-isnt-enough/
image: /wp-content/uploads/2019/01/Reverse-Proxy-Phishing-Header.png
categories:
  - Exploits
  - News
  - Phishing
  - Tools
tags:
  - evilginx
  - evilginx2
  - Modlishka
  - Passwords
  - Phishing
  - Reverse proxy
  - Tools
  - Two-factor
---
There has been a massive push to encourage users to enable two-factor authentication on their accounts. From <a rel="noreferrer noopener" aria-label=" (opens in a new tab)" href="https://kotaku.com/fortnite-now-gives-you-a-reward-if-you-turn-on-two-fact-1828553198" target="_blank">in-game rewards</a> to [membership discounts](https://www.theverge.com/2013/3/27/4152602/mailchimp-rewarding-users-ten-percent-off-two-step-security) two-factor has been strongly encouraged by a number of companies to provide greater security to users, but could this lull users into a false sense of security?

As two-factor usage has grown more of its shortcomings have been pointed out; from the ability of <a rel="noreferrer noopener" aria-label="SMS-based codes (opens in a new tab)" href="https://www.kaspersky.co.uk/blog/2fa-practical-guide/14589/" target="_blank">SMS-based codes</a> to be intercepted, to the ability to <a rel="noreferrer noopener" aria-label="brute force (opens in a new tab)" href="https://blog.malwarebytes.com/101/2018/09/two-factor-authentication-2fa-secure-seems/" target="_blank">brute force</a> the codes. An extremely sophisticated method that has grown in use is to use a reverse proxy while phishing. 

A recent <a rel="noreferrer noopener" aria-label="report  (opens in a new tab)" href="https://www.amnesty.org/en/latest/research/2018/12/when-best-practice-is-not-good-enough/" target="_blank">report </a>by Amnesty International outlined an increase in the sophistication of phishing attacks targeting people around the world, particularly people based in states in the Middle East. Amnesty noted that the attacks frequently involved &#8220;secure email&#8221; providers such as Tutanota and ProtonMail, but did also involve well-used email providers such as Yahoo! and Google.

The method these attacks used in order to more effectively clone the providers website was a method called a <a rel="noreferrer noopener" aria-label="reverse proxy (opens in a new tab)" href="https://en.wikipedia.org/wiki/Reverse_proxy" target="_blank">reverse proxy</a>. A reverse proxy server sits between the client and the server the client wishes to access. The reverse proxy has the ability to then manipulate and feed the data to the client. One of the defining features of a reverse proxy is that the client doesn&#8217;t have to know it&#8217;s part of a proxy network, whereas with the more common forward proxy the client is aware of being part of a proxy network.

Phishing reverse proxies pull the data from the website it wants to masquerade as (Google, Yahoo!, ProtonMail e.t.c) and presents it to the users. Using a reverse proxy the site it presents to the user can look indiscernible from the real website. A lot of these attacks have also used a domain name so close to the real thing that a user could easily be fooled by an attack (Amnesty gives one example of proton**e**mail.ch in comparison to protonmail.ch). As the attacks are also able to pull the sites almost identically, they can also show the two-factor authentication pages for a site, intercept the two factor code, and gain access using this code if they are quick enough.

## Tools Available

Two tools to setup your own phishing reverse proxy server are <a rel="noreferrer noopener" aria-label="Modlishka  (opens in a new tab)" href="https://github.com/drk1wi/Modlishka" target="_blank">Modlishka </a>and <a rel="noreferrer noopener" aria-label="evilginx2 (opens in a new tab)" href="https://github.com/kgretzky/evilginx2" target="_blank">evilginx2</a>. Both of these tools are intended as a demonstration rather than to setup your own phishing operation, only use it with permission from the parties to be phished. I had intended to do a full write of my experiences with Modlishka, but despite installing it on both macOS and Kali I&#8217;ve only managed to capture the password and not the username and session ID. If I get it working fully I&#8217;ll likely do a write-up later.<figure class="wp-block-image">

<img src="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2019/01/Modlishka-on-Kali.png?w=640&#038;ssl=1" alt="Screenshot of Modlishka running on Kali Linux" class="wp-image-455" srcset="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2019/01/Modlishka-on-Kali.png?w=1000 1000w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2019/01/Modlishka-on-Kali.png?resize=300%2C251 300w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2019/01/Modlishka-on-Kali.png?resize=768%2C644 768w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> </figure> 

## Is Two-Factor Pointless?

Upon first reading it can look as though perhaps it was wrong to place so much stock in two-factor authentication, but the reality is, as usual, more nuanced than simply that two-factor needs to be replaced. For example some of the conclusions on the <a rel="noreferrer noopener" aria-label="accompanying blog post (opens in a new tab)" href="https://blog.duszynski.eu/phishing-ng-bypassing-2fa-with-modlishka/" target="_blank">accompanying blog post</a> for Modlishka are that for the best security a <a rel="noreferrer noopener" aria-label="U2F  (opens in a new tab)" href="https://en.wikipedia.org/wiki/Universal_2nd_Factor" target="_blank">U2F </a>hardware token should be used and that password managers should be used as they will verify the domain the login information is being entered into. A password manager is definitely a good tool to use as when attempting to use Modlishka on my own machine it wouldn&#8217;t show my phishing account as available to enter on my fake Google login page. Hardware tokens are an invaluable step for highly sensitive systems, but for the average user they are probably an extreme step; accessing sensitive systems should use a hardware token as a requirement, but do you need one to access your H&M account?

The last conclusion that the blog post comes to is that user awareness should constantly be raised and this I think is why the answer to the question of is two-factor pointless is no. Two-factor is now available on nearly every major website I use yet the only system in common use that I&#8217;ve seen a high number of users use two-factor is their Apple ID (I think a massive factor in its high take-up is that Apple has pushed it in the setup process of iOS and within OS updates). The <a rel="noreferrer noopener" aria-label="top 25 passwords of 2018 (opens in a new tab)" href="https://gizmodo.com/the-25-most-popular-passwords-of-2018-will-make-you-fee-1831052705" target="_blank">top 25 passwords of 2018</a> are worryingly insecure and this list will likely stay unchanged at the end of 2019. If most users haven&#8217;t yet updated their passwords to something more secure let alone enabled two-factor, they are already operating with a level of security nowhere near two-factor. 

My personal conclusion is that awareness, as ever, should be continued to be increased (I haven&#8217;t attended school for some years, but would hope most curriculums include staying secure online), but perhaps companies should perhaps be more forceful in at least ensuring users have a secure password. My personal opinion is that we&#8217;re still so far away from the broad adoption of two-factor that the people there may be an excessive knee jerk reaction that two-factor is insecure. We know there are <a rel="noreferrer noopener" aria-label="faults  (opens in a new tab)" href="https://www.theverge.com/2017/9/18/16328172/sms-two-factor-authentication-hack-password-bitcoin" target="_blank">faults </a>with two-factor and that any faults should be resolved or mitigated against, but my personal experience is that there are a still a lot of users who haven&#8217;t protected themselves against simpler attacks than this. An example of this is in a Jimmy Kimmel <a rel="noreferrer noopener" aria-label="video  (opens in a new tab)" href="https://www.youtube.com/watch?v=opRMrEfAIiI" target="_blank">video </a>where people are tricked into saying their password on camera, and I&#8217;ve lost count of the number of people that carry their passwords around with them in a book.