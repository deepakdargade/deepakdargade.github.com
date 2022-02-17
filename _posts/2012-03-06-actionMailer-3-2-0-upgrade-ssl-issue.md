---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.
headline: ActionMailer 3.2.0 Upgrade SSL Issue
datePublished: 06 Mar 2012, Mumbai
datetime: 2012-03-06T23:00
---

I upgraded my Rails app to Rails 3.2.0 from 3.1.3 and found that my SMTP outgoing mail was no longer able to authenticate with my mail server.

Further investigation revealed that my ActionMailer config was using the configuration option

<pre>
:tls => true,
</pre>

which is now effectively

<pre>
:enable_starttls_auto => true.
</pre>

But of course. After that quick change it worked.

The specific error message I was seeing was:

<pre>
OpenSSL::SSL::SSLError: SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B: certificate verify failed.
</pre>