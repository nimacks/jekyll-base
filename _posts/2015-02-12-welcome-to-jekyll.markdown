---
layout: post
title:  "Understanding the Git file system"
date:   2019-01-17 13:46:40
categories: distributed git
---
Git is arguably the most popular version control system for tracking changes in computer files and coordinating work on those files among multiple people.

It is a distributed system which helps manage small and very large projects efficiently and with very good performance. One of the most attractive things about Git which I believe has contributed to its incredible popularity is that it's easy to learn. With a few commands, you can get a project up and running in a matter of minutes.

However, because Git is so easy to learn, developers often forget to look under the covers to understand what is happening when you run a git command. 

In this article we'll walk through a few common scenarios to use git with a special emphasis on understanding how commands are executed.

### Creating a repository
Matthew is a developer who works for a trucking company called Blue Trucks. He's been asked by his boss to create a new website for the company and has chosen git to be his choice for version control. He begins by creating a new directory and issuing a command to initialize a new repository

![asciicast](https://distributedhash.s3-us-west-2.amazonaws.com/git-init.gif "asciicast")

### Under the covers
Creating or initializing a new repository is done with the command `git init`. This command creates a set of files that will be used to track changes to the files you add. The diagram below shows the list of files created. Let's walk through each file and understand it jobs.
{% highlight bash %}
$ ls 
config
description
HEAD
hooks/
info/
objects/
refs/
{% endhighlight %}


##### *HEAD* 

##### *branches*

##### *config*
 The config file contains your project-specific configuration options.

{% highlight java %}
[core]
        repositoryformatversion = 0
        filemode = false
        bare = false
        logallrefupdates = true
[remote "origin"]
        url = https://github.com/nimacks/blueprints.git
        fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
        remote = origin
        merge = refs/heads/master
 {% endhighlight %}

##### *description*
The description file is used only by the Gitweb program and aptly describes the repository by giving it a name.The default contents of the content contain the following:

{% highlight bash %}
Unnamed repository; edit this file 'description' to name the repository.
{% endhighlight %}


##### *hooks*
The hooks directory contains your client- or server-side hook scripts.
##### *info*
The info directory keeps a global exclude file for ignored patterns that you don’t want to track in a .gitignore file.

{% highlight bash %}
" ============================================================================
" Netrw Directory Listing                                        (netrw v156)
"   /Playground/blueprints/.git/info
"   Sorted by      name
"   Sort sequence: [\/]$,\<core\%(\.\d\+\)\=\>,\.h$,\.c$,\.cpp$,\~\=\*$,*,\.o$,\.obj$,\.info$,\.swp$,\.bak$,\~$
"   Quick Help: <F1>:help  -:go up dir  D:delete  R:rename  s:sort-by  x:special
" ==============================================================================
../                                                                                                                     ./
exclude*
{% endhighlight %}


##### *objects*
The objects directory stores all the content for your database
##### *refs*
The refs directory stores pointers into commit objects in that data (branches, tags, remotes and more)

In part two in this series we'll look at what happens when you add, commit and push to a remote repository.


{% highlight java %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
