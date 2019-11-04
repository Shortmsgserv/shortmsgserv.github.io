---
id: 391
title: Getting Started with Splunk
date: 2018-10-27T21:12:30+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=391
permalink: /getting-started-with-splunk/
image: /wp-content/uploads/2018/10/Splunk-Blog-Header.png
categories:
  - Tools
tags:
  - Data
  - Data analysis
  - Splunk
  - Tools
---
<img class="aligncenter wp-image-405 size-medium" src="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Blog-Header.png?resize=300%2C225" alt="Splunk Blog Post Header Image" width="300" height="225" srcset="https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Blog-Header.png?resize=300%2C225 300w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Blog-Header.png?resize=768%2C576 768w, https://i1.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Blog-Header.png?w=800 800w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />

With the growth of technology into every aspect of our lives, the amount of data being reported back has grown with it. The sheer volume of data means that manually sifting through the data is impossible within a reasonable time frame. [Splunk](https://www.splunk.com) is software whose aim is to sort through this data and highlight any interesting trends or patterns within the data. There are a number of different versions of Splunk available tailored to the type of data you&#8217;re looking to analyse and it can be expanded with plug-ins posted on [Splunkbase](https://splunkbase.splunk.com). Luckily a free version is offered by Splunk, allowing you to download and learn Splunk without paying the [significant] fee for one of the Splunk variants.

# Downloading, Installing, and Launching

Splunk is available for all major operating systems; Linux, Windows, and macOS; but I&#8217;ll focus on macOS. To [download](https://www.splunk.com/en_us/download.html) Splunk you&#8217;ll need to sign-up for an account on the Splunk website, once complete you&#8217;ll have the choice of downloading and [installing](http://docs.splunk.com/Documentation/Splunk/7.2.0/SearchTutorial/InstallSplunk) your preferred platform.

I chose to install Splunk from the command line on macOS by downloading the tar file and ran this command to install into the applications directory:

_$ tar xvzf splunk-version.tgz -C/Applications_

With Splunk installed you&#8217;ll then need to start the Splunk process. If you install Splunk to the applications directory as I did then you&#8217;ll need to start the Splunk process by running:

_$ /Applications⁩/splunk/bin⁩/splunk start_

During the startup process you&#8217;ll be asked to assign the installation an admin password of your choice. For ease you can add an alias to the .bash\_profile file within your home directory that will allow you to start and stop the process with a simple &#8216;splunk&#8217; command. Use nano to open your .bash\_profile

_$ nano ~/.bash_profile_

and add the line

_alias splunk=&#8217;/Applications/splunk/bin/splunk&#8217;_

With everything installed and started navigate to 127.0.0.1:8000 in your browser and you&#8217;ll be able to login with the user name password and the admin password entered during startup.

# Importing Data

<img class="aligncenter size-medium wp-image-400" src="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Home.png?resize=300%2C187" alt="A picture of the initial Splunk Home dashboard" width="300" height="187" srcset="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Home.png?resize=300%2C187 300w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Home.png?resize=768%2C478 768w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Home.png?resize=1024%2C638 1024w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Home.png?w=1280 1280w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Home.png?w=1920 1920w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" /> 

With Splunk set up, you can now import data into it to be analysed. Splunk [provide](http://docs.splunk.com/Documentation/Splunk/7.1.2/SearchTutorial/Systemrequirements) sample data on their site to be imported (the instructions on uploading the data on the Splunk site [explain](http://docs.splunk.com/Documentation/Splunk/7.2.0/SearchTutorial/AboutgettingdataintoSplunk) it concisely).

# Searching the Data

By default Splunk will have the Search & Reporting app installed that will allow you to get started in finding something useful in the data. Clicking on the data summary button on the right-hand side you will be presented with three headings; Hosts, Sources, and Sourcetypes. A Host is the host name, IP address or fully qualified domain name of the machine from where the event originated. The Source is the path, port, or script where the event originated. Finally the Sourcetype is what type of data it is.

I&#8217;d recommend going try a few of the entires within each heading and finding out what is produced and remember that after clicking on them if you aren&#8217;t shown any data, you&#8217;ll likely need to expand the timeframe in the top right from &#8220;Last 24 hours&#8221; to a greater period; I chose all time for ease as it does not make my Mac struggle and there isn&#8217;t a massive amount of data.

An example of what can be found just in the this search view is when choosing the &#8220;access\_combined\_wcookie&#8221; Sourcetype. Once this is selected you&#8217;ll be able to see all the fields this data contains. Two of the fields that provide some form of interesting data are the &#8220;action&#8221; and &#8220;useragent&#8221; field. These two fields are the most interesting as &#8220;action&#8221; would allow you to see some of the most common user behaviours while on a website, while useragent would allow you to prioritise development for certain browsers, or for desktop or mobile.

Returning back to the front page of the Search & Reporting app allows you to query the data. For example I used the query &#8220;categoryid=accessories&#8221; &#8220;action=addtocart&#8221; to find events where the addtocart action was triggered while in the accessories section.

Next we&#8217;ll create a chart using the data, but before this can be done we&#8217;ll need to import a Lookup file. A lookup file allows you to pair the anonymous looking product ID data with a more descriptive product name and description, along with other data. The Splunk [tutorial](https://docs.splunk.com/Documentation/Splunk/7.2.0/SearchTutorial/Usefieldlookups) explains how to do this clearly and in detail.

# Creating a chart

To create a chart with the Search & Reporting tool a query needs to be entered in the search field. In the case of this data I used the example query [listed](http://docs.splunk.com/Documentation/Splunk/7.2.0/SearchTutorial/Basicchart) within the Splunk tutorial as this is a query with at least a basic level of complexity, but with a time frame of all time as otherwise nothing was shown for me.

_sourcetype=access_* status=200 | chart count AS views count(eval(action=&#8221;addtocart&#8221;)) AS addtocart count(eval(action=&#8221;purchase&#8221;)) AS purchases by productName | rename productName AS &#8220;Product Name&#8221;, views AS &#8220;Views&#8221;, addtocart AS &#8220;Adds to Cart&#8221;, purchases AS &#8220;Purchases&#8221;_

Switch to the statistics tab to more easily see that this command counts the number of &#8220;addtocart&#8221; and &#8220;purchase&#8221; instances in the data that each product has, then also displays them with the number of views. Moving to the Visualization tab allows you to present this data in a more visual form; I chose the column chart format but try different charts if you think it may be presented in a better form. Splunk also has more in-depth data visualisation [options](https://docs.splunk.com/Documentation/Splunk/7.2.0/SearchTutorial/Chartoverlays), but I won&#8217;t go into them at this time.

# Create a Dashboard

You can create dashboards within Splunk so that you have quick, visual access to data as fast as possible. For this I&#8217;ve again used the example query on the Splunk website, but with the time frame set as all time:

_sourcetype=access_* status=200 action=purchase | top categoryId_

With the query run move over to the Visualization tab and change the data so it&#8217;s shown as a pie chart and click Save As in the top right and choose &#8220;Dashboard&#8221;. You can fill in the fields as you choose, but I&#8217;ve included a screenshot of how I filled out the data. With this saved you have the option of returning to your Splunk homepage and adding this freshly saved Dashboard so its viewable straightaway after logging into Splunk.

<img class="aligncenter size-medium wp-image-403" src="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Dashboard-Fields.png?resize=300%2C251" alt="A screenshot of the Splunk Save As Dashboard Dialogue" width="300" height="251" srcset="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Dashboard-Fields.png?resize=300%2C251 300w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Dashboard-Fields.png?resize=768%2C642 768w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Dashboard-Fields.png?resize=1024%2C856 1024w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Dashboard-Fields.png?w=1280 1280w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/10/Splunk-Dashboard-Fields.png?w=1920 1920w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" /> 

My blogpost only goes over what Splunk can do at an incredibly basic level, what&#8217;s possible with Splunk is far greater than what I&#8217;ve outlined here and it is used everyday by a large [number](https://www.splunk.com/en_us/customers.html) of companies to analyse the massive volumes of data they collect. For someone in a network security role, being able to sort through the large amount of log data collected in order to find what could be a significant threat to an organisation, tools such as Splunk are an excellent way of being able to respond to potential threats faster as reducing the chance of a benign event being blown up into something significant.

&nbsp;