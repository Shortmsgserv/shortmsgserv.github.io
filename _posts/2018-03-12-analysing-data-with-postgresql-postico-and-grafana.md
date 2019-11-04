---
id: 237
title: Analysing Data with PostgreSQL, Postico and Grafana
date: 2018-03-12T21:37:01+00:00
author: shortmsgserv
layout: post
guid: http://shortmsgserv.co.uk/?p=237
permalink: /analysing-data-with-postgresql-postico-and-grafana/
image: /wp-content/uploads/2018/03/Postico-Postgres-Grafana-Header.png
categories:
  - Data Analysis
tags:
  - csv
  - Homebrew
  - Postgres
  - PostgreSQL
  - Postico
  - Script
  - Scripting
  - SQL
  - SQL Query
  - Terminal
  - Visual Studio Code
  - VS Code
---
<img src="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Postico-Postgres-Grafana-Header.png?resize=300%2C225" class="size-medium wp-image-244" width="300" height="225" alt="Analysing Data with PostgreSQL and Grafana Header Image" srcset="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Postico-Postgres-Grafana-Header.png?resize=300%2C225 300w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Postico-Postgres-Grafana-Header.png?resize=768%2C576 768w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Postico-Postgres-Grafana-Header.png?w=1024 1024w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />

A large number of threats can affect an organisation and good practice is to keep a record of the threat and its characteristics. This can result in a huge amount of information; processing and analysing this information can be time consuming. One method to make the analysis of a high volume of data easier is by using a SQL database. A SQL database allows you to query large datasets so you can extract meaningful information far more easily than using other methods, such as spreadsheets.

For this example I&#8217;ve used <a href="https://www.postgresql.org" target="_blank" rel="noopener">PostgreSQL</a>, <a href="https://eggerapps.at/postico/" target="_blank" rel="noopener">Postico</a> and <a href="https://grafana.com" target="_blank" rel="noopener">Grafana</a>. PostgreSQL (sometimes just Postgres) is our main database management system while Postico sits on top as a slightly more user friendly client. Grafana is a visual dashboard that will allow us to present the results of our queries in an attractive way, allowing even non-technical people to utilise it.

I&#8217;ve used macOS so the instructions will be focused around that, but after installation most of the instructions are platform agnostic so will broadly be applicable to most operating systems. Both Postgres and Grafana can be installed using <a href="https://brew.sh" target="_blank" rel="noopener">Homebrew</a> via Terminal so fire up a terminal window and type

_$ brew install grafana_

and

_$ brew install postgresql_

to install both packages to your machine. Postico is available directly from the developers website which should be linked above and follows the standard method of being dragged to the applications folder.

You will also need your dataset which you might have already, if not there will be data all over the internet you could use for the exercise. One massive source of CSV file data is the website of the <a href="https://www.ons.gov.uk" target="_blank" rel="noopener">Office for National Statistics</a>. However, for the exercise try to have data with a column that would be set to a time formatting.

An optional download for the exercise is also Microsoft&#8217;s <a href="https://code.visualstudio.com" target="_blank" rel="noopener">Visual Studio Code</a>. Everything in this exercise could be done with a standard text editor, but VS Code does have a few helpful shortcuts along with support for a massive number of languages, including SQL.

# Getting Started

With everything downloaded and installed, we&#8217;ll need to set it all up. In your application folder you will have a Postgres app, click on this and you&#8217;ll be shown a very minimal window with an &#8220;Initialize&#8221; button located on the right. Click this button and it will create the SQL server on your Mac at the default locations which you may alter in future if you use Postgres more frequently; but we won&#8217;t during this exercise. With Postgres&#8217; setup complete open Postico to make sure it works correctly, but this should open your database with little complaint.

Grafana setup is a little less obvious. First start the process using Terminal by typing

_$ brew services start grafana_

This may take a few minutes.

With the Grafana process started open your web browser of choice and type localhost:3000. This should load the Grafana login screen; the details of which are stored within its configuration files and can be changed to your choice of username and password. For the exercise we&#8217;ll keep them as the default of username: admin and password: admin. Once you&#8217;ve logged in we&#8217;ll need to add Postgres as a data source so click on the big cog/gear to the left of the screen and navigate to the data source tab.

Click &#8220;+ Add a data source&#8221; and change the &#8220;Type&#8221; to PostgreSQL; eliminating a number of options. The name isn&#8217;t important so call it whatever is relevant to you. Host will need to be &#8220;localhost:&#8221; and whatever port your database is set to communicate on; I never changed this so for me it was 5432 but if that port number isn&#8217;t working navigate to the Postgres app and click on &#8220;Server Settings&#8230;&#8221; and you should see your Postgres port number. Your database name will also have to match where you will put your data and what the name is in Postgres; if you have followed the steps so far this will likely be your user shortname. Last of all change &#8220;SSL Mode&#8221; to disable and hit save and test which should result in a success message.<figure id="attachment_239" aria-describedby="caption-attachment-239" style="width: 640px" class="wp-caption aligncenter">

