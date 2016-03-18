---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.<br/>Best known for turning ideas into reality and Co-founder of Classpro.
headline: Ruby on Rails to_json with include
datePublished: 11 Dec 2011, Mumbai
datetime: 2011-12-11T23:00
---

If the models aren't associated through active record, then fetching json data is pretty simple in Ruby on Rails.
<pre>
respond_to do |format|
  format.json  { render :json => @order}
end
</pre>

If an association does exist, you can pass an :include argument to the render call, like so:

<pre>
respond_to do |format|
  format.json  { render :json => @order.to_json(:include => [:payments])}
end
</pre>