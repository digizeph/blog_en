---
layout: post
title: "Simple Procmail Tutorial"
comments: True
---

If your school uses a unix/linux servers as Email systems,
you can use Procmail to process your emails and put them in the right folders before your email client fetching the email.
This can be especially useful if you receives frequent emails and want to automatically move them into some folders.

Using email client in this case is not enough.
Consider this case where you have more than one machines, and one of them (A) has a filter that moves emails.
When a email comes, your machine A may fetch the email later than other clients,
leaving the other clients put the email into a different folder than your machine A.

For example, I've just set up the Fail2Ban program on my lab's servers and set it to generate automated reports and send them to me.
I can receive tens of emails per day and I would just like to put them away and take a look whenever I have time.
So I would like to ask my email server to archive this type of emails to a folder called "Fail2Ban" out of my inbox.
Here is the steps

## 1. Locate the email folder

The email folder on my email server is located at

    ~/mail/

All the folders apart from the inbox are located in this folder.

## 2. Write a Procmail rule.

After you've located the mail folder, you can write the procmail rule to enable the automatic archiving.
Open the file .procmailrc and add the following lines to the file:

    # archive Fail2Ban emails to Fail2Ban folder.
    :0:
    * ^(From|Cc|To).*(Fail2Ban)
    $MAILDIR/Fail2Ban

The line ```:0:``` indicate that the following lines belong to a new rule.
```*``` indicate that this line has the regular expression for matching the emails.
Once procmail matches a email, it will move the email to the folder ```$MAILDIR/Fail2Ban```.

Note that there can be more actions than just moving to specific folders.
If you'd like to learn more about writing the procmail rules, you can read [this post][procmail_post].

## Enjoy the geeky way of filtering your emails！

[procmail_post]: http://userpages.umbc.edu/~ian/procmail.html
