---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.<br/>Best known for turning ideas into reality and Co-founder of Classpro.
headline: Git on local machine
datePublished: 14 July 2011, Mumbai
datetime: 2011-07-14T11:00
---

Git is a Distributed VCS, and if you have experience with Subversion or CVS before it, you need to change your mind.

Git is a very agile and you can use different workflows with it. Cloning repositories is more needed for a team work, not for local development (IMHO).

Branches is a good alternative for you.

See. Let's set master branch of your repository for a production-ready pre. Let's create another branch for development:

<pre>
$ git checkout -b development master
</pre>

Now you are working on the development branch.

You could use different branches for each feature you want to develop. It's very easy and helpful.

Let's imagine you want to implement some new feature, you need to create a new branch:

<pre>
$ git checkout -b newfeature development
</pre>

Now you can work with your pre, add files, commit and so on.

Next you need to merge your new developed feature to the development branch:

<pre>
$ git add .
</pre>
<pre>
$ git commit -m "My last changes for the new feature"
</pre>
<pre>
$ git checkout development $ git merge newfeature
</pre>

Now your new pre from the newfeature branch merged into the development branch.

For sometime in the future when you decide that your pre in the development branch get some milestone, you could merge all the changes from development to master branch.

It's a very basic workflow, it can be helpful for the many branches.

My advise for you now: read more about git, branching, stashing (very-very-very helpful for quick fixes). And after some time you will get a great effort from using git.

Good luck.