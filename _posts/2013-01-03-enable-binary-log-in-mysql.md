---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.<br/>Best known for turning ideas into reality and Co-founder of Classpro.
headline: Enable binary log in Mysql
datePublished: 03 Jan 2013, Mumbai
datetime: 2013-01-03T15:00
---

To enable binary log in Mysql, edit the file:

<pre>
/etc/mysql/my.cnf
</pre>

Uncomment the log_bin line:

<pre>
log_bin = /var/log/mysql/mysql-bin.log
</pre>

<pre>
expire_logs_days = 10
</pre>

<pre>
max_binlog_size = 100M
</pre>