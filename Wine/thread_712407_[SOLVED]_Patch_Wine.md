---
title: "[SOLVED] Patch Wine?"
date: 2008-03-01
forum: Wine
---

### Post by cartisdm on 2008-03-01
I already have Wine installed (most recent version too).  I'm trying to play the game snood and someone gave me a patch to it.  How do I apply this wine patch after I've already installed wine?

I already searched around a bit but all the answers said you have to apply patches during install of wine

---

### Post by Eddie Wilson on 2008-03-02
What kind of file is the patch?

Eddie

---

### Post by pissedoffdude on 2008-03-02
You're going to have to reinstall wine from source.  Make sure that you've added the winehq repo:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get build-dep wine
sudo apt-get install fakeroot
mkdir wine1.5
cd wine1.5
apt-get source wine1.5
cd wine*
patch -p0 < /home/YOURNAME/yourpatch.patch 
dpkg-buildpackage -rfakeroot -uc -b

```
This will create your new wine deb.  Then completely remove your old wine:
```
sudo dpkg --purge wine1.5
``` 
Now you can install your patched version of wine.

---

### Post by cartisdm on 2008-03-03
> **pissedoffdude said:**
> Now you can install your patched version of wine.

I'm away from my laptop for a few days but I'll try all that soon as I get home.  This is the code I was given: 
```
--- server/queue.c.orig	2007-05-07 07:38:23.000000000 -0700
+++ server/queue.c	2007-05-07 07:44:23.000000000 -0700
@@ -1779,9 +1779,18 @@
     if (filter & QS_PAINT) queue->changed_bits &= ~QS_PAINT;
 
     /* then check for posted messages */
-    if ((filter & QS_POSTMESSAGE) &&
-        get_posted_message( queue, get_win, req->get_first, req->get_last, req->flags, reply ))
-        return;
+/*    if ((filter & QS_POSTMESSAGE) &&
+        get_posted_message( queue, get_win, req->get_first, req->get_last, req->flags, reply ))*/
+          /* but NOT any with code 0x5555 - hack to make Snood work! */
+    if ((filter & QS_POSTMESSAGE) &&((req->get_first <= 0x5555) && (0x5555 <= req->get_last)))
+    {
+       if (get_posted_message( queue, get_win, req->get_first, 0x5554, req->flags, reply ))
+            return;
+        if (get_posted_message( queue, get_win, 0x5556, req->get_last, req->flags, reply ))
+            return;
+    }
+    else if (get_posted_message( queue, get_win, req->get_first, req->get_last, req->flags, reply ))
+    return;
 
     /* only check for quit messages if not posted messages pending.
      * note: the quit message isn't filtered */
@@ -1793,6 +1802,12 @@
         filter_contains_hw_range( req->get_first, req->get_last ) &&
         get_hardware_message( current, req->hw_id, get_win, req->get_first, req->get_last, reply ))
         return;
+    /* Now check for posted messages with code 0x5555 - hack to make Snood work! */
+
+    if ((filter & QS_INPUT) &&((req->get_first <= 0x5555) && (0x5555 <= req->get_last)
+        && (get_posted_message( queue, get_win, 0x5555, 0x5555, req->flags, reply ))))
+       return;
+
 
     /* now check for WM_PAINT */
     if ((filter & QS_PAINT) &&


```

You said after those previous instructions I can now install the patch, how do I got about doing this or is it self-explanitory after I've reinstalled Wine etc.?

---

### Post by mc4man on 2008-03-03
You have to patch it (the source) first
> Now you can install your_ patched_ version of wine.
 Follow pissedoffdude's instructions exactly - excellent method - gives you a proper .deb package
Create a new text document and paste the patch text into, save and rename snoodpatch.patch  Then place the file in your home directory and follow above commands.

---

### Post by Ariccanfly on 2008-07-28
I want to do this, and I'm willing to patch WINE for the sake of snood... but the patch is for snood version 2.4.4 and the current version of snood is 3.something.  I'm pretty sure I need the old version of snood (2.4.4) so please, if anyone has that old version, post it here! :)

---

### Post by YokoZar on 2008-07-28
> **Ariccanfly said:**
> I want to do this, and I'm willing to patch WINE for the sake of snood... but the patch is for snood version 2.4.4 and the current version of snood is 3.something.  I'm pretty sure I need the old version of snood (2.4.4) so please, if anyone has that old version, post it here! :)
The patch is to Wine, so it likely works with all Snood versions.  No guarantees, but give it a try.

---

### Post by c0rdawg on 2008-11-04
Sorry to bring up an old post, but this was very helpful and allowed me to patch and build wine very easily. The only problem now is apt keeps wanting me to upgrade wine to the one in the budget dedicated repository. Is there anything special I need to do when building wine to make apt know that it is a more recent version?

---

### Post by YokoZar on 2008-11-05
> **c0rdawg said:**
> Sorry to bring up an old post, but this was very helpful and allowed me to patch and build wine very easily. The only problem now is apt keeps wanting me to upgrade wine to the one in the budget dedicated repository. Is there anything special I need to do when building wine to make apt know that it is a more recent version?
This is how apt is designed to work.  So, other than marking the package as "do not upgrade" (eg in Synaptic), no.

---

### Post by c0rdawg on 2008-11-05
Ah okay, thank you.

---

### Post by bokl on 2008-11-30
Man, I REALLY want to get Snood (v 3.52) working on Ubuntu 8.10

I have done these steps:
1. added the wine repositories
(instruction: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) )
2. saved the patch text above to snoodpatch.patch and placed it in my home directory

Now I need to do steps 3 - 5:
3. create custom wine including patch 
4. remove already installed wine
5. install custom wine from created .deb

I'm hesitant about trying the exact code for step 3 given above, since it seems suited for an older version of ubuntu. 

Can someone please give me an updated guide for steps 3-5 that works on 8.10. As basic as possible please! For example, I'm unsure on how to install from a .deb file.

---

### Post by Czechrite on 2012-12-30
> **pissedoffdude said:**
> You're going to have to reinstall wine from source.  Make sure that you've added the winehq repo:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get build-dep wine
sudo apt-get install fakeroot
mkdir wine1.5
cd wine1.5
apt-get source wine1.5
cd wine*
patch -p0 < /home/YOURNAME/yourpatch.patch 
dpkg-buildpackage -rfakeroot -uc -b

```
This will create your new wine deb.  Then completely remove your old wine:
```
sudo dpkg --purge wine1.5
``` 
Now you can install your patched version of wine.

Wow. Thank you for this great advice and information.
I am trying to patch Wine for World of Tanks.
I'm an Ubuntu user for 3 days now and I don't want to give up on it...if I can just patch WINE and get WOT going.

I'm so sick of WINDOWS I could puke...CHEERS.
Thanks again.

---

### Post by oldos2er on 2012-12-30
Closed. Please don't bump old threads.

---

