---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.<br/>Best known for turning ideas into reality and Co-founder of Classpro.
headline: Position of callbacks is important in Rails Model
datePublished: 29 Feb 2012, Mumbai
datetime: 2012-02-29T23:00
---

Yesterday i was working on destroy action of a model in. Before deletion I had to check whether the model has any child model or not. Even the model has child model, but deletion was successful even though i had set to false.

So i got curious and checked the rails issues. There i got to know a important concept of position of different members of model class in rails.

In my case i had placed belongs_to, has_many, validations and then callbacks.

So if I am using before_destroy, the rails follows the same sequence in my model. It first deletes the associated models if dependent destroy is mentioned, then checks for validations and then my before_destroy callback where i had explicitly told it to return false if child model size > 0. But since child model are already destroyed the size is 0 and my condition in before_destroy fails.

The solution is to place before_destroy above all.

So now rails will call callbacks first and then associations and validations.

It also helps in reducing the number of sql queries executed. In my case it reduced from 25 to 5. pretty good.