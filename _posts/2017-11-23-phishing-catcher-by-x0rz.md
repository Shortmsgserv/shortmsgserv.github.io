---
id: 77
title: Phishing Catcher by x0rz
date: 2017-11-23T22:20:41+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=77
permalink: /phishing-catcher-by-x0rz/
categories:
  - Phishing
tags:
  - Phishing
  - Phishing Catcher
  - Tools
---
Recently I was shown a tool by a friend that I can honestly say left me in awe of its simplicity, yet how powerful it could be. Working in technical support for sometime means I have lost count of the number of people I have come across who have fallen for phishing scams. One method that phishing scams use now to make themselves appear more genuine than they are is to buy domain names that contain the name of the company they are using to target people.

Phishing Catcher by <a href="https://0day.rocks" target="_blank" rel="noopener">x0rz</a> allows you to see in realtime the certificates logged by <a href="https://certstream.calidog.io" target="_blank" rel="noopener">Certstream</a> and it’s astounding the sheer number created every minute that, at least upon initial glance, are less than genuine.

To get set up I <a href="https://github.com/x0rz/phishing_catcher" target="_blank" rel="noopener">downloaded</a> the zip file of Phishing Catcher from its Github repository and unpacked it in my Kali Linux VirtualBox. One its unpacked and moved to where you want it, you’ll likely need some extra Python packages installing. You’ll need to the packages required in the included “requirements.txt” file. For ease, while looking at the files in the Kali file manager, right click and choose &#8220;Open in Terminal&#8221; and in your terminal window you’ll need to run:

> pip install -r requirements.txt

Once thats completed, enter into terminal:

> ./catch_phishing.py

And watch as it updates with any domains Certstream has detected certificates created for.

<img class="alignnone size-large wp-image-93" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Kali_Web.jpg?resize=640%2C625" alt="Phishing Catcher in Kali" width="640" height="625" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Kali_Web.jpg?resize=1024%2C1000 1024w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Kali_Web.jpg?resize=300%2C293 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Kali_Web.jpg?resize=768%2C750 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Kali_Web.jpg?w=1280 1280w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Kali_Web.jpg?w=1920 1920w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> 

While I find this interesting the sheer volume of domains that will be created can be overwhelming, so it can be good to filter this down to specific keywords that you’re interested in. Luckily when phishing catcher is first run it will create a file called “suspicious_domains.log” which can be used to filter domains down to your preferred keyword.

When I was shown this it was with a second terminal window open showing the preferred domains simultaneously which is the way I’ll explain now. You’ll need to open a second terminal window (with terminal focused on the Phishing Catcher directory). Within the second terminal window enter:

> tail -f suspicious_domains.log | grep -E ‘_keyword_’

If you desire more than one keyword you can include a vertical bar between the keywords (In my example I entered ‘amazon|google|paypal|twitter|instagram|apple’). The second terminal window will only show the domain certificates generated that contain your chosen keywords.

<img class="size-large wp-image-81 alignnone" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Web.jpg?resize=640%2C477" alt="Phishing Catcher Screenshot" width="640" height="477" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Web.jpg?resize=1024%2C763 1024w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Web.jpg?resize=300%2C223 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Web.jpg?resize=768%2C572 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Web.jpg?w=1280 1280w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2017/11/Phishing_Catcher_Web.jpg?w=1920 1920w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> 

What will not be shown in our tail window but is on the main window is the scores given to the domain by the tool which is based on multiple measures of how suspicious the tool thinks the link is. Luckily we can easily find out how what the measures are and how it calculates them.

To have a look at how the score is decided, navigate to where the “catch_phishing.py” file is located, right click on it and then open the file in a text editor. As you browse through the file you’ll be able to see what characteristic of a URL adds to the score. Something as simple as too many hyphens in a URL or a certificate issued from a free authority will add to the score. The <a href="https://en.wikipedia.org/wiki/Levenshtein_distance" target="_blank" rel="noopener">Levenshtein algorithm</a> is also used to detect the unfortunately common practice of making a domain few letters away from the genuine one. It uses a bank of keywords (listed in “suspicious.py” in the same directory) that are unlikely to be used by anyone else such as netflix which would add a whopping 70 points to a score.

After viewing what Phishing Catcher could do I questioned why more companies haven’t integrated this or something like this more liberally in their systems to prevent more phishing attacks for their customers or employees. For example, an organisation could implement a flag on their email system that any email received with their name in the certificate or above a certain score would be flagged with suspicion. The downside is what if the certificate just happens to look suspicious but is actually genuine e.g. perfectly-legitimate-apple-juice.com, sometimes such a harsh tool can create issues as the people you’re trying to protect may look for ways to circumvent the protection.