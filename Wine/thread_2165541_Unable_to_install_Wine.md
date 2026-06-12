---
title: "Unable to install Wine"
date: 2013-08-05
forum: Wine
---

### Post by Haroon_Gilani on 2013-08-05
Hi all i am using ubuntu 13.10 alpha 2 and i am trying to install wine but when i am downloading via terminal it gives me unmet dependencies error see below 


haroon@haroon-Hackerz-Domain:~$ su
Password: 
root@haroon-Hackerz-Domain:/home/haroon# apt-get install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-amd64 (= 1.6-0ubuntu1~ppa1) but it is not going to be installed
           Depends: wine1.6-i386 (= 1.6-0ubuntu1~ppa1)
E: Unable to correct problems, you have held broken packages.







Everytime i try to install the same error any advice   :confused: 


i need to play gta san andreas extreme edition plz help me

---

### Post by GwL3eNC on 2013-08-05
Hi,

have you tried

sudo apt-get -f install

to solve the depends.

---

### Post by Haroon_Gilani on 2013-08-05
Yes but to no avail

---

### Post by GwL3eNC on 2013-08-05
What if i say to you:

Try rebooting or reinstalling ubuntu on ur pc if the probel persists 
If not go to higher mods. I think you know what i mean.

Check your reposietories if there is a older wine ppa present. If so, delete that.
If not i would try

sudo apt-get update -f
and
sudo apt-get uprage -f

Also you can try a sudo apt-get dist-upgrade to try solve the depends.

If all wont work, i dont know further and hope that you are not forced to your
given solution.

---

### Post by Haroon_Gilani on 2013-08-05
Thnx dude the last coomand about distro upgrade should solve it thanx again 

i didn't mean to show disrespect before just wanted to help and get 25 posts 

only reason 

sorry again 

and thnx again

would try the command after 3 :00 clock cuz the internet gets a lot faster after that time 


Thnx again keep :guitar:




PS i am 13 using 13.10 alpha 2 had lot of problems with unity and gnome now safe via installing lubuntu-desktop using terminal 

sorry for any inconvienience

---

### Post by GwL3eNC on 2013-08-05
It's ok man!

Keep working hard, never stop learning and you can have more than the 25 posts you target!

Please mark your thread as solved.

---

