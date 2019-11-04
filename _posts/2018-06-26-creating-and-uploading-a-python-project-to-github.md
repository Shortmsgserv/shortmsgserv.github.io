---
id: 323
title: Creating and uploading a Python project to Github
date: 2018-06-26T16:31:03+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=323
permalink: /creating-and-uploading-a-python-project-to-github/
image: /wp-content/uploads/2018/06/Caesar-Cipher.png
categories:
  - Programming
  - Python
tags:
  - Bsides
  - Caesar Cipher
  - Cipher
  - Code
  - Git
  - Github
  - Octoverse
  - Python
  - Repository
  - ROT13
---
<img class="aligncenter wp-image-327 size-medium" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/06/Caesar-Cipher.png?resize=300%2C225" alt="Caesar Cipher Header" width="300" height="225" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/06/Caesar-Cipher.png?resize=300%2C225 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/06/Caesar-Cipher.png?resize=768%2C576 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/06/Caesar-Cipher.png?w=800 800w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />

Having recently attended [BSides London 2018](https://www.securitybsides.org.uk) I&#8217;ve become more conscious of where my skills fall short and more determined to increase them. An area I&#8217;m particularly determined to improve is my programming skills.

One of the subjects I did at A-Level was computing where I we were tasked with creating a program in [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language)). Pascal was not widely used then and probably less so now (it does not appear within the fifteen most popular languages on Github&#8217;s yearly [Octoverse](https://octoverse.github.com) report). In my spare time had a play around with C# and a tiny amount of Visual Basic.

While I believe I have at least a basic understanding of the concepts of programming, in terms of practical use my skills are in need of some serious polishing, cue my [Caesar Cipher Python project](https://github.com/Shortmsgserv/Caesar-Cipher.git). If you&#8217;re unaware of a [Caesar Cipher](https://en.wikipedia.org/wiki/Caesar_cipher) it was allegedly used by Julius Caesar and is a substitution cipher that changes a letter of the alphabet for another letter a number of letters down the alphabet and is contemporarily used in the [ROT13](https://en.wikipedia.org/wiki/ROT13) cipher.

# The Project

To get started on the project I used the [Caesar Cipher walkthrough](https://codeclubprojects.org/en-GB/python/secret-messages/) on Code Club which gives you a basic guide to create a cipher that can easily transpose lowercase characters and not fail when letters are chosen as the input. After creating this basic project, I then added code to transpose upper case letters of the alphabet and also added the ability to change the number of places the letter is shifted (the key).

With my cipher created I then wanted to upload my project to my [Github](https://github.com/Shortmsgserv) using the command line as much as possible. After looking around the first step appeared to need to be done on the Github website.

<img class="aligncenter size-full wp-image-326" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/06/Create-a-github-repository.png?resize=640%2C567" alt="Create a github repository" width="640" height="567" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/06/Create-a-github-repository.png?w=900 900w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/06/Create-a-github-repository.png?resize=300%2C266 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/06/Create-a-github-repository.png?resize=768%2C680 768w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> 

With this done I switched back over to the command line. One thing I wish I&#8217;d done at the start of the process is edited my git config file in my home directory, so if you are looking to do this, make sure this is edited by typing

_$ nano ~/.gitconfig_

adding the name and email you use on Github.

Navigating to the directory with my project in using the _cd_ command, I then initialised it as a git repository with

_$ git init_

the [walkthrough](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/) I initially followed advised to not create the README or gitignore files to minimise issues as they could be added later, so didn&#8217;t create these. I was then directed to add the files to the local git repository (if you&#8217;re on a Mac all these files will be hidden as they have a . in front of the folder name. An easy way to show hidden files is with _command + shift + ._) so entered the command

_$ git add ._

and then committed the files with

_$ git commit -m &#8220;First commit&#8221;_

Next I specified the URL of my repository with

_$ git remote add origin https://github.com/Shortmsgserv/Caesar-Cipher_

and verified this was correct with

_$ git remote -v_

Followed by the final push of the files with the command of

_$ git push -u origin master_

Github will then asked for my your username and password. This seemed obvious enough, however there is a slight complication if you have Two Factor enabled. For this you&#8217;ll need to create a personal access token ([Github&#8217;s documentation](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/) walks you through this. When generating my token I only ticked the repo boxes and nothing else.) and use this as your password. With all the details entered my file was then visible on Github.

&nbsp;

&nbsp;