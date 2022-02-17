---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.
headline: Rails sends 0 byte files using send_file
datePublished: 30 Dec 2012, Mumbai
datetime: 2012-12-30T22:00
---

send_file has :x_sendfile param which defaults to true in Rails 3.

This feature offloads streaming download to front server - Apache (with mod_xsendfile) or lighttpd, by returning empty response with X-Sendfile header with path.

Nginx uses X-Accel-Redirect header for same functionality but you have to configure Rails properly in proper environment file:

<pre>
config.action_dispatch.x_sendfile_header = 'X-Accel-Redirect'
</pre>

<b>Rails 3 update: this line already exists in production.rb, just uncomment it.</b>

Add <b>sendfile on;</b> to your nginx config to utilize header sent by Rails.
Remember the absolute path must be used and nginx must have read access to file.