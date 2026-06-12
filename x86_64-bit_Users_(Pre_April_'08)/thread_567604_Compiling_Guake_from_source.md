---
title: "Compiling Guake from source"
date: 2007-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Johnny K on 2007-10-04
Hey there. I think that [Guake]("http://www.gnomefiles.org/app.php?soft_id=2159") sounds pretty cool. Unfortunately, there is no 64 bit deb available. How would I go about compiling it from source (or even better, do you know of a 64 bit deb available)?

TIA :)

---

### Post by miggols99 on 2007-10-06
I guess you would just do

./configure
make
sudo checkinstall/sudo make install

---

### Post by Johnny K on 2007-10-08
I don't understand. How do I use those commands with the file guake-0.1.tar.gz ?
```
make guake-0.1.tar.gz 
```
gives an error. Does it need other options?

---

### Post by Tasu on 2007-10-08
> **Johnny K said:**
> I don't understand. How do I use those commands with the file guake-0.1.tar.gz ?
```
make guake-0.1.tar.gz 
```
gives an error. Does it need other options?

I'm attaching the deb I made.

Well however that's not the proper way to use make, normally you have to unzip the tar.gz, cd to the directory created and issue these commands 
```

./config # This command checks for all the dependecies for the source package
make # This command compiles the source in a binary file
sudo make install # This command installs in the right folder the binary file just compiled

```
In the case, however, the ./config is handled by the autogen.sh script that you can find in the source folder, to compile guake myself I found I needed a lot of dev packages, I can't remember which ones, it was just a matter of tries and errors.
Anyway, here is the 64bit package I compiled using checkinstall (not the best way in terms of debian policy compliance, but it's a fast way to have a deb! ^_^).

P.S. However Guake is not so stable at the moment, a good piece of software, but not so stable, with compiz-fusion enabled, the second time I access the guake terminal it won't show anything other than a grey window!)

P.P.S When I installed it the first time, I thought it would have user true transparency, but that's not the case! O_O Probably in future versions! Who knows! ^_^

---

### Post by Johnny K on 2007-10-08
Thanks for all the great info!

But when I try to run Guake, I get the error message "Guake can not init! Gconf Error. Have you installed guake.schemas properly?"

What is causing that error? And how do submit that deb so that it appears in synaptic?

---

### Post by John.Michael.Kane on 2007-10-08
> **Johnny K said:**
> Thanks for all the great info!

But when I try to run Guake, I get the error message "Guake can not init! Gconf Error. Have you installed guake.schemas properly?"

What is causing that error? And how do submit that deb so that it appears in synaptic?

And did you try the below command found here [http://www.gnomefiles.org/app.php?soft_id=2159](http://www.gnomefiles.org/app.php?soft_id=2159)
ATENTION:

After install please run the following command:

gconftool-2 --install-schema-file=/usr/etc/gconf/schemas/guake.schemas

---

### Post by Johnny K on 2007-10-08
Oh right, I forgot about that. Thanks for pointing that out.

However, I get an error message when I try to do that. There is no /usr/etc/gconf on my filesystem. There is a /usr/share/gconf/schemsas, but no guake.schemas in it.

---

### Post by Tasu on 2007-10-09
On a Ubuntu computer, the right command is:
```

gconftool-2 --install-schema-file=/usr/local/etc/gconf/schemas/guake.schemas

```
the command issued by SD-Plissken is right if you compile from source by yourself, package files instead need to be compliant with the Debian Policies even in where confg files must be placed in your file system (coherence is coherence!  And it's important! ^_^).

However you could have easily found where the deb package has put the guake.schemas file by opening synaptic (System -> Administration -> Synaptic Package Manager), search for guake (left panel Status tab->Installed (Local or Obsolete), then right click on the package-> Properties, there you could see a tab called Installed Files, here you'll find where the package put all the files.
Another way a lot faster (well the updatedb command takes some time to index every file, but it's faster issuing two simple commands than going through all those menu messes! ^_^) is via the command line (my preferred way), by issuing those 2 commands (just copy and paste):
```

sudo updatedb
locate guake.schemas

```
Thus when someone tells you to issue some commands that seems non existent in your installation, you can check for yourself if the path to the file is the same as the hint you recieved. ^_^

---

### Post by Johnny K on 2007-10-09
Awesome, works great! Thanks!

The deb that you created, is it able to be submitted to Ubuntu's repository (and things like getdeb.net), or should I not do that because you used checkinstall?

---

### Post by John.Michael.Kane on 2007-10-09
> **Johnny K said:**
> Awesome, works great! Thanks!

The deb that you created, is it able to be submitted to Ubuntu's repository (and things like getdeb.net), or should I not do that because you used checkinstall?

Checkinstall debs are not for Ubuntu's repository. Files for the repo go through a more rigorous check. I'm not sure how the getdeb group handles deb uploads. 

Edit: Heres how getdeb handles deb files.
[Preparation]("http://wiki.getdeb.net/Package_Building/Preparation")

Bottom line check install is for personal use or in some cases passing on to friends in need of a deb who don't know how or don't want to compile their own.

---

### Post by Tasu on 2007-10-09
> **Johnny K said:**
> The deb that you created, is it able to be submitted to Ubuntu's repository (and things like getdeb.net), or should I not do that because you used checkinstall?

Thank you for the apreciation, but I've just compiled it, better you thank the coder that wrote this piece of software.
About the checkinstall question, as SD_Plissken stated (and as reported in my previous post), debian packages are well standardized, checkinstall ones are not so refined, eventhough in this particular checkinstall deb I've set all the install dependencies (thus is a bettere than average checkinstall package ;-), it lacks build ones and the comment is not well formatted (and probably there are more problems I'm not aware of! ^_^), so it's not good to put it on a public repository.

---

