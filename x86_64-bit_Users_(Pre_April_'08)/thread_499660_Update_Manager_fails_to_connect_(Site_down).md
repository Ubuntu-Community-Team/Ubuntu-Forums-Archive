---
title: "Update Manager fails to connect (Site down??)"
date: 2007-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by diddler on 2007-07-12
Well, I have looked at the other threads on this subject and I guess the servers are just down temporarily, BUT, just in case that is not so, let me state the problem for the record:

I have been using Ubuntu for several months without any problems with any update manager.

Because I have dial-up, I generally wait until I can use a friend's DSL to do any downloading or updating unless the files are very small.
Up until today, each time I connected with the Internet, the update Manager would get the latest headers.

Today, after several weeks of accumulating updates, I connected to the DSL and tried to do an update with update manager.

I get a message that the update manager:
        Failed to download the list of changes. 
        Please check your Internet connection.

All other internet based apps seem to be working, email, Firefox, and oddly enough, add/remove and synaptic.

When I try to get the updates anyway, I get the following message for each update:
        W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.2.0-1ubuntu4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.2.0-1ubuntu4_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


Like I said, hopefully this is a temporary update site problem (I will go to the Ubuntu Homepage and see if they have something there).

If the problem persists tomorrow, I will be back and this thread will be open for business.

---

### Post by djchandler on 2007-07-12
> **diddler said:**
> Well, I have looked at the other threads on this subject and I guess the servers are just down temporarily, BUT, just in case that is not so, let me state the problem for the record:

I have been using Ubuntu for several months without any problems with any update manager.

Because I have dial-up, I generally wait until I can use a friend's DSL to do any downloading or updating unless the files are very small.
Up until today, each time I connected with the Internet, the update Manager would get the latest headers.

Today, after several weeks of accumulating updates, I connected to the DSL and tried to do an update with update manager.

I get a message that the update manager:
        Failed to download the list of changes. 
        Please check your Internet connection.

All other internet based apps seem to be working, email, Firefox, and oddly enough, add/remove and synaptic.

When I try to get the updates anyway, I get the following message for each update:
        W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.2.0-1ubuntu4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.2.0-1ubuntu4_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


Like I said, hopefully this is a temporary update site problem (I will go to the Ubuntu Homepage and see if they have something there).

If the problem persists tomorrow, I will be back and this thread will be open for business.

This looks like an error in lan configuration to me. I'm sure you have re-checked everything, but look again just to be sure. I have broadband, so this is not a problem for me, so I'll check update manager for you to be sure. What part of the world are you trying to connect from?

DJ

---

### Post by djchandler on 2007-07-12
I just connected from the Kansas City area. Found 14 OpenOffice security updates I didn't know about, and I am currently downloading 60 mb.

DJ

---

### Post by diddler on 2007-07-12
> **djchandler said:**
> This looks like an error in lan configuration to me. I'm sure you have re-checked everything, but look again just to be sure. I have broadband, so this is not a problem for me, so I'll check update manager for you to be sure. What part of the world are you trying to connect from?

DJ

I am in the USA.  I have used this exact DSL connection before without any problem.  I HAD downloaded and installed Anon-proxy since the last time, but even after I uninstalled it, the problem persisted.

---

### Post by diddler on 2007-07-12
> **djchandler said:**
> I just connected from the Kansas City area. Found 14 OpenOffice security updates I didn't know about, and I am currently downloading 60 mb.

DJ

OK, I guess it is MY problem, but the question is why something that has worked perfectly and has not been (at least deliberately) changed in any way, should suddenly STOP working?

---

### Post by diddler on 2007-07-12
1

---

### Post by diddler on 2007-07-12
Never mind the never mind.  It just stopped working again.  Maybe it is a sign of the Armageddon.  After all, if Linux starts acting like Windows, that must be a sure sign of the end of the world!:mad:

---

### Post by djchandler on 2007-07-12
> **diddler said:**
> OK, I guess it is MY problem, but the question is why something that has worked perfectly and has not been (at least deliberately) changed in any way, should suddenly STOP working?

I don't know either, but I just finished a 60.3 mb download and update to OpenOffice. Are you hooking into your friends network through a switch. Sometimes switches get real picky about which port you hook into. You either need to remember where you hooked in last time, or power  down the whole backbone and restart everything on his network. Ethernet switches have memory and match MAC addresses to ports. If his whole system has been up for a long time that could be the problem. A hub won't be picky, but ethernet switches are.

DJ
:confused:

---

### Post by diddler on 2007-07-12
> **djchandler said:**
> I don't know either, but I just finished a 60.3 mb download and update to OpenOffice. Are you hooking into your friends network through a switch. Sometimes switches get real picky about which port you hook into. You either need to remember where you hooked in last time, or power  down the whole backbone and restart everything on his network. Ethernet switches have memory and match MAC addresses to ports. If his whole system has been up for a long time that could be the problem. A hub won't be picky, but ethernet switches are.

DJ
:confused:

Well, I am connecting through a Bellsouth DSL modem.  I took power off the modem and let it shut down, then repowered it and let it reset itself.  Still can get everything on the net BUT update manager.  I guess this is one of those insolvable Linux problems that only hit us non-geeks.  I think I will go home, go to bed, and come back tomorrow and assume that tonight was just a non-drug induced nightmare.

---

### Post by djchandler on 2007-07-12
> **diddler said:**
> Never mind the never mind.  It just stopped working again.  Maybe it is a sign of the Armageddon.  After all, if Linux starts acting like Windows, that must be a sure sign of the end of the world!:mad:

I sure hope you are wrong about the end of civilization.

Sometimes it seems like you just have to hold your mouth right, and there's just no explanation, Sometimes a connection, even as you check it, seems okay, but you actually did move something a micron or so that makes all the difference.

Glad you got the updates going. I can't imagine what a hassle that must be to maintain a Linux distro without broadband.

You should get extra beans just for doing things the hard way.

DJ
:guitar:

---

### Post by diddler on 2007-07-12
OK, I quit.  Went to synaptic to try and download the update manager updates and it fails to connect there also.  I have successfully downloaded OTHER synaptic packages tonight.  Screw it, its not worth the aggrevation.

---

### Post by diddler on 2007-07-12
> **djchandler said:**
> I sure hope you are wrong about the end of civilization.

Sometimes it seems like you just have to hold your mouth right, and there's just no explanation, Sometimes a connection, even as you check it, seems okay, but you actually did move something a micron or so that makes all the difference.

Glad you got the updates going. I can't imagine what a hassle that must be to maintain a Linux distro without broadband.

You should get extra beans just for doing things the hard way.

DJ
:guitar:

It is IMPOSSIBLE to maintain a LINUX distro on dial-up.  That is why I haul my computer here to do the updates.  Since this no longer seems to work, I guess I am just screwed. (Now where is that Windows XP 64 disk?)

---

### Post by djchandler on 2007-07-12
> **diddler said:**
> Well, I am connecting through a Bellsouth DSL modem.  I took power off the modem and let it shut down, then repowered it and let it reset itself.  Still can get everything on the net BUT update manager.  I guess this is one of those insolvable Linux problems that only hit us non-geeks.  I think I will go home, go to bed, and come back tomorrow and assume that tonight was just a non-drug induced nightmare.

DSL modems do go bad, and will start intermittent problems without warning. You keep looking for other problems, but nothing you have control over is wrong. If the modem is over 5 years old, make AT&T (or whoever the ISP is) do a line check for your friend. I just had to replace a 7 year old Speedstream 5260 with a new 4100 B last month. The kind of thing you were describing in the op is similar to what the old 5260 was doing.

As I recall, the first time I had problems was in the middle of running update-manager. It must be the error checking protocol is so strict that it shows weaknesses there first. When I think about it, it kind of gives me a good feeling knowing that Canonical goes to such lengths to protect its users from bad downloads.

DJ

---

### Post by diddler on 2007-07-12
OK, Thanks everybody.  Go to bed (or to work, or to school, depending on your locale).  I failed to apply the first law of computering (which I thought I had learned 20 years ago):  When all else fails, REBOOT!  I did.  Its working.  I feel such a fool.  I don't deserve to use LINUX.  I should be sentenced to a lifetime of VISTA.  Sorry to keep everybody up.  Mea Culpa, mea culpa.

---

