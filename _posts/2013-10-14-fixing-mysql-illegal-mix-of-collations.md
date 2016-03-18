---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.<br/>Best known for turning ideas into reality and Co-founder of Classpro.
headline: Fixing MySQL’s Illegal Mix of Collations
datePublished: 14 Oct 2013, Mumbai
datetime: 2013-10-14T10:00
---

I recently started to encounter MySQL’s dreaded illegal-mix-of-collations error. The occasional query would result in Illegal mix of collations (latin1_swedish_ci,IMPLICIT) and (utf8_general_ci,COERCIBLE) for operation '='.

<pre>
Mysql2::Error: Illegal mix of collations (latin1_swedish_ci,IMPLICIT) and (utf8_general_ci,COERCIBLE)
</pre>

MySQL’s default character set is latin1 with an adventurous Swedish collation, which presumably seemed like a good idea at the time. However Rails uses UTF-8 everywhere and from time to time the two collations collide.

<br/>
<h3>How I solved it:</h3>
First figure out where you stand. In MySQL do this:

mysql> show variables like 'char%';
The result you want is this:

<pre>
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8                       |
| character_set_connection | utf8                       |
| character_set_database   | utf8                       |
| character_set_filesystem | binary                     |
| character_set_results    | utf8                       |
| character_set_server     | utf8                       |
| character_set_system     | utf8                       |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
</pre>

At this stage several of these values will be latin1.

Similarly for collation:

<pre>
mysql> show variables like 'collation%';
+----------------------+-----------------+
| Variable_name        | Value           |
+----------------------+-----------------+
| collation_connection | utf8_general_ci |
| collation_database   | utf8_general_ci |
| collation_server     | utf8_general_ci |
+----------------------+-----------------+
</pre>

The utf8_general_ci collation will do but ideally we want utf8_unipre_ci. The former basically ignores all accents: it treats ‘ü’ the same as ‘u’. The latter pays attention to accents; it’s a tiny bit slower but more accurate.

To see what your tables are using:

<pre>
mysql> show table status \G
</pre>

…and look at the Collation field in each table.

<br/>
<h3>Configuring MySQL to use UTF8</h3>
I added this configuration to /etc/mysql/my.cnf (on Ubuntu 10.04):

<pre>
[mysqld]
character-set-server=utf8
collation-server=utf8_general_ci
</pre>

After I had done all this and restarted mysql, I found all the character_set_* variables were correct except character_set_database. To fix this:

<pre>
mysql> alter database DATABASE default character set utf8;
</pre>
<pre>
mysql> alter database DATABASE default collate utf8_general_ci;
</pre>
<pre>
mysql> ALTER TABLE tablename CONVERT TO CHARACTER SET utf8 COLLATE utf8_general_ci;
</pre>

<br/>
<h3>Verifying everything worked</h3>

In the MySQL console I ran these:

<pre>
mysql> show variables like 'char%';
mysql> show variables like 'collation%';
mysql> show create database DATABASE;
mysql> show table status \G
</pre>

And then in the Rails console:
<pre>
>> ActiveRecord::Base.connection.collation
"utf_general_ci"
</pre>