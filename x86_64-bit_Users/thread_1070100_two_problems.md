---
title: "two problems"
date: 2009-02-14
forum: x86 64-bit Users
---

### Post by Richard-g8jvm on 2009-02-14
Hi 
Two problems giving problems on my mothers machine.

Running 8.10 64 bit.

1.certain gnome card games start in full screen mode, and when you try to
return to normal mode, it changes for about 1 second then flips back.
She's using CAB as a stop gap.

2 She has a wireless router, the gnome keyring util keeps requesting a password, even when the privileges set in the user control are set to allow this.
Also when the user password is changed the key ring stays unchanged.
The password control for internet connection needs to be removed, but the keyring util complains each time its locked and needs a password.
 
This is a major problem, with shakey hands it takes several attempts ,even with the keyboard slugged to enter the password, and several minutes.


Please no silly coments about security and using CAB to kill X, the user
is disabled and has severe difficulty using a keyboard.


TIA

Richard

---

### Post by dcstar on 2009-02-14
> **Richard-g8jvm said:**
> Hi 
Two problems giving problems on my mothers machine.

Running 8.10 64 bit.

1.certain gnome card games start in full screen mode, and when you try to
return to normal mode, it changes for about 1 second then flips back.
She's using CAB as a stop gap.

2 She has a wireless router, the gnome keyring util keeps requesting a password, even when the privileges set in the user control are set to allow this.
Also when the user password is changed the key ring stays unchanged.
The password control for internet connection needs to be removed, but the keyring util complains each time its locked and needs a password.
....

This might help with #2:

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

#1 may be video hardware, what is it?

---

### Post by theozzlives on 2009-02-14
I have a wireless laptop that asks for the keyring password when I set it to login automatically.

---

### Post by Clancy_s on 2009-02-14
> **theozzlives said:**
> I have a wireless laptop that asks for the keyring password when I set it to login automatically.

It's meant to do that as a security thing, the keyring is only unlocked if you log in manually and give a password.

There's been a number of fixes discussed, I went with making the passkey null, which was the simples.  Having a null password is a theoretical security hole but I don't do anything high risk with this computer.  The instructions are here:

[http://ubuntuforums.org/showthread.php?t=1003471](http://ubuntuforums.org/showthread.php?t=1003471)

a search on keyring will lead you to some others (I didn't bookmark the ones I didn't use)

---

### Post by Richard-g8jvm on 2009-02-15
Thanks for the replies, I'll e-mail the answers across to my sister who lives a lot closer, and let her run through, I'm 70 miles away.


On item 1

when everything was loaded the gnomes games did not show any problems.
I suspect its a config problem, as this occurred after use.
A complete reinstall of gnome games didnt clear it.
Its not a major problem just a PIA


Thanks
 Richard

---

