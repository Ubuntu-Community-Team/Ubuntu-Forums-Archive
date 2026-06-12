---
title: "Can I install gnome desktop on kubuntu 64??"
date: 2006-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by bobbymcsteels on 2006-01-29
Like the title says can I install gnome desktop on my kubuntu-amd64 breezy 5.10??
If so how??
Cheers

---

### Post by christhemonkey on 2006-01-29
i think if you search in synaptic and select gnome-session
and gnome-bar (or something like that!) it should select all the gnome dependencies that you need.

---

### Post by bobbymcsteels on 2006-01-29
kubuntu hasnt got synaptic and I cant apt it.... any other way round it??

---

### Post by varunus on 2006-01-29
You need to open up Adept, in K->System->Adept.  Then enter your password when asked.

After that, install the package "ubuntu-desktop"; this is a complete Ubuntu GNOME.  (Similarly, you could install kubuntu-desktop to get a complete Kubuntu KDE.)

---

### Post by mostwanted on 2006-01-29
[QUOTE=bobbymcsteels]kubuntu hasnt got synaptic and I cant apt it.... any other way round it??[/QUOTE]

The use Kynaptic or Adept instead. Why can't you use apt-get if I may be so bold?

---

### Post by bobbymcsteels on 2006-01-29
Have tried apt-get but didnt work.... not sure if my repos are correct to be honest, been trying to apt-get stuff and they appear not to be in the repos when I'm pretty sure they should be.

Have looked in adept but can only find kubuntu-standard nothing else there matching or similar:neutral:

---

### Post by christhemonkey on 2006-01-29
sudo apt-get ubuntu-desktop
should work

---

### Post by bobbymcsteels on 2006-01-29
```
root@ubuntu:/home/mcsteels# apt-get ubuntu-desktop
E: Invalid operation ubuntu-desktop

```

can someone please paste their repos for me to copy as I think mine are buggered.
Cheers

---

### Post by christhemonkey on 2006-01-29
sorry apt-get install ubuntu-desktop
My bad!

---

### Post by thepocketdrummer on 2006-01-29
How do you switch between KDE and gnome once you've done that? I'm installing gnome on Kubuntu as we speak.

---

### Post by christhemonkey on 2006-01-30
on the logon screen, press F10 go down to sessions, should be one for;
GNOME session.
I think anyway, never usud kubuntu!

---

### Post by thepocketdrummer on 2006-01-30
I installed both, but I have to say... gnome is very ugly compared to KDE. I like KDE much better.

Anyone know how to make the KDE desktop the default again? When I installed gnome-desktop, it made gnome default. [-(

---

### Post by bobbymcsteels on 2006-01-30
Gnome I found needs a lot of work to make it look nice...... KDE is very childish looking.

---

### Post by christhemonkey on 2006-01-30
To make KDE the default (i assume) , just do what you did to change into gnome ( by pressing F10 at login screen and selecting sessions) and then select kde.

It should then ask whether you would like to use it as default, say yes if you want it!

---

### Post by thepocketdrummer on 2006-01-31
It doesn't ask.

:cry:

---

### Post by bobbymcsteels on 2006-02-01
log out of kde(kubunbtu) then at the bottom of the login page it says sessions, click gnome then login as normal....

BTW installed gnome on my system now.... had lots of problems with my repos, they werent doin what they were meant to be doin... but semi-sorted now

---

### Post by bobbymcsteels on 2006-02-01
ok I have got gnome.... but how does gnome connect to the repos.... repos are found under /etc/apt/sources.list


But with kubuntu and ubuntu normally run off different repos... only slightly so where does gnome get its repos from??

---

### Post by varunus on 2006-02-06
Actually, the repos are the same, except for some kubuntu upgrades that they like to add when new KDE software comes out.

---

