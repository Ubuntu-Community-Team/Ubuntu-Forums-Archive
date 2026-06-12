---
title: "GAH! *rips hair out* keyboard mapping problems"
date: 2006-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by weird_c00kie on 2006-10-25
i successfully installed beryl today on my amd64 and everything has been absolutely perfect.... EXCEPT ONE THING!

eversince i installed it, pressing shift+backspace results in X resetting the same way it does when you do ctrl+alt+backspace!

so say i'm pressing shift to write in caps, right? and i make a mistake, so i want to delete it. the moment i touch backspace, it resets, and i lose everything... it's happened so many times already today that it really isn't funny

in the last 10 minutes i lost a post 4 times in another forum and had to rewrite this one 2 times, assuming i don't accidentally press it again.
it's driving me crazy


is there ANY way to view (and alter) keyboard shortcuts like that? please help if you can before i throw myself out the window or something.... or reset again and lose this post which i almost just did twice before finishing this sentence....


please help if you can!

---

### Post by _simon_ on 2006-10-25
stick this in an executable file in /usr/local/bin then place it in session startup

```

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

```

That will stop shift + backpace from restarting.

---

### Post by weird_c00kie on 2006-10-25
wow, thanks for the super-fast response

i have a question though... being very much still a n00b.... how do i make an executable? secondly, the /usr/ dir is one of the locked ones, right?
so i'd need to use sudo somewhere in the terminal to create and edit the file, wouldn't i?

sorry to impose a request for extra help, but there's still so much to learn hehe


by the way, would it be possible to set up Beryl so it boots up using a script like that as well? because right now i have to type /usr/bin/beryl-manager into the terminal everytime i restart in order to get it running

---

### Post by po0f on 2006-10-25
weird_c00kie,

Navigate to System->Preferences->Sessions and click on the Start Programs tab.  Add beryl-manager to the programs that are already starting when you log in.  Fire up gedit with root privileges:
```
$ gksu gedit /usr/local/bin/fix_backspace
```
Enter in what _simon_ posted.  Now make it executable:
```
$ sudo chmod a+x /usr/loca/bin/fix_backspace
```
chmod changes the permissions of files, and a+x sets the e**x**ecutable bit for **a**ll users.  Now add that to Startup Programs as well.

---

### Post by weird_c00kie on 2006-10-25
thanks for that po0f. something weird happens though

i added both of them to the startup list, but when i closed the list and logged out and back in again, nothing happened
so i looked at the list again, and the entries i'd made were gone!

---

### Post by po0f on 2006-10-25
weird_c00kie,

I don't know what that problem could be, is gnome-settings-daemon running?

Anyway, I was thinking of an easier way to run beryl-manager and the xmodmap command all-in-one.  Open up gedit as a root user and enter the following:
```
$ gksu gedit /usr/local/bin/beryl-startup.sh
```
```
#!/bin/bash
# Start up beryl and change the behavior of Shift+Backspace
/usr/bin/beryl-manager
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```

---

### Post by weird_c00kie on 2006-10-25
> **po0f said:**
> weird_c00kie,

I don't know what that problem could be, is gnome-settings-daemon running?

it's there in the System Monitor under Processes. says it's "sleeping"

> **po0f said:**
> 
Anyway, I was thinking of an easier way to run beryl-manager and the xmodmap command all-in-one.  Open up gedit as a root user and enter the following:
```
$ gksu gedit /usr/local/bin/beryl-startup.sh
```
```
#!/bin/bash
# Start up beryl and change the behavior of Shift+Backspace
/usr/bin/beryl-manager
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```
how do i get the sh file to execute at startup?
*tries adding it to startup programs*


---- edit ----

dang, anything i add to startup programs gets removed as soon as i close the window :(

---

### Post by weird_c00kie on 2006-10-25
by the way, thanks for all the attempts to help already. it's really appreciated :)

---

### Post by po0f on 2006-10-25
weird_c00kie,

When you log in, what session is chosen as the default?

---

### Post by weird_c00kie on 2006-10-25
ummm... the default one? heheh
i didn't tamper with that at all, so it should be whatever the default is... whatever that may be

sorry i'm not being very helpful :/


--- edit ---

i logged out to check what it's set to. it's just set to boot into the last used session, whatever that may be

---

### Post by Henry Rayker on 2006-10-25
I had the same problem where I couldn't change my startup programs. I don't know what was wrong with it, and ended up giving in and doing a full reinstallation (to try to reproduce it). I couldn't find any help, and I couldn't reproduce it on my reinstallation.

---

### Post by weird_c00kie on 2006-10-25
eek.... you mean reinstall ubuntu for the 6th time in one month? that's a bit more than i could handle, i'm afraid heheh hopefully there'll be a simpler answer hehehe

---

### Post by po0f on 2006-10-25
weird_c00kie,

I guess you could try making a new sesion to load.  Navigate to System->Preferences->Sessions and create a new session.  Make sure beryl-manager is started and that you have run the xmodmap command.  Just save your session, log out and log back in using the previously used session.  Hope this works for you.

---

### Post by weird_c00kie on 2006-10-26
hmm, i wish i knew how to make a new session and have it work :p

i tried creating a new session in the System > Preferences > Sessions window, but when i booted into it, i couldn't even right-click the desktop. and i still couldn't add any new items to the start-up programs list

is it just me, or have i managed to run into one of those bizarre-and-annoying-but-too-small-to-spend-too-much-time-figuring-out bugs?

---

