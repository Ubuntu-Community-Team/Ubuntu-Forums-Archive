---
title: "Getting the Fingerprint reader working in Ubuntu"
date: 2008-06-07
forum: x86 64-bit Users
---

### Post by mbach_007 on 2008-06-07
I have a HP dv9700t laptop with a AES2501A fingerprint reader.  Can anybody help.

Thanks 

Matt

---

### Post by Prometheum on 2008-06-07
There's a thread you can get to by searching dv9000 on these forums that details how to get it working. The driver for AES2501 is in the repos, after that, you need to install libfprint and pam_fprint for support.

However, it isn't very useful: pam_fprint isn't very stable, so you shouldn't risk locking yourself out of your system just yet.

---

### Post by mbach_007 on 2008-06-07
I found the driver script and it seemed to have installed.  Now I need the software to run it.

---

### Post by Unix_Slayer on 2008-06-07
[http://www.softexinc.com/product.asp?product=omnipass3]("http://www.softexinc.com/product.asp?product=omnipass3")

I use OmniPass. You have to order special for Linux program, and drivers. But i'm not sure which chip you are running in there. Check on their page to see which chips work. I know, it's not free... but it works.

---

### Post by jblackthorne on 2008-06-08
Personally, I have had pretty good luck using the fprint products.  I agree that it is a good idea to keep password authentication enabled along with fprint.  However, even in alpha state, the fprint project works really well on three new HP laptops (HP dv6700, HP dv2700, and my friends HP dv9000 series) (all used with gutsy and hardy).

If you are interested in trying out the open source alternative, it is very easy to install now too.  Just add this to your sources:

deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse

The official project page is here:
[http://www.reactivated.net/fprint/wiki/Main_Page](http://www.reactivated.net/fprint/wiki/Main_Page)

Additional notes can be found here:
[http://legacy.madman2k.net/comments/105](http://legacy.madman2k.net/comments/105)

---

### Post by Unix_Slayer on 2008-06-08
> **jblackthorne said:**
> Personally, I have had pretty good luck using the fprint products.  I agree that it is a good idea to keep password authentication enabled along with fprint.  However, even in alpha state, the fprint project works really well on three new HP laptops (HP dv6700, HP dv2700, and my friends HP dv9000 series) (all used with gutsy and hardy).

If you are interested in trying out the open source alternative, it is very easy to install now too.  Just add this to your sources:

deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse

The official project page is here:
[http://www.reactivated.net/fprint/wiki/Main_Page](http://www.reactivated.net/fprint/wiki/Main_Page)

Additional notes can be found here:
[http://legacy.madman2k.net/comments/105](http://legacy.madman2k.net/comments/105)

I seem to be having a problem installing the drivers for fprint. I am using an Authentec chip in mine, but the debian installation fails. Do you know of a source file for the drivers that I could configure? The source you gave above only updates the fprint program.

---

### Post by jblackthorne on 2008-06-09
> **Unix_Slayer said:**
> I seem to be having a problem installing the drivers for fprint. I am using an Authentec chip in mine, but the debian installation fails. Do you know of a source file for the drivers that I could configure? The source you gave above only updates the fprint program.

No, that source link gives access to all 3 fprint libs.

* fprint-demo (the main program for enrolling and verify for now)
* libfprint0 (required library)
* libpam-fprint

I used that very same source link on my laptops.  It installed fprint-demo version 0.4, libfprint ver 0.9.5-2, and libpam-fprint 0.2-2. Make sure you correctly add the source string:

1. Click System\Administration\Software Sources
2. Click the Third-party Software tab
3. Click Add
4. Paste the string exactly as the next line:

deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse

5. When the popup asks to refresh sources, choose "Yes"
6. Open Synaptic (or use sudo apt-get) and install all 3 libs.

That should work.  Good luck

Edited to add: I have Authentec chips as well.  There is no required "driver" for this fingerprint reader chipset.  If I understand correctly, libfprint accesses the reader through the standard interface (TWAIN perhaps?).

---

### Post by Unix_Slayer on 2008-06-09
> **jblackthorne said:**
> No, that source link gives access to all 3 fprint libs.

* fprint-demo (the main program for enrolling and verify for now)
* libfprint0 (required library)
* libpam-fprint

I used that very same source link on my laptops.  It installed fprint-demo version 0.4, libfprint ver 0.9.5-2, and libpam-fprint 0.2-2. Make sure you correctly add the source string:

1. Click System\Administration\Software Sources
2. Click the Third-party Software tab
3. Click Add
4. Paste the string exactly as the next line:

deb [http://ppa.launchpad.net/madman2k/ubuntu](http://ppa.launchpad.net/madman2k/ubuntu) hardy main restricted universe multiverse

5. When the popup asks to refresh sources, choose "Yes"
6. Open Synaptic (or use sudo apt-get) and install all 3 libs.

That should work.  Good luck

Edited to add: I have Authentec chips as well.  There is no required "driver" for this fingerprint reader chipset.  If I understand correctly, libfprint accesses the reader through the standard interface (TWAIN perhaps?).

[B]It's in my third party add-on.

This is what I get.[/B]

[IMG]http://mysite.verizon.net/mgm_mgm/fprint1.jpg[/IMG]

**Then**

[IMG]http://mysite.verizon.net/mgm_mgm/fprint2.jpg[/IMG]

---

