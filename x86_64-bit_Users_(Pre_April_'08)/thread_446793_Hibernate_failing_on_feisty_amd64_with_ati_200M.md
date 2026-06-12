---
title: "Hibernate failing on feisty amd64 with ati 200M"
date: 2007-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by renraw on 2007-05-17
Hello readers,

I am rather new to linux and ubuntu, and I ran into an issue with my laptop. The laptop is a AMD Turion 64 bit with a ATI Xpress 200M chipset and running ubuntu feisty fawn with xfce.

The issue is that when I use the ubuntu shutdown menu and select hibernate, my  screen goes black for about a second and then returns to the desktop with all programs still running. When trying to get the laptop to go to sleep, there is no reaction of the system whatsoever.

I have tried to search the net on this and have found some suggestions, however none seem to work. Is there anyone here who could point me to some other solutions or just tell me that is not possible with ati at all :confused:.

Thanks

Warner

PS: Just attached a file containing some parts of my logs. Hope they help.

---

### Post by zhinker on 2007-05-17
I was having the same problem, then yesterday I was just browsing through some of the packages in synaptic and I found one called 'hibernate'...you can guess what happened after that :)

After finding that I tried to see if I could find a package to fix my other problem: my shutdown button is missing in the shutdown menu!  I found a package called 'wmshutdown' but it didn't do anything.

(btw, if the hibernate package doesn't do the trick by itself, try installing the wmshutdown package as well, I installed both of them at the same time so I'm not sure if hibernate did the job alone.)

--Alright!  Looks like my time to start giving back to the Ubuntu community has begun :D (assuming this works...)

---

### Post by ububuL on 2007-05-18
> **zhinker said:**
> I was having the same problem, then yesterday I was just browsing through some of the packages in synaptic and I found one called 'hibernate'...you can guess what happened after that :)

After finding that I tried to see if I could find a package to fix my other problem: my shutdown button is missing in the shutdown menu!  I found a package called 'wmshutdown' but it didn't do anything.

(btw, if the hibernate package doesn't do the trick by itself, try installing the wmshutdown package as well, I installed both of them at the same time so I'm not sure if hibernate did the job alone.)

--Alright!  Looks like my time to start giving back to the Ubuntu community has begun :D (assuming this works...)

I installed both packages. They didn't fix my problem. I am not sure what else I am missing.

---

### Post by renraw on 2007-05-18
> **zhinker said:**
> I was having the same problem, then yesterday I was just browsing through some of the packages in synaptic and I found one called 'hibernate'...you can guess what happened after that :)

After finding that I tried to see if I could find a package to fix my other problem: my shutdown button is missing in the shutdown menu!  I found a package called 'wmshutdown' but it didn't do anything.

(btw, if the hibernate package doesn't do the trick by itself, try installing the wmshutdown package as well, I installed both of them at the same time so I'm not sure if hibernate did the job alone.)

--Alright!  Looks like my time to start giving back to the Ubuntu community has begun :D (assuming this works...)

Thanks for the sugestion, I had a look at hibernate before but then it did not work, this time I know how to get some more info from the man pages. This page mentions that hibernate is a script which uses uswsusp. Trying "sudo dpkg-reconfigure uswsusp" resulted in a message saying that my swap file was not active.

After resolving the swap issue with editing the /etc/fstab and replacing the UUID codes with /dev/hda3 (swap partition) I ran hibernate again. The result is still the same, however I found another log file /var/log/hibernate.log which I have appended to this post.

Could someone review it please?

Warner

---

### Post by renraw on 2007-05-18
Oke, I have got the hibernate package to work. I restated my laptop and found out that there is something wrong with my swap configuration, it mentioned a noauto in the /etc/fstab file. After I removed it and tested hibernate from a terminal, it worked.

However if I try to use the exit menu from xubuntu it gives me several options (switch user, logoff, restart, shutdown, suspend and hibernate), when the hibernate option is selected, nothing happens for 5 seconds, then an information popup appears saying: "Swap partition '3:9' is not available, cannot suspend to disk".

I am still trying to figure out how this works, so if anyone has any suggestion on this it will be much appriciated.

Warner

---

### Post by ububuL on 2007-05-18
> **renraw said:**
> Oke, I have got the hibernate package to work. I restated my laptop and found out that there is something wrong with my swap configuration, it mentioned a noauto in the /etc/fstab file. After I removed it and tested hibernate from a terminal, it worked.

However if I try to use the exit menu from xubuntu it gives me several options (switch user, logoff, restart, shutdown, suspend and hibernate), when the hibernate option is selected, nothing happens for 5 seconds, then an information popup appears saying: "Swap partition '3:9' is not available, cannot suspend to disk".

I am still trying to figure out how this works, so if anyone has any suggestion on this it will be much appriciated.

Warner

I am using Gnome, with both hibernate & uswsusp installed, now hibernate works for me. Hopefully, you can find your solution. Thanks.

---

### Post by ububuL on 2007-05-18
> **ububuL said:**
> I am using Gnome, with both hibernate & uswsusp installed, now hibernate works for me. Hopefully, you can find your solution. Thanks.
Actually, hibernate only works for me on command line. I tried to click Hibernate from the exit menu, after 30 secs or so, the log in prompt shown up for me to log back in gnome. I didn't see any error messages.

---

### Post by dresnu on 2007-05-21
> **ububuL said:**
> Actually, hibernate only works for me on command line. I tried to click Hibernate from the exit menu, after 30 secs or so, the log in prompt shown up for me to log back in gnome. I didn't see any error messages.

What command are you issuing in the terminal? "hibernate" or "s2disk" (which is the direct uswsup command)?

---

### Post by ububuL on 2007-05-22
> **dresnu said:**
> What command are you issuing in the terminal? "hibernate" or "s2disk" (which is the direct uswsup command)?
```
$sudo hibernate
```

---

### Post by dresnu on 2007-05-22
Ok try s2disk then. Just type "sudo s2disk".

Check if it works. If that resolves the problem hibernate script can be changed to use that command instead.

---

