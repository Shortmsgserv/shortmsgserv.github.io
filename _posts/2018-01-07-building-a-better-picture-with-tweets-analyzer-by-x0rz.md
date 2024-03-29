---
id: 163
title: Building a Better Picture with Tweets Analyzer by x0rz
date: 2018-01-07T22:12:20+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=163
permalink: /building-a-better-picture-with-tweets-analyzer-by-x0rz/
image: /wp-content/uploads/2018/01/Twitter-Logo.png
categories:
  - Tools
  - Tweets Analyser
tags:
  - Tweets Analyzer
  - Twitter
  - x0rz
---
<img class="aligncenter wp-image-169 size-medium" src="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/01/Twitter-Logo.png?resize=300%2C225" alt="Twitter Logo" width="300" height="225" srcset="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/01/Twitter-Logo.png?resize=300%2C225 300w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/01/Twitter-Logo.png?w=640 640w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />

Most of the posts on social media can seem relatively mundane and unremarkable. From the tweets regarding what we first ate for breakfast, to our comment on the latest Netflix release, we may think that the information within our tweets is only our comment on a particular topic. In reality, the information behind these tweets can be far more revealing than we imagine.

A tool I’ve come across that can help discover the data behind the tweet is Tweets Analyzer by <a href="https://twitter.com/x0rz" target="_blank" rel="noopener">x0rz</a>. To download <a href="https://github.com/x0rz/tweets_analyzer" target="_blank" rel="noopener">Tweet Analyser</a> you’ll need to have [Python 3 installed on your computer](http://shortmsgserv.co.uk/the-endorser-by-eth0izzle/) (in my case I’m using macOS). Load the files from Git using the command

_$ git clone https://github.com/x0rz/tweets_analyzer_

Once these files are pulled down you can use pip to install the required files. After navigating to the Tweets Analyzer directory run the command

_$ pip3 install requirements.txt_

Also within the directory will be a “secrets.py” file. In order to run an app using the Twitter API you’ll need to get an API key from <a href="http://apps.twitter.com" target="_blank" rel="noopener">apps.twitter.com</a>. Once you have made a new app, you should receive a consumer key, consumer token, access token and an access token secret. These four items will need pasting into the “secrets.py” file in order for the programme to run successfully. You can either edit these in a text editor or use nano in terminal.

With your secrets file updated and the required extras installed you can run the program to analyse a Twitter profile with

$ python3 tweets_analyzer.py -n <twitter handle>

<img class="aligncenter size-large wp-image-166" src="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/01/govuk-twitter-profile.png?resize=640%2C823" alt="GOVUK Output Screenshot" width="640" height="823" srcset="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/01/govuk-twitter-profile.png?resize=796%2C1024 796w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/01/govuk-twitter-profile.png?resize=233%2C300 233w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/01/govuk-twitter-profile.png?resize=768%2C988 768w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/01/govuk-twitter-profile.png?w=1280 1280w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> 

Each section generated by the programme will be able to be used to find out a little more information about a subject. The first two sections are perhaps the most important for determining the behaviour of a person.

The time a person tweets can speak volumes about the person running an account. In the scan of <a href="https://twitter.com/GOVUK" target="_blank" rel="noopener">@GOVUK</a> above you can see how nearly all of the tweets are posted between nine o’clock and five o’clock. Not too long ago I once read about a group who scanned a set of Twitter accounts created by a government in order to shape the opinions of another countries citizens (Apologies, I have not been able to find the reference to this). One point the group found is that most tweets from these accounts were sent during the working hours for the country the accounts were from, suggesting that these tweets were perhaps a result of a working day, not just someone’s personal musings.

Among the other sections is a top 10 detected places (not present for @GOVUKs tweets) which outlines the top geotags attached to tweets. This information could be enough to glean a users physical location or any location they may frequently go to, such as their place of work.

These and the other sections present a massive opportunity to develop a clear picture of a users interests and behaviour and when combined with other sources can be enough to develop an extensive profile of a person, perhaps more than they would wish you to know.