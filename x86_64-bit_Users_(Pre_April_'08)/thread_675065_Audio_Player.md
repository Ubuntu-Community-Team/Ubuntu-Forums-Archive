---
title: "Audio Player"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by balagunner on 2008-01-22
Hi
I'm facing lot of problems regarding the audio players and their installation.

I downloaded the installer of the realplayer and the hlix player

I also tried:

sudo apt-get install xmms
sudo apt-get install vlc
and stuff but its always saying saying package not found......

P.S: I also did sudo apt-get update

---

### Post by John Jason Jordan on 2008-01-22
> **balagunner said:**
> Hi
I'm facing lot of problems regarding the audio players and their installation.

I downloaded the installer of the realplayer and the hlix player

I also tried:

sudo apt-get install xmms
sudo apt-get install vlc
and stuff but its always saying saying package not found......

P.S: I also did sudo apt-get update
If packages are not found that others seem to have no problem installing it is probably because you have not enabled all the repositories. This is especially true for proprietary stuff like RealPlayer. A standard Ubuntu install does not enable the repositories for proprietary and restricted software. 

Go into System > Administration > Software Sources and enable everything. When you close the window it will prompt you to update your repository list. Clicking OK will update the list - which does the same as "sudo apt-get update." Afterwards apt-get should find the packages. 

Having said that, I'm not sure if RealPlayer is in the repositories. Search the forums for RealPlayer because there has been a lot of discussion on how to install it.

---

### Post by XplOzIOn on 2008-01-22
Hi there!,

Have you enabled "ALL" the repositories?? If not Check this Link:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories")


EDIT: :( JJ Jordan post show after i posted mine. Well lets hope it helps!

---

### Post by luisromangz on 2008-01-22
Try enabling the universe repositories, if you haven't enabled them previously.

---

