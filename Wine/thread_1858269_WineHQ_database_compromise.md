---
title: "WineHQ database compromise"
date: 2011-10-12
forum: Wine
---

### Post by ergo-proxy on 2011-10-12
In case someone didn't get it:

> Hi,  I am sad to say that there was a compromise of the WineHQ database system.

 What we know at this point that someone was able to obtain unauthorized access to the phpmyadmin utility.  We do not exactly how they obtained access; it was either by compromising an admins credentials, or by exploiting an unpatched vulnerability in phpmyadmin.

We had reluctantly provided access to phpmyadmin to the appdb developers (it is a very handy tool, and something they very much wanted).  But it is a prime target for hackers, and apparently our best efforts at obscuring it and patching it were not sufficient.  

So we have removed all access to phpmyadmin from the outside world.  We do not believe the attackers obtained any other form of access to the system.  

On the one hand, we saw no evidence of harm to any database. We saw no evidence of any attempt to change the database (and candidly, using the real appdb or bugzilla is the easy way to change the database).  

Unfortunately, the attackers were able to download the full login database for both the appdb and bugzilla.  This means that they have all of those emails, as well as the passwords.  The passwords are stored encrypted, but with enough effort and depending on the quality of the password, they can be cracked. 

This, I'm afraid, is a serious threat; it means that anyone who uses the same email / password on other systems is now vulnerable to a malicious attacker using that information to access their account. 

We are going to be resetting every password and sending a private email to every affected user. 

This is again another reminder to never use a common username / password pair.  This web site provides further advice as well: [http://asiknews.wordpress.com/2011/03/02/best-practice-password-management-for-internet-web-sites/](http://asiknews.wordpress.com/2011/03/02/best-practice-password-management-for-internet-web-sites/)  

I am very sad to have to report this.  We have so many challenges in our world today that this is a particularly painful form of salt for our wounds.  

However, I think it is urgent for everyone to know what happened.  

Cheers,

 Jeremy

---

### Post by dino99 on 2011-10-12
So what ?

---

### Post by ergo-proxy on 2011-10-12
If someone has an account on winehq and uses the same password for everything might be worth to change it.

---

### Post by Dangertux on 2011-10-12
I guess 1 equaled 1 but not 2 ;-)

---

### Post by ubupirate on 2011-10-12
I wonder if someone got fired already or not...

---

