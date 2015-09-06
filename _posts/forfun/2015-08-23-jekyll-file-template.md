---
layout: post
title: "Creating template Jekyll post using Bash"
categories: [systems]
tags: [jekyll, bash]
comments: True
---

## A lazy person's problem

Creating new posts in Jekyll sometimes can be hard,
especially when you are not that familiar with all the options in the jekyll post header.
Specifically, the header of the posts, like the following example:

    ---
    layout: post
    title: "Creating Jekyll post files using Bash script"
    categories: [systems]
    tags: [jekyll, bash]
    comments: True
    ---

For someone like me, it takes too many steps to find an existing post, copy the headers and paste into the new file.
To make things even worse, the file format of jekyll posts require a full date (e.g. `2015-08-23`),
which is a pain to lookup and type everytime you want to write a post.

Thus, as a super lazy person, I created the following script to help me create a new post
and fill in all the fields in the header.

## The script

<script src="https://gist.github.com/digizeph/b0b3fe5388e398e09924.js"></script>

## What does the script do?

This script will first ask for the values of the folloing fields, 
and then generate a file with all fields filled:

* Title: the title of the post.
* Filename: the file name part that is after the date and before the `.md` suffix.
* Categories: the values of the categories, without the brackets.
* Tags: the values of the tags, without the brackets.

Then it will generate a file using the current date and the filename value,
and fill in all the fields you just put in.
Here is an example interaction:

    $ jekyllpost.sh
    Title:
    This is a test post for template.

    Filename:
    Test Post

    Categories:
    jekyll

    Tags:
    test, jekyll

    $ ls
    2015-08-23-test-post.md

    $ cat 2015-08-23-test-post.md
    ---
    layout: post
    title: "This is a test post for template."
    categories: [jekyll]
    tags: [test, jekyll]
    comments: True
    ---

Note that I also added a small snippet to convert the filename into all lower case characters and replace spaces with '-'.
Now we have a perfectly formated jekyll post file for us to write!

Also, if you want to easily access the script, please add the script folder into [$PATH](http://www.cyberciti.biz/faq/appleosx-bash-unix-change-set-path-environment-variable/). 
Or put your script into `/usr/local/bin` folder.

## Enjoy!

