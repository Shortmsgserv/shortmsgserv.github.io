---
id: 145
title: The Endorser by eth0izzle
date: 2017-12-14T17:20:56+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=145
permalink: /the-endorser-by-eth0izzle/
image: /wp-content/uploads/2017/12/example.png
categories:
  - Tools
tags:
  - ChromeDriver
  - eth0izzle
  - Google Chrome
  - Homebrew
  - LinkedIn
  - OSINT
  - Python
  - The Endorser
  - Tools
  - Xcode
---
<img class="aligncenter wp-image-154 size-large" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/12/example.png?resize=640%2C324" alt="Example of The Endorser Output" width="640" height="324" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/12/example.png?resize=1024%2C519 1024w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/12/example.png?resize=300%2C152 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/12/example.png?resize=768%2C389 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/12/example.png?w=1280 1280w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" />

A common trope is that there are only <a href="https://en.wikipedia.org/wiki/Six_degrees_of_separation" target="_blank" rel="noopener">six degrees of separation</a> between all people on the planet. While this may or may not be true; <a href="https://github.com/eth0izzle/the-endorser" target="_blank" rel="noopener">the endorser by eth0izzle</a> is an Open-Source intelligence tool that can help you use the connections between people to find ever more promising potential targets.

The endorser uses <a href="https://www.linkedin.com" target="_blank" rel="noopener">LinkedIn</a> skill endorsements to find the important connections between employees. It works on the principle that people who are closely linked within an organisation are more likely to have more numerous skill endorsements than a person who is external.

For my work I use a Mac, so my guide will include all the steps I took to get the endorser working. Unfortunately macOS adds a few more steps than an up-to-date Linux install may require.

If you haven’t installed Xcode or its command line tools, now will be a great time to do this as <a href="https://brew.sh" target="_blank" rel="noopener">Homebrew</a> (which I’ve <a href="http://shortmsgserv.co.uk/setting-up/" target="_blank" rel="noopener">mentioned in other blog posts</a>) will require the them to complete the installation of Python. I always install the entirety of Xcode from the Mac App Store as every now and then I use some of its other tools for tinkering, but most third party tools only require the command line tools, such as code compilation. The command line tools can installed by typing _$ xcode-select &#8211;install_ in a terminal window.

A standard installation of macOS ships with Python 2 (As I write this the latest version of macOS, which I have installed, is High Sierra 10.13.2) the endorser will require a minimum of Python 3.0 to be installed for it to work, so you’ll need to update your Python installation. With Homebrew this will be easy, just type _$ brew install python3_ and it will grab the latest version of Python.

<img class="aligncenter size-large wp-image-152" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/12/Clone-the-endorser-git.png?resize=640%2C352" alt="Cloning the endorser from git" width="640" height="352" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/12/Clone-the-endorser-git.png?resize=1024%2C563 1024w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/12/Clone-the-endorser-git.png?resize=300%2C165 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/12/Clone-the-endorser-git.png?resize=768%2C422 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/12/Clone-the-endorser-git.png?w=1434 1434w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/12/Clone-the-endorser-git.png?w=1280 1280w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> 

Once you&#8217;ve then got the files needed for the endorser from Git using the command _$ git clone https://github.com/eth0izzle/the-endorser.git_, within the files downloaded as part of the endorser there should be one called requirements.txt. This contains a list of (some of the) extras needed to run the endorser. Navigate to the main endorser directory; for me this command is _$ cd ./the-endorser_. Once terminal has the endorser folder as the active directory, you can install the dependancies within the requirements file. Previously I used pip within Kali where the command would be _$ pip install requirements_; however, within macOS you’ll need to use _$_ **_pip3_** _install requirements_. If you don’t use the 3, the command may fail. We’re not quite done with grabbing extras yet as you’ll still need to grab <a href="https://sites.google.com/a/chromium.org/chromedriver/" target="_blank" rel="noopener">ChromeDriver</a> and if you don’t have it installed already, <a href="https://www.google.com/chrome/index.html" target="_blank" rel="noopener">Google Chrome</a>.

With everything finally loaded, all thats left to do is to add your LinkedIn credentials into the ‘config.yaml’ file; you can either use nano within terminal ($ _nano config.yaml_) or any text editor will do. Credentials entered, run the endorser using _python3 the-endorser.py_ and add the two URLs you wish to compare the number of endorsements for e.g.

$ Python3 the-endorser https://www.linkedin.com/in/FirstUser https://www.linkedin.com/in/SecondUser

It may take a number of minutes to finally produce but the output should automatically open, if it doesn’t it should be stored within the main level of the endorser folder. From this file you should be able to see the skills person one has on their profile, along with the skills person two has on their profile that are shared with contacts in both their networks.

Confusingly to me, the arrows are pointing at your selected users contacts, but the links actually signify that the contact has endorsed your chosen user for that skill. This then means that any contacts with a high number of shared links are likely to be closely linked in reality to your two chosen users, allowing you to focus any further investigation on that shared contact.

This will be enormously useful if you don’t have any prior knowledge of an organisations structure as the endorser allows you to quickly gather information on who may work for an organisation and at what level they likely work at.