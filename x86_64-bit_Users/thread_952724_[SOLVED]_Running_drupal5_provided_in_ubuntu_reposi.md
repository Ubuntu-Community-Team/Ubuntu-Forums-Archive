---
title: "[SOLVED] Running drupal5 provided in ubuntu repositories"
date: 2008-10-19
forum: x86 64-bit Users
---

### Post by etdsbastar on 2008-10-19
[SIZE=4]Hello friends,

I have successfully installed drupal5 with synaptic package manager in ubuntu. But, I don't know how to start drupal. 

Please help me regarding [COLOR=Blue]running of drupal5[/COLOR] in Ubuntu.

Thanks.[/SIZE]

---

### Post by cariboo on 2008-10-19
Drupal is a web application so you would access using Firefox, In the address bar type: [http://localhost](http://localhost) or [http://localhost/drupal](http://localhost/drupal). Check /var/www to see what the document root is.

Jim

---

### Post by etdsbastar on 2008-10-19
Hey Friend,

My /var/www is displaying only one folder naming apache2-default and one file naming index.html

Now what to do. Please help how to run drupal...

---

### Post by etdsbastar on 2008-10-19
Please,

Is anyone having guanine answer for running drupal5 and adding the same in applications menu

I am using x86 64-bit Hardy Heron...

Awaiting...

---

### Post by villindesign on 2008-10-20
I have not installed Drupal, but it should be similar to installing other web apps like Wordpress or Joomla. You need to have Lamps (**L**inux-**A**pache-**M**ySQL-**P**HP). So, create a mysql username, password, and database for Drupal. Then, add the information into the Drupal config file and point your browser to localhost/drupal/ to start the set-up.

Do you have Apache-MySQL-PHP installed?

See also Ubuntu help for [LAMPS]("https://help.ubuntu.com/community/ApacheMySQLPHP") and [Drupal]("https://help.ubuntu.com/community/Drupal")

---

### Post by etdsbastar on 2008-10-20
Yes, I have installed Apache-MySQL-PHP in my Ubuntu machine.

I just want to know how to start LAMP and Drupal.

---

### Post by villindesign on 2008-10-20
OK, good. now follow the directions [here]("https://help.ubuntu.com/community/Drupal"). The Community Documentation does not recommend installing Drupal from the repositories since it is old and does not include modules. After following the directions, post if you have problems.

---

### Post by etdsbastar on 2008-10-21
Hey friend...

thanks for your post. But, there was no result for your posting. I found rather an another way to sort it out...

Look at this:

I Just copied the contents from 

[COLOR=Red]**/usr/share/drupal5**[/COLOR]

and pasted the same here:

[COLOR=Red][B]/var/www/drupal

[/B][/COLOR]and then from mozilla i ran

**[http://localhost/drupal/](http://localhost/drupal/)**install.php

after the installation has been completed i just again ran

[http://localhost/drupal/](http://localhost/drupal/)

and my drupal is running perfectly.

**Please tell me if this process is correct or not?**

---

### Post by etdsbastar on 2008-10-21
[SIZE=4]Please reply me to my query as soon as possible...
[/SIZE]

---

### Post by cariboo on 2008-10-21
That will make Drupal run, but it may be insecure have done this:

```
sudo mkdir /var/www/drupal/sites/default/files
sudo chown www-data:www-data /var/www/drupal/sites/default/files

It is also required to create the initial configuration file for the default site.

sudo cp /var/www/drupal/sites/default/default.settings.php /var/www/drupal/sites/default/settings.php
sudo chown www-data:www-data /var/www/drupal/sites/default/settings.php
```

as list in the previous posters link?

This is more for security, that operation. This is especially if you intend on making Drupal live.

Jim

---

### Post by etdsbastar on 2008-10-22
Ya dear I had done everthing you listed in above code but I havent got any answer.

I don't know why the below given page is coming when i am trying to open [http://localhost/drupal](http://localhost/drupal)

***View the attachment "ss.png" please***

and nothing is happening except the page i shown in the attachment.

---

### Post by cariboo on 2008-10-22
Did you click on the sites directory to see if there is anything there? If all your files are located in the sites directory, just move them from the sites directory to the Drupal directory.

Jim

---

### Post by etdsbastar on 2008-10-23
> **cariboo907 said:**
> Did you click on the sites directory to see if there is anything there? If all your files are located in the sites directory, just move them from the sites directory to the Drupal directory.

Jim

No dear, Nothing found in sites directory, it is empty, except one '**default**' folder containing one **files** folder and two other php files named **dbconfig.php** and **settings.php.**

[B]Nothing else is happening

Help ...
[/B]

---

### Post by cariboo on 2008-10-23
This is a quick and dirty way to get drupal up nad running, Open a Applications-->Accessories-->Terminal and type:

```
cd /var/www
```

Hit enter. Next in the same terminal type:

```
sudo ln -s /usr/share/drupal5 drupal5
```

Enter your password when prompted.

To access your you new Drupal site in firefox type:

```
http://localhost/drupla5/install.php
```

From there just click on the links to set it up.

I don't recommend setting it up this way for a live site. This is just to get you going, so that you can play with Drupal.

For a live site go to the drupal web site, download and install the latest version and follow the installation instructions.

Jim

---

### Post by etdsbastar on 2008-10-23
> **cariboo907 said:**
> This is a quick and dirty way to get drupal up nad running, Open a Applications-->Accessories-->Terminal and type:

```
cd /var/www
```Hit enter. Next in the same terminal type:

```
sudo ln -s /usr/share/drupal5 drupal5
```Enter your password when prompted.

To access your you new Drupal site in firefox type:

```
http://localhost/drupla5/install.php
```From there just click on the links to set it up.

I don't recommend setting it up this way for a live site. This is just to get you going, so that you can play with Drupal.

For a live site go to the drupal web site, download and install the latest version and follow the installation instructions.

Jim

thanks a lot jim. my drupal is working perfectly after this action.

---

### Post by etdsbastar on 2008-10-31
Thank you everyone for the successful replies...

---

### Post by etdsbastar on 2008-11-11
thank you for the efforts.

---

