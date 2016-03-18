---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.<br/>Best known for turning ideas into reality and Co-founder of Classpro.
headline: Nginx - Redirect non www to www
datePublished: 7 Dec 2013, Mumbai
datetime: 2013-12-07T22:00
---

Nginx 301 redirect (non-www to www – traditional way)

<pre>
server{
  server_name domain.com;
  rewrite ^(.*) https://www.domain.com$1 permanent;
}
</pre>

You should never use a rewrite.

Why? Because nginx has to process and start a search.

But if you use <b>return</b>, it directly stops execution. This is more preferred.

Nginx 301 redirect (non-www to www – new, efficient, & the best way)

<pre>
server{
  listen  80;
  server_name  domain.com;
  return  301 $scheme://www.domain.com$request_uri;
}

server{
  listen 443;
  server_name  domain.com;
  ssl on;
  ssl_certificate path_to_ssl.crt;
  ssl_certificate_key path_to_ssl.key;
  return 301 https://www.domain.com$request_uri;
}

server{
  listen 443;
  server_name www.domain.com;
  root /var/www/student-performance/public;
  ssl on;
  ssl_certificate path_to_ssl.crt;
  ssl_certificate_key path_to_ssl.key;
  passenger_enabled on;

  #rest of configuration

}
</pre>
