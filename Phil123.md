---
layout: page
title: Philosophy 123 privacy presentation
linktitle: Phil123
permalink: /en/phil123/
---

##Slides:

<iframe src="https://docs.google.com/presentation/d/1-ef6wXGBxMYzfnOLo6eEvS4XcyyvWWb7uNn3JptWXxw/embed?start=false&loop=false&delayms=3000" frameborder="0" width="480" height="299" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

The following techniques were demonstrated during the class:

* File encryption and decryption
* TorBrowser


Here is how you can repeat the steps to try the demonstration by yourself.

--------------

## File encryption and decryption

![pgp diagram](http://upload.wikimedia.org/wikipedia/commons/thumb/4/4d/PGP_diagram.svg/500px-PGP_diagram.svg.png)

The following steps can demonstrate how to encrypt and decrypt a file using public/private keys and message key.
This demonstration can be repeated in a Mac OS environment, and possibly a Linux environment.

# receiver

* prepare public and private keys
    * using the command `ssh-keygen` in a terminal
    * when prompt for file location, please fill in your preferred location and file name.
* transform the key format for encryption
    * private key: `openssl rsa -in phil123 -outform pem > phil123.pem`
    * public key: `openssl rsa -in phil123 -pubout -outform pem > phil123.pub.pem`
    * note that in this case, my private key is called `phil123` and public key is called `phil123.pub`.
        change the file name accordingly in your case.
* send the public key to the sender for secure communication.

# sender

* generate a key to encrypt the message
    * run `openssl rand 128 > key.bin` in a terminal
    * the file `key.bin` is then our key to encrypt and decrypt the message.
    * we need to make sure only the receiver can know the key
* encrypt the message with the key we just created
    * run `openssl enc -aes-256-cbc -salt -in SECRET_FILE -out SECRET_FILE.enc -pass file:./key.bin`
    * change the file name from `SECRET_FILE` to whatever your file is.
* encrypt the message key with receiver's public key
    * run `openssl rsautl -encrypt -inkey phil123.pub.pem -pubin -in key.bin -out key.bin.enc`
* send the encrypted message `SECRET_FILE.enc` and the encrypted message key `key.bin.enc` to the receiver

# receiver

* decrypt the key first using receiver's private key (only the private key can decrypt)
    * run `openssl rsautl -decrypt -inkey phil123.pem -in key.bin.enc -out key2.bin`
* decrypt the message with the message key `key2.bin` we just got
    * run `openssl enc -d -aes-256-cbc -in SECRET_FILE.enc -out SECRET_FILE2 -pass file:./key2.bin`


--------------

## Tor Browser

Download the Tor browser from https://www.torproject.org/

Here is some places you can start looking at in the deep web:

* [duckduckgo](https://3g2upl4pq6kufc4m.onion/)
* [TorLink](http://torlinkbgs6aabns.onion/)
* [Hidden Wiki](http://zqktlwi4fecvo6ri.onion/wiki/index.php/Main_Page)

# happy Toring!


