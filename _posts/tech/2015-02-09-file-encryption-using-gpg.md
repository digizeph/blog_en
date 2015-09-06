---
layout: post
title: "File Encryption and Decryption Using GPG"
comments: True
---

Encryption decryption has been a "go-to" place for everyone who talks about how to reach perfect privacy.
However, among all those people who talks about encryption and privacy, there are still a large
portion of them knows little about how to actually do that in real-world.
That also includes myself.

Driven by the uncontrollable feeling of embarrassment, I finally decided to take a look at how
the encryption, decryption myths work on a normal no-secret computer.

The *goal* here is to have a hands-on experience on how to setup your own public/private key pair
and use the keys to do file encryption and decryption.

#step 1: set up keys

In order to enable yourself to access secrecy, you first need to create a pair of keys: public key and private key.
There is a nice explanation of how public key cryptography works on [Wikipedia][wiki:pki].

![pic:alice_keys](http://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Public-key-crypto-1.svg/200px-Public-key-crypto-1.svg.png)

Alice generates one public key and one private key, where public is given to anyone who wanted to securely communicate  with Alice.
The private key on the other hand will be kept secret, and only Alice will know it.
When Bob wants to send a secret message that only Alice can know about, it will obtain Alice's public key,
and then encrypt the message with the public key and send it over to Alice.
Upon receiving the secret message, Alice can use its secret key to decrypt the message.
This methods works simply because one fact: only Alice knows about the private key, and therefore only Alice can decrypt the message.

![pic:alice_bob_comm](http://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Public_key_encryption.svg/200px-Public_key_encryption.svg.png)

Here what we are going to do is to create a pair of the public/private key pair for ourselves.
In order to do so, we will take the usage of [GnuPrivacyGuard][gpg] toolkit,
or the [GPGTools][gpgtools] which provides a set of tools that can help us creating the keys and publish it as well.

Download install the GPGTools from their website first.
We will now have a new program called "GPG Keychains".

![](https://farm9.staticflickr.com/8572/16488487425_727a112d9f_o.png)

Using this tool, we can then generate our keys.

In the following steps, I will show you how to step by step create a pair of public/private keys using GPG Keychain.
When you open the program, you will see a window with a list of keys and their information displayed.
Each one of them represents a key that either is created by you, or obtained from other sources.
In order to securely communicate with others, you will need all of you contacts listed here.

![List of keys](https://farm8.staticflickr.com/7348/15865999874_8eb80361d2_o.png)

To create a new key pair, click on the "New" button on the top-left corner of the program.
Then you will see a window like the one shown below.
Here you will need the following information to create the key pair:

* The name that you want be found with. Note that, in most cases, your public key will be uploaded to a online server, in which your friends can look up and find your key by the name you put in.
* The email address that you want your key associate with. When people want to write you a email, they can also look up the email address and obtain the key to encrypt the message to you.
* Expiration date. Not every key can live forever, and you can decide how long the key will be valid for.
* *PASSPHRASE*: the passphrase is very important. It provides a second layer of protection against private key theft. Say you lost your private key file to some one, and he wants to impersonate your online identity, it still needs a  correct passphrase for the private key to do that.
* Key type and length. You can choose the algorithm to use for the key and the length of the keys. Default is usually more than enough.

![](https://farm9.staticflickr.com/8613/16488532315_d9b5fe5124_o.png)

With these fields filled, you can then proceed and generate the key pair (see below).
Once you click "Generate key", the program will collect some random information obtained from your computer to create a better "randomized" key.
During this phase, you can type your keyboard and click the mouse randomly to create some more seeds for the program.

![](https://farm8.staticflickr.com/7285/16302623957_960e53c71f_o.png)

After that, you will then have the new key pair with you!
Go ahead and double-click the item to view the details of the key you just created.

![](https://farm8.staticflickr.com/7394/16302260579_35d90e6e69_o.png)

# step 2: use the key to encrypt any files

We will now try to encrypt this cat picture.

![](https://farm8.staticflickr.com/7335/16531916581_c996cc6030_o.png)

First, right click on the photo, and select "Services" ->  "OpenPGP: Encrypt File".

![](https://farm9.staticflickr.com/8621/16507630416_2e80f976e0_o.png)

![](https://farm9.staticflickr.com/8667/15911063934_7fbbf500b8_o.png)

Then you will be prompted to enter the recipients of the encrypted file.
Note that the purpose of the whole encryption is to ensure that *only* the recipients can view the content of the files, no one else can.
Here I will just choose myself as the recipient.

![](https://farm9.staticflickr.com/8581/16531916251_f4dd837de0_o.png)

Then we will have the encrypted version of the cat photo.

![](https://farm8.staticflickr.com/7343/16347359679_8d5229b2b1_o.png)

![](https://farm9.staticflickr.com/8617/16346172850_1816399809_o.png)

# step 3: decrypt the secret files

The recepient of the encrypted files is able to decrypt the file using its private key that corresponds to the encryption public key.
Using GPG Tools, you will just have to right click the file and select "Services" -> "OpenPGP: Decrypt File".

![](https://farm9.staticflickr.com/8667/16347728087_baf3c70b22_o.png)

If you set the passphrase for your key, then you will need to type in the passphrase in order to use your private key.

![](https://farm9.staticflickr.com/8671/16507630206_d6f138ede7_o.png)

Then here we go.

![](https://farm8.staticflickr.com/7318/16507630166_135453e56d_o.png)

![](https://farm8.staticflickr.com/7319/15913450383_ed7f30dc19_o.png)

# summary

In this post, I briefly described how you can encrypt and decrypt files using GPG Tools.
More importantly, we also see how to create and use the public/private key pair in practice.
More applications like email signature and encryption can be found on their [official website][gpgtools]
I hope you can enjoy this post.


[wiki:pki]: http://en.wikipedia.org/wiki/Public-key_cryptography "Public key cryptography"
[gpg]: https://www.gnupg.org/
[gpgtools]: https://gpgtools.org/
