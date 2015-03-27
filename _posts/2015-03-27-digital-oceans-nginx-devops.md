---
title: DigitalOcean, Nginx, Some devops
layout: post
---

[Background on digitalocean and droplets]


### A. Create a DigitalOcean account

1. Create an account in digitalocean (DO) using [this referral link](https://www.digitalocean.com/?refcode=0e555c3228a6) and enter your credit card data. (The link is a referral link that will also give you $10 free credit - or up to two free months worth).

1. Check that you have the $10 credit by going to "Billing" in DO. Then lick on "Manage Payments" to see if you have the credit. If you don't have credit, try [the referral link](https://www.digitalocean.com/?refcode=0e555c3228a6) again. If that fails, find and apply a coupon from [retailmenot](http://www.retailmenot.com/view/digitalocean.com).



### B. Grab your SSH from your local machine

Before you create your first droplet, you need to add an SSH key to your DigitalOcean ("DO") account. SSH is more robust against brute force password attacks, so you want to use it over password authentication. _Adapted from [DO's SSH instructions](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets)._

1. On terminal on a Mac `$ cd /.ssh` then `$ ls` to check your folder's contents.

1. If you don't have the files `id_rsa` and `id_rsa.pub` in this folder, create them by `$ ssh-keygen -t rsa -C "YOUR@email-address.com"`.

1. When prompted with **"Enter file in which to save the key"** just hit Enter.

1. When prompted for passphrase, just hit enter again if you don't want to set a password (this is usually the most convenient way to work). Otherwise, if you want to be more security at the expense of convenience, enter a passphrase and WRITE IT DOWN somewhere.

1. You should then see your key fingerprint (looks sort of like `9E:3H:W5:0A...`). You will also see your key's randomart image.

1. Copy the public key from here `$ cat ~/.ssh/id_rsa.pub`.


### C. Set up your SSH on DigitalOcean

Now we want to paste the copied key into your DigitalOcean account so that it stores it in memory.

1. In DigitalOcean, click on your name in the upper right corner and select "Your Settings".

1. Click the "Security" tab.

3. In the SSH section, paste the public key in and give your key a name __of your computer you are currently accessing from__ (for example: `johns-mba-2012-13in`).


### D. Create your first droplet

With your SSH added to DO, you can now create your first Droplet.

1. "CREATE" a new droplet.

2. Name your droplet. This is a project name that isn't public. Name it something like "personal-resume-site". If you already know your planned hostname (YOUR-DOMAIN), you can put that instead. For instance "happyblimp" if it's `happyblimp.com`.

3. Select the cheapest droplet ($5/mo).

4. Select New York #3 region (the bigger the region number, the newer and better).

5. Leave all the Available Settings as is.

6. Select "Ubuntu 14.04 x64" (this should also be the default set) from servers.

7. In "Add optional SSH Keys" click on your Key so that it turns from gray to blue. You will also no longer receive an email with the root login password.

8. Leave the "Settings" per defaults and "Create Droplet".

Congrats! You now have a DO VPS (Virtual Private Server) in the cloud that you can access. This server is running a version of Linux called Ubuntu which is like the Linux that runs your terminal on your Mac - so it will be a very familiar environment.


### E. Log into your DO server (droplet)

1. Copy your IP Address from DigitalOcean to your clipboard

2. To access your server's terminal from your local terminal, do the following in your local terminal: `$ ssh root@[IP ADDRESS]`.

3. If you get something like the below, don't worry:

    ```
    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    @    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
    Someone could be eavesdropping on you right now (man-in-the-middle attack)!
    It is also possible that a host key has just been changed.
    The fingerprint for the RSA key sent by the remote host is
    [LOOKS LIKE LONG MAC ADDRESS].
    Please contact your system administrator.
    Add correct host key in /Users/[YOU]/.ssh/known_hosts to get rid of this message.
    Offending RSA key in /Users/[YOU]/.ssh/known_hosts:16
    RSA host key for [IP ADDRESS] has changed and you have requested strict checking.
    Host key verification failed.
    ```

    Just delete the "offending" line from your `~/.ssh/known_hosts` file and then try again. The offending line may be at the bottom (it may look like multiple lines due to wrapping). It likely starts with the same IP address as on your DO (hence the conflict).

4. The first time you SSH into your DO's server, you'll see this:

    ```
    The authenticity of host '[IP ADDRESS] ([IP ADDRESS])' can't be established.
    RSA key fingerprint is [LOOKS LIKE A LONG MAC ADDRESS].
    Are you sure you want to continue connecting (yes/no)?
    ```

    Type "yes" and hit `enter`.

5. Copy the wp-admin password that this pre-installation of Wordpress provides you and paste it into some notepad or somewhere. You will need this later.

3. At this point, DigitalOcean's one-click instructions has you install Wordpress. We're not going to do that yet. PublishingWithWordpress' guide has some optimization instructions we'll do first. Not sure if this order is necessary, but the author does them first so we'll follow suit. While still in your SSH terminal session, do the following in order:

    ```
    #=> NOTE: The prompt on the server may show a hashtag # instead of dollar sign $ as on your machine. We'll keep using dollar sign notation.
    $ sudo apt-get update
    $ sudo apt-get upgrade       #=> "dist-" deals with dependencies but adds ~270MB
    $ sudo a2enmod rewrite
    $ dd if=/dev/zero of=/swapfile bs=1M count=1024
    $ mkswap /swapfile
    $ swapon /swapfile
    $ sudo nano /etc/fstab
    #=> ADD the following line to the fstab file:
    /swapfile swap swap defaults 0 0
    #=> verify the swap file is active (should show 1GB free):
    $ free
    ```




