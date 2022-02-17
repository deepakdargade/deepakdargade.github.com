---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.
headline: Project collaboration using Git
datePublished: 15 July 2011, Mumbai
datetime: 2011-07-15T11:00
---

Install Git on both Server and Client machines.

if you’re on a Debian-based distribution like Ubuntu, try apt-get to install Git:
<pre>
apt-get install git-core
</pre>

<h2>Preferred way of doing GIT on server:</h2>

In order to initially set up any Git server, you have to export an existing repository into a new bare repository — a repository that doesn’t contain a working directory.

This is generally straightforward to do.
In order to clone your repository to create a new bare repository, you run the clone command with the --bare option. By convention, bare repository directories end in .git, like so:

<pre>
git clone --bare my_project.git
</pre>
output:
<pre>
Initialized empty Git repository in /var/www/my_project.git/
warning: this creates an empty git repository.
</pre>

<h2>On Client machine</h2>

<b>Step 1 on client machine clone the remote repository using,</b>

<pre>
git clone user@www.deepakdargade.me:/var/www/my_app.git
</pre>

output:
Initialized empty Git repository in /var/www/my_app/.git/
warning: You appear to have cloned an empty repository.

<b>Step 2 create a Readme file inside the my_app folder and add it to the stage and commit it,</b>

<pre>
git add Readme<br/>
git status<br/>
git commit -m "Initial commit adding readme file"
</pre>

<b>Step 3 check the remote repository information using</b>

<pre>
git remote -v
</pre>

output:
origin  user@www.deepakdargade.me:/var/www/my_app.git (fetch)
origin  user@www.deepakdargade.me:/var/www/my_app.git (push)

<b>Step 4 check your branches in local repository</b>

<pre>
git branch
</pre>

output:
* master


<b>Step 5 lets create a new branch that reflect new pre in the project.</b>

<pre>
git checkout -b develop master
</pre>

output:
Switched to a new branch 'develop'

<b>Step 6 again, check your branches in local repository</b>

<pre>
git branch
</pre>

output:
* develop
  master

<b>Step 7 lets switch to master branch</b>

<pre>
git checkout master
</pre>

output:
Switched to branch 'master'

<b>Step 8 adding remote path to git</b>

<pre>
git remote add origin ssh://user@www.deepakdargade.me/var/www/my_app.git
</pre>

<b>Step 9 pushing local master pre to remote repository</b>

<pre>
git push origin master
</pre>

<b>Step 9 same way push the develop pre to remote repository</b>

<pre>
git push origin develop
</pre>

<b>Step 10 to fetch the latest pre from the remote repository</b>

<pre>
git fetch origin < branch name > 
</pre>


<b>Git Tips: To remove a file(s) from Git</b>

<pre>
git rm --cached < file path > 
</pre>