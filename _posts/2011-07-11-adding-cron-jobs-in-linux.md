---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.<br/>Best known for turning ideas into reality and Co-founder of Classpro.
headline: Adding cron jobs in Linux
datePublished: 11 July 2011, Mumbai
datetime: 2011-07-11T09:00
---

Cron is a Linux system process that will execute a program at a preset time.

To use cron you must prepare a text file that describes the program that you want executed and the times that cron should execute them.

Then you use the crontab program to load the text file that describes the cron jobs into cron.

For example if we want to execute a script (.sh file) on linux server each day at a specific time, we need to use cron jobs provided by the linux server.


<h3>Steps for adding a cron job:</h3>

<b>Step 1: To check for existing cron jobs running, open a terminal and enter</b>

<pre>
crontab -e
</pre>

o/p: it will show the cron jobs for the existing user.

<b>Step 2: The cronjob resides in the file</b>

<pre>
/etc/crontab
</pre>

<b>Step 3: edit this file to add cron job using,</b>

<pre>
nano /edit/crontab
</pre>

<b>Step 4: add the following line to the end of the file</b>

<pre>*  *  root /var/www/hello.sh</pre>
<pre>03 05 *  * root /var/www/hello.sh</pre>

the first line runs the hello script after every 1 minute.
and the second line executes the hell oscript at 03:05 am.

<b>Step 6: make sure to restart the cron process using</b>

<pre>
restart cron
</pre>

<br/>

For more information on cron job format visit <a target="_blank" href="http://www.scrounge.org/linux/cron.html">http://www.scrounge.org/linux/cron.html</a>

and for Mysql Backup script, visit <a target="_blank" href="http://www.cloudtech.org/2010/07/30/backup-mysql-databases-automatically-on-your-vps/">http://www.cloudtech.org/2010/07/30/backup-mysql-databases-automatically-on-your-vps/</a>