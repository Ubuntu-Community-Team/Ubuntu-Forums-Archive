---
title: "sources.list error??Failed to check for installed and available applications??"
date: 2009-07-24
forum: x86 64-bit Users
---

### Post by kouchris on 2009-07-24
Reading package lists... Error!                            
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened

i am getting this error when i try to  $sudo apt-get update.
i also cant get add/remove to load anything.
i think it has something to do with my sources.list.

i read in a forum that this command might help me : ~$ sudo apt-get update -o APT::Cache-Limit=25165824
it didnt cause i think that it has to do with a bug in i386.


i have tryied :
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade
sudo atp-get dist-upgrade

same error comes up.

i have once edited my sources.list but got it back the way it was i think.
i am also posting my sources.list just to be sure.

> # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted 
#Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu) jaunty main

i am sooo desparete.. google doesnt help at all..
am i the only one ?
thnx for the help !

my update manager doesnt work also.
same error.

---

### Post by oldos2er on 2009-07-25
Have you tried different servers?

---

### Post by kouchris on 2009-07-25
it worked just fine before.. could it be a sudden server problem?
well if it is.. where do i find other servers? is there an administrative setting i should change. or i ll have to do it manually?



> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

thats the messege i get from the update manager.
hope this helps.

---

### Post by wojox on 2009-07-25
Go to System > Administration > Software Sources

Then the first tab Ubuntu Software

Pick the Download from:

and find a mirror closer to you.

---

### Post by poptart_85 on 2009-07-25
Im a Newbie to ubuntu hardy, when i go to my package manager i get this error.

E: Type '--11:59:50--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

the goal was to get wine so that i can play The sims complete collection.
need help dont know what to do i also get error signs on software source

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

need some big help thank u

---

### Post by oldos2er on 2009-07-25
You can either edit your winehq.list by running **gksu gedit /etc/apt/sources.list.d/winehq.list **and comment out the first line,or run **cat /etc/apt/sources.list.d/winehq.list** , post the output here, and wait for further help.

---

### Post by poptart_85 on 2009-07-25
well how do i edit it and onces i've edit it how to i change it so it can read that source.list



> **oldos2er said:**
> You can either edit your winehq.list by running **gksu gedit /etc/apt/sources.list.d/winehq.list **and comment out the first line,or run **cat /etc/apt/sources.list.d/winehq.list** , post the output here, and wait for further help.

---

### Post by kouchris on 2009-07-26
> **wojox said:**
> Go to System > Administration > Software Sources

Then the first tab Ubuntu Software

Pick the Download from:

and find a mirror closer to you.

changing the server didnt help at all same message in the update manager.
when i changed the server it downloaded some packages and then there was this error:

> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

any other ideas?

Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages

why does this error come up ?:confused:

---

### Post by oldos2er on 2009-07-26
> **poptart_85 said:**
> well how do i edit it and onces i've edit it how to i change it so it can read that source.list

 Run the command I gave in a terminal. To edit:
```
gksu gedit /etc/apt/sources.list.d/winehq.list
```
Remove the text that's causing the problem ('--11:59:50--'). Save and exit, then run
```
sudo apt-get update
```

---

### Post by oldos2er on 2009-07-26
> **kouchris said:**
> changing the server didnt help at all same message in the update manager.
when i changed the server it downloaded some packages and then there was this error:



any other ideas?

Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages

why does this error come up ?:confused:

 Found this possible solution through google:```
sudo rm /var/lib/apt/lists/* -vf
``````
sudo apt-get update
```

---

### Post by poptart_85 on 2009-07-26
> **oldos2er said:**
> Run the command I gave in a terminal. To edit:
```
gksu gedit /etc/apt/sources.list.d/winehq.list
```Remove the text that's causing the problem ('--11:59:50--'). Save and exit, then run
```
sudo apt-get update
```


Thank You oldos2er it worked perfectly i pretty much deleted everthing that was in the sources.list then i update and now my package manager works again well at least i can get in now..

---

### Post by kouchris on 2009-07-26
> **oldos2er said:**
> Found this possible solution through google:```
sudo rm /var/lib/apt/lists/* -vf
``````
sudo apt-get update
```
you re my savior!
thnx so much for taking the time...
i ve searched google as well but..keywords keywords keywords!
cheers!

---

