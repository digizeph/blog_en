---
layout: post
title: "svnnotify, SVN over HTTP, and SELinux"
categories: [tips]
tags: [svn, svnnotify, tips]
comments: True
---

Here is a strange case.
I am running a SVN repository for HTTP access.
It uses svnnotify script for sending out notifications on commits.
The repo is hosted on a Apache server, the location of the repo is at `/var/www/svn`.
The host system is running a CentOS 5.11.


One day, my advisor told me that he couldn't receive any notification emails.
So as usual, I checked the following items:

* is there any tailing space in the `post-commit` file?
* is the permission of the post-commit correct?
* is the post-commit script runs well?

I checked all the items and there seems to be nothing wrong with the system.
What can possibly go wrong here?

## SELinux Mandates!

When I see this line in the `/var/log/messages`, I knew it must be the SELinux's issue.

> SELinux is preventing the httpd from using potentially mislabeled files
> (/var/www/svn/repos/hooks/post-commit).
> For complete SELinux messages. run sealert -l 639e008c-7f30-4778-b1a9-77d2279ae2d0

So I ran the command as the error told me to, and here it is:

> Detailed Description:
> 
> SELinux has denied httpd access to potentially mislabeled file(s)
> (/var/www/svn/repos/hooks/post-commit). This means that SELinux will not allow
> httpd to use these files. It is common for users to edit files in their home
> directory or tmp directories and then move (mv) them to system directories. The
> problem is that the files end up with the wrong file context which confined
> applications are not allowed to access.

Aha!
It must be the fact that my advisor moved the file to its home,
editted it, and copied it back.
The result is that SELinux nolongger think that was the same file as before.
Therefore, SELinux stopped the script from running for security reasons.

So, to get things back to normal, I followed the instruction within the message:

> Allowing Access:
> 
> If you want httpd to access this files, you need to relabel them using
> restorecon -v '/var/www/svn/repos/hooks/post-commit'. You might want to relabel
> the entire directory using restorecon -R -v '/var/www/svn/repos/hooks'.

I never know that my system is running a [SELinux][centos-selinux] (I took that machine over when I joined the lab), 
and I would of course never suppect that the svnnotify would not work in such a strange case.

A precious lesson learned: **always edit the file at its original location**!

![PAX](https://upload.wikimedia.org/wikipedia/commons/b/ba/Pax_tux.png)

To learn more about SELinux and Mandatory Access Control (MAC), 
you can take a look at this [article][article].

[article]: http://www.linux-magazine.com/Issues/2008/91/SE-Linux
[centos-selinux]: https://wiki.centos.org/HowTos/SELinux
