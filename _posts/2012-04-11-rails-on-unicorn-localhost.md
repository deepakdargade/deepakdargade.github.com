---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.
headline: Rails on Unicorn - Localhost
datePublished: 11 Apr 2012, Mumbai
datetime: 2011-04-11T23:00
---

Time for flying rainbow horses. Start by installing the Unicorn gem:

<pre>
gem install unicorn
</pre>

You should now have Unicorn installed: unicorn (for non-Rails rack applications) and unicorn_rails (for Rails applications version >= 1.2) should be in your path.

Time to take it for a spin! (You may wish to re-login with su - USERNAME if you haven’t already, this ensures your permission tokens are set, otherwise you will not have write permission to /var/www)

<pre>
rails new unicorn
</pre>

There we go, we now have our Unicorn Rails test app in /var/www! Let’s fetch some Unicorn config and start the madness. We’re going for the unicorn.conf example that comes with the Unicorn source:

<pre>
curl -o config/unicorn.rb
</pre>

<pre>
https://raw.github.com/defunkt/unicorn/master/examples/unicorn.conf.rb
</pre>

You might want to tweak a few things:

<pre>
APP_PATH = "/var/www/unicorn" working_directory APP_PATH
</pre>

<pre>
stderr_path APP_PATH + "/log/unicorn.stderr.log"
</pre>

<pre>
stdout_path APP_PATH + "/log/unicorn.stderr.log"
</pre>

<pre>
pid APP_PATH + "/tmp/pid/unicorn.pid"
</pre>

Our Unicorn is ready! Rainbow magic

Start the Nginx deamon, how this is done depends on your OS. And then start Unicorn:

<pre>
unicorn_rails -c /var/www/unicorn/config/unicorn.rb -D
</pre>

-D deamonizes it. -c should be pretty obvious; it specifies the configuration. In production you will probably want to pass -E production as well to run the app in the production environment.

That’s it! Visiting localhost should take you to the Rails default page.