---
title: "Add/Remove Applications"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by d7aug9 on 2008-06-21
I tried to use the Add/Remove Applications tool but when I click the checkbox I get a message, "The list of applications is not availabe Click on 'Reload to load it. To reload the list you need a working internet connection".  When I click 'Refresh' (there is no 'Reload') I get a brief dialog titled "Downloading Package Information", then a quick dialog with a progress bar in it (no title, I think, though it disappears before I am really able to read anything) and then nothing.  Apparently nothing has changed because clicking on the checkbox again gives me the same results.  The dialogs that pop up once I click 'Refresh' disappear so quickly I can't even tell what it's trying to do.  I have no idea how to make the list available, other than by clicking on the 'Refresh' button.  Does anyone know what this application is trying to do?

Thanks

Supporting info:
Ubuntu 7.10 Gutsy Gibbon
I have a working internet connection (I'm using it right now to access this forum).

---

### Post by pixel :-) on 2008-06-21
like it said,it downloads information about available pakages.

The stuff that where to fast to read, was simply the files that it was downloading,it's not important.

Actually i'm on kde, what check box do you mean?Give a screenshot.

---

### Post by d7aug9 on 2008-06-21
How do I do a get a screen shot?

---

### Post by pixel :-) on 2008-06-21
you just check,what you whant and then ok.It's not the same aplication as the screenshot?
[http://svn.opensuse.org/svn/yast/tags/stable-2_16_9/gtk/mockups/package-selector/ubuntu-add-remove-applications.jpg]("http://svn.opensuse.org/svn/yast/tags/stable-2_16_9/gtk/mockups/package-selector/ubuntu-add-remove-applications.jpg")

close it:
in a terminal
sudo apt-get update //give me the output

sudo apt-get -s yourpakage  //yourpakage the name of the pakage,if you don't know the real name of the pakage just tell me what it's name in the program, this is a simulation, give me it's out put.

this is strange ,it should be straight forward installation with this,are you sure you haven't played with some other stuff.Have you given it your password?Are there other pakage managers active?

---

### Post by d7aug9 on 2008-06-21
That (the screenshot) is the right app.

I figured out how to do get a screenshot and I think I managed to attach the results.  I was able to capture the error and the "Downloading Package Information" dialogs, but not the one afterwards.  Here are the results you asked for:

d7aug9@PipeOrgan:~$ sudo apt-get update
[sudo] password for d7aug9:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done

and...

d7aug9@PipeOrgan:~$ sudo apt-get -s emacs22
E: Invalid operation emacs22


I agree that its weird, but I've never used it before.  This is a relatively fresh installation and I haven't played around with anything.  I did try to install from the terminal (sudo apt-get install emacs22) with no success:

d7aug9@PipeOrgan:~$ sudo apt-get install emacs22
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emacs22

Thanks for the quick responses!

---

### Post by d7aug9 on 2008-06-21
I also managed to capture the third dialog, though it doesn't seem to throw much light onto the situation

---

### Post by pixel :-) on 2008-06-21
apparently the repositories aren't configured,only the cd is present,you mist a step during installation apparently.Here how to add repositories.

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-a86dddc6826cec4a3847d8441b24051d07b8dc64]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-a86dddc6826cec4a3847d8441b24051d07b8dc64")

You just need to check all except the backports.

If your source list is empty,here mine. Thies are the mirors for belgium,you have to edit it to corespond to where you live,or it will download from belgium,use this link to edit my example(replace be.archive.ubuntu.com by the server near you),if you are unsure tell me where you live,i'll edit it for you[https://launchpad.net/ubuntu/+archivemirrors]("https://launchpad.net/ubuntu/+archivemirrors").
Add this in 
/etc/apt/sources.list,"gksudo gedit /etc/apt/sources.list" don't delete the cd repositories, and then "sudo apt-get update"

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) gutsy partner

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security multiverse

###################################################

# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

---

### Post by d7aug9 on 2008-07-04
Configuring the repositories worked.  Is it possible that they didn't get configured because I didn't have a working network connection during installation?

---

### Post by Kevbert on 2008-07-04
> **d7aug9 said:**
> Configuring the repositories worked.  Is it possible that they didn't get configured because I didn't have a working network connection during installation?
That's correct.  I generated a bug report on this on Gutsy a while ago suggesting that updates and security settings in particular were enabled by default - still waiting for a response.

---