<img src="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Grafana-Postgres-Data-Source-Settings.png?resize=640%2C478" class="size-large wp-image-239" width="640" height="478" alt="Screenshot of the PostgreSQL Data Source settings on my Mac" srcset="https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Grafana-Postgres-Data-Source-Settings.png?resize=1024%2C765 1024w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Grafana-Postgres-Data-Source-Settings.png?resize=300%2C224 300w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Grafana-Postgres-Data-Source-Settings.png?resize=768%2C574 768w, https://i0.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/Grafana-Postgres-Data-Source-Settings.png?w=1304 1304w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> <figcaption id="caption-attachment-239" class="wp-caption-text">Screenshot of the PostgreSQL Data Source settings on my Mac</figcaption></figure> 

# Creating the table

With your CSV file to hand, open it in VS Code or a text editor of choice. At the top of the CSV file your headers should be listed with a comma separating them all (header, header two, header three, e.t.c&#8230;). Copy these header details into a new VS Code file and change the type of code to SQL to provide syntax highlighting (the button is located in the bottom right and within a new document will be set to &#8220;Plain Text&#8221;). With your text copied into the new document will now need to be formatted in the following way:<figure id="attachment_241" aria-describedby="caption-attachment-241" style="width: 714px" class="wp-caption aligncenter">

<img src="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/SQL-Table-Creation-Query.png?resize=640%2C396" class="size-full wp-image-241" height="396" alt="SQL Table Creation Query" width="640" srcset="https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/SQL-Table-Creation-Query.png?w=714 714w, https://i2.wp.com/shortmsgserv.co.uk/wp-content/uploads/2018/03/SQL-Table-Creation-Query.png?resize=300%2C186 300w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /> <figcaption id="caption-attachment-241" class="wp-caption-text">The CREATE TABLE SQL query</figcaption></figure> 

This first query doesn&#8217;t yet import our data but creates the table that our data will be copied into. I&#8217;ll run through each aspect of the query so it becomes clear what it does.

The first line &#8220;CREATE TABLE IF NOT EXISTS newtable&#8221; is a literal command. Postgres will check if the table &#8220;newtable&#8221; exists, if doesn&#8217;t it will create it, if it does exist it will proceed no further. Ensure you finish the line with the start bracket.

On a new line with an indent we have our first column with its data type. &#8220;header&#8221; is plain and simple text so can consist of something like &#8220;dog food&#8221; or &#8220;We need to order 54 more boxes of dog food&#8221;.

Notice with our second column header we have the underscore (&#8220;_&#8221;) between the words and also applied to the space between any word in any of our other headers. Just leaving a space and not including the underscore will cause a failure in the creation of our table so ensure you include these instead of any of your spaces.

Our description and status headers have also been encased in double quotes. This is because these words are already reserved by SQL itself and so will be interpreted as a command, causing a failure in the creation of the table.

For our &#8220;header_number&#8221; we&#8217;ve assigned it the type of INT which is short for integer; which according to a <a href="https://www.w3schools.com/sql/sql_datatypes.asp" target="_blank" rel="noopener">document on the Postgres website</a> is a number &#8220;-2147483648 to +2147483647&#8221;. Numbers can also be assigned to other numeric types such as FLOAT. Each of these assignments will have their own characteristics but one of the biggest issues to keep in mind is that the more complex the assignment, the greater amount of memory it will use; if you have a large dataset this can have a huge impact on the speed of your database. The document I&#8217;ve linked to has a brief overview of each number type, but for this example the two I&#8217;ve used are INT and FLOAT. The key difference between the two in this case is that INT cannot have a decimal point, but FLOAT can.

Another datatype used is INET. Postgres can use this type to natively understand IPv4 addresses, allowing them to be used and understood easily for computation as IP addresses. TIMESTAMP will identify the data as a time record, but make sure you&#8217;re aware that the data will have to be in a certain format to be understood.

Finally, as each record will need to have a unique number assigned to it due to the nature of relational databases we include a line for each record to be given a primary key. This is created with out ID SERIAL PRIMARY KEY. Theres no need for a comma after our primary key line so end with a close bracket and semi-colon. Do ensure that, as above, you&#8217;ve indented all your header names.

Copy this text to your clipboard, navigate to Postico and connect to your preferred database if you have more than one (I&#8217;ve used my shortname database titled matt). Once connected choose SQL Query on the left, paste your copied text and then click execute statement. Your table should then be created. Once complete refresh your database information in Postico with cmd + r and you should end up with a table entry on the left. Clicking on it should show a table with your headers created, but no data within the table.

# Importing your data

Initially when shown this I was shown a method of importing my data using a script; this exercise will focus on using the terminal command that allows the data from a singular file to be imported.

_$ psql -d matt -c &#8220;COPY newtable(header, header\_two, header\_number, header\_ip, header\_time, \&#8221;description\&#8221;, header\_second\_time, \&#8221;status\&#8221;, latitude) FROM &#8216;/Users/matt/Documents/CSVfilefolder/csvfile.csv&#8217; delimiter &#8216;,&#8217; CSV HEADER;&#8221;_

Again with this command you&#8217;ll need your column headers in the same format as the table creation except the reserved word headers will need \&#8221; instead of quotes alone.

This should then import your data which will populate the table within Postgres/Positco (ensure you refresh Postico to see it).

## [Optional] &#8211; Importing data from multiple CSV files using a script

An alternate way, and the way I was originally shown, is to import the data from a number of files (in my case around 340 files) using a script. This method however will rely on your data being formatted in a uniform fashion across all your CSV files. You can either create your script in a basic text editor, or use VS Code and choose &#8220;Shell Script&#8221; as the type of file.

The script I used is as follows:

<div>
  <div>
    <em>for csvfile in *.csv</em>
  </div>
  
  <div>
    <em>do</em>
  </div>
  
  <div>
    <em>psql -d matt -c &#8220;COPY global(header, header_two, header_number, header_ip, header_time, \&#8221;description\&#8221;, header_second_time, \&#8221;status\&#8221;, latitude) FROM &#8216;/Users/matt/Your/File/Directory/$csvfile&#8217; delimiter &#8216;,&#8217; CSV HEADER;&#8221;</em>
  </div>
  
  <div>
    <em>done</em>
  </div>
</div>

<div>
  You&#8217;ll see our terminal command mentioned previously (psql -d&#8230;) is largely the same but the file name at the end of the file path is $csvfile signifying what ever csvfile our script is currently working on.
</div>

<div>
  The for statement encasing our command is saying for EACH csvfile in *.csv do the following command. the * character is our wild card character so is simply saying that star character could be anything (ourcsvfile.csv, anycsvfile.csv, alargecsvfile.csv e.t.c.). Once your script is completed save the script file in the same directory as your CSV files. Navigate to that directory in terminal and give your &#8220;script.sh&#8221; file executable permissions by using the terminal command
</div>

<div>
  <em>$ chmod +x script.sh</em>
</div>

<div>
  Then run the script using
</div>

<div>
  <em>$ script.sh</em>
</div>

<div>
  Depending on your data size this may take some time; when complete your data should have been imported to your Postgres database.
</div>

# Presenting your data in Grafana

With the data imported into your table, you&#8217;ll now be able to show this data within Grafana for an easier way to analyse and present your data. Within Grafana create a new dashboard by clicking the + button in the left side panel. For the first panel choose single stat which will show a single number extracted from your data. With this panel added click on the disclosure triangle near the panel title and choose edit. Navigate to the &#8220;Metrics&#8221; tab where we&#8217;ll enter our SQL query that will produce our stat.

<div>
  <div>
    <em>SELECT COUNT(header_two) FROM newtable WHERE $__timeFilter(header_time);</em>
  </div>
</div>

<div>
  Breaking this down we can see that our SELECT statement is selecting the COUNT of our header_two column which will return the amount of rows we have in our newtable (as we have said FROM our newtable). We could leave the query at that, but this number would remain a static number which may not be all that useful. Adding the WHERE statement allows the stat to take into account the attached time recorded. This means if we want to return the count between two points of time (Grafana has a time frame selector in the top right) it will only return the count for that period.
</div>

<div>
  Another panel to add is the graph panel, add a graph panel and again navigate to its &#8220;Metrics&#8221; tab.
</div>

<div>
  <div>
    <div>
      <em>SELECT date_trunc(&#8216;hour&#8217;, header_time) AS time, COUNT(date_trunc(&#8216;hour&#8217;, header_time)) AS &#8220;Total&#8221;</em>
    </div>
    
    <div>
      <em>FROM newfile</em>
    </div>
    
    <div>
      <em>WHERE $__timeFilter(header_time)</em>
    </div>
    
    <div>
      <em>GROUP BY time;</em>
    </div>
  </div>
  
  <div>
    This time our query within SELECT is returning the header_time column with superfluous data removed as well as the number of entries within header_time. Our as statement simply changes the name this is outputted as to total instead of header_time. Our FROM directs the query to pull its data from our newfile table, WHERE allows us to add conditional statements (e.g. all data must equal 1). For our WHERE statement above includes a macro that is part of Grafana &#8220;$_timeFilter&#8221;, running this statement as is through Postgres/Postico will return an error. For the GROUP BY statement we are asking our data to be grouped by time which was previously created within &#8220;date_trunc(&#8216;hour&#8217;,header_time) AS time&#8221;.
  </div>
</div>

<div>
  Our two panel queries complete you should have a (very) basic dashboard in Grafana. I would advise also taking the time to look through the settings for each of the panels to see what works best with your data; one change that I found enhanced my dashboard was to change my graph from lines to bars. The instructions I&#8217;ve written here should work as a great starting point and allow you to expand your Grafana knowledge and if you have a browse online you&#8217;ll see some very impressive dashboards.
</div>