---
title: "Medibuntu Repo problem"
date: 2008-10-28
forum: x86 64-bit Users
---

### Post by Terry S on 2008-10-28
I have just added the Medibuntu repros 
[HTTP://packages.medibuntu.org/hardy](HTTP://packages.medibuntu.org/hardy) free non-free
[HTTP://packages.medibuntu.org/hardyfree](HTTP://packages.medibuntu.org/hardyfree) non-free (source Code)

When I reload I get the following message

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Can anyone please tell me what I have done wrong and how to fix it?

I am running Ubuntu Hardy AMD64

Thanks

---

### Post by NilsE on 2008-10-28
I just ran into the same problem on Intrepid

Try this page to help install the new repo and keys.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

First remove it in software sources

---

### Post by JoseReyes on 2008-10-28
> **NilsE said:**
> I just ran into the same problem on Intrepid

Try this page to help install the new repo and keys.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

First remove it in software sources


I was having the same problem. I tried several suggestions from whithin the forum but would not work. I went to this location on the forum and added the key as per the multimedia setup and worked perfect hope this helps..

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by _sAm_ on 2008-10-29
Same happen with me, but one hour later it worked. So perhaps you can try again and see if it works now.

---

### Post by jespdj on 2008-10-29
Did you follow all the instructions in the [howto](https://help.ubuntu.com/community/Medibuntu)? After adding the repository, you should do:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
as the howto says.

---

### Post by philinux on 2008-10-29
I've notice the last 2 weeks that the medibuntu repos have either been down or very slow.

It's just a case of try again later. :rolleyes:

---

### Post by Terry S on 2008-10-29
> **jespdj said:**
> Did you follow all the instructions in the [howto](https://help.ubuntu.com/community/Medibuntu)? After adding the repository, you should do:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
as the howto says.

Hi jespdj

I followed the 'How To' by cutting and pasting the code instructions but to be sure I input your code anyway and this is the message I got after reload.


W: Bizarre Error - File size is not what the server reported 0 3445


So something changed but what I haven't a clue can you help?

---

### Post by Terry S on 2008-10-29
Thanks to all who responded to my post. The problem was solved by going back to the site recommended by NilsE and after uninstalling the Medibuntu repros I then reinstalled and all is now as it should be.

Thanks again.

---

### Post by jespdj on 2008-10-29
> **Terry S said:**
> W: Bizarre Error - File size is not what the server reported 0 3445
That kind of error sounds like Internet connection problems with the website, as other people have already noted. So it's most likely a problem at Medibuntu, you'll just have to wait until they fix their connection problems.

---

