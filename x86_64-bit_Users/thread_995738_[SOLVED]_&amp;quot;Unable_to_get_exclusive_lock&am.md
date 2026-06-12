---
title: "[SOLVED] &amp;quot;Unable to get exclusive lock&amp;quot;"
date: 2008-11-28
forum: x86 64-bit Users
---

### Post by AdamantLobster on 2008-11-28
_Newby needs help._:confused:

When I try running the Synaptic Package manager and/or the add/remove programs I keep getting this error-

[B]Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.[/B]

How do I close this application?

The problem started when I installed DVD codecs to enable DVD playback on my system from an installer program that my friend had built.

If anyone could please explain to me why this is happening and how to fix it in the most laymen of terms and instruction, I would be most appreciative.

I am familiar with the terminal on a very minimum basis. I can use it when instructed well.


System specs:

AMD Athlon 64 Processor 3800+
3GiB RAM
NVidia GForce 7800GT
Asus A8N5X Motherboard

O.S. specs:

Ubuntu 8.10 64bit

---

### Post by Kevbert on 2008-11-28
Please use the following in terminal and report back the error:
```
sudo apt-get update
```

---

### Post by philinux on 2008-11-28
The error message means that more than one package manager is running. You can only have have one running at a time. So if you've got add/remove open then open synaptic and try to do anything the error will pop up. So close one or other. 

Logging out then logging back in will clear the system as will rebooting should there be a package process running that you cant see.

You can check by looking at the system monitor process tab. Look for apt processes.

---

### Post by AdamantLobster on 2008-11-28
> **Kevbert said:**
> Please use the following in terminal and report back the error:
```
sudo apt-get update
```

The full version error code-
[B]
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

---

### Post by AdamantLobster on 2008-11-28
> **philinux said:**
> The error message means that more than one package manager is running. You can only have have one running at a time. So if you've got add/remove open then open synaptic and try to do anything the error will pop up. So close one or other. 

Logging out then logging back in will clear the system as will rebooting should there be a package process running that you cant see.

You can check by looking at the system monitor process tab. Look for apt processes.

I did not open them at the same time and I already checked the system monitor for active processes, also when I did logout and also reboot all I got was no pubkey error.

---

### Post by Kevbert on 2008-11-28
See if this helps in terminal:
```
sudo wget -q http://fr.packages.medibuntu.org/medibuntu-key.gpg -O- | sudo
apt-key add - 
sudo apt-get update
```
Just copy using Ctrl-C from here, each line, and paste in terminal using Ctrl-Shift-V.

---

### Post by AdamantLobster on 2008-11-28
> **Kevbert said:**
> See if this helps in terminal:
```
sudo wget -q http://fr.packages.medibuntu.org/medibuntu-key.gpg -O- | sudo
apt-key add - 
sudo apt-get update
```
Just copy using Ctrl-C from here, each line, and paste in terminal using Ctrl-Shift-V.

I gave me this:

**W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783**

---

### Post by philinux on 2008-11-28
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

From medibuntu click the link below for more info.

---

### Post by AdamantLobster on 2008-11-28
> **philinux said:**
> ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

From medibuntu click the link below for more info.

**Awesome**, thank you very much. That's the answer I have been waiting for.:guitar:

---

### Post by mcrene on 2009-01-10
I have been having much the same problem, error code and so on.

when I tried that final sudo that worked for Lobster, this is what I got
"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

this is directly after a reboot. any other ideas?

---

### Post by mcrene on 2009-01-10
some help?

---

