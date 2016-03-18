---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.<br/>Best known for turning ideas into reality and Co-founder of Classpro.
headline: Rails 3 data attributes in select tag
datePublished: 11 Dec 2011, Mumbai
datetime: 2011-12-11T23:00
---

in Rails we can add custom attributes to select options, using the existing options_for_select helper.

If you need grouped options, you can use the grouped_options_for_select helper, like this (if @continents is an array of continent objects, each having a countries method):

<pre>
<%= f.select :country_id, grouped_options_for_select(@continents.map{ |group| [group.name, group.countries.map{ |c| [c.name, c.id, {'data-currency_pre'=>c.currency_pre}] } ] }, selected_key = f.object.country_id) %>
</pre>