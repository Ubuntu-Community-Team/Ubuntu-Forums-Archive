---
title: "WINE Account Corrupted"
date: 2024-04-21
forum: Wine
---

### Post by mark bower on 2024-04-21
I have tried to gain access to WINE, but my account is corrupted.  I have tried to reset password, but only failure.  I am not sure of my username, one of two options, but trying to change that also leads to a negative result.

I need an administrator to cancel my account, and do a clean register.  However, I cannot find and on line presence Board Administrator to help.  A Board Administrator is suggested, but where is the link or email address?

Suggestions?

---

### Post by TheFu on 2024-04-24
You've lost me.  

WINE is "W.I.N.E." and it is an emulator provided for free by installing the **wine** package.  Then, while running under the WINE emulator, you would install MS-Windows programs.  There's a WINEPREFIX environment variable that is used to control the location of where WINE programs are installed.  If you want to reset everything, just reset that environment variable to a new location.  Of course, if it isn't set, then there are default locations. I don't use WINE enough to know where the default locations are for WINE settings or WINE application installations.

The number of supported programs is growing, but don't work.  Sometimes, you'll find relevant information at [https://www.winehq.org/](https://www.winehq.org/) - they have a list of applications, with both versions of WINE and versions of the application that have worked. Sometimes another user has provided instructions for any techniques to get a specific application version to work.  IME, it is always required.  Only the most trivial applications will run without extra DLLs and settings specifically setup.

There is no username.  It is the same as your login name under Ubuntu, but I can't remember ever being asked for that under WINE.  Of course, you might be trying to run an application that connects to remote servers, which may require a login.  Nobody here can help with that, since we didn't setup the remote server, if there is one, and certainly didn't setup your account on it.  What were you trying to do?  Do you have a different Linux login just to use WINE?

"WINE" and "board administrator" don't make sense together, not to me. Perhaps if you explain that further?

You've been here 15 yrs, and have lots of posts, so I'm assuming you'll figure this out.  I can only think you were in a hurry when posting and posted to the wrong forums?  IDK.

I'm just throwing guess out. It is unlikely I'll hit on the actual issue, but some of these might get you thinking differently and you'll figure it out.

---

### Post by mark bower on 2024-04-24
I have successfully used WINE to run ACAD2000 (32bit) and Irfanview (64bit) for many many years.  My SYNAPTIC PKG MGR installations of it were successful in '21, '22, and '23.  I am in the process of completing my Installation of MATE 2024.04.  When I attempted to install WINE via synaptic pkg mgr, it balked with an error message.  I was attempting to get help from WINE Forums, but could not get login to work.  I tried to get help from WINE Hq, but no success, and could not find a successful path to get them to reset my account.  [I much prefer using synaptic or .deb over PPA installation, although I have been successful with PPA installations on rare occasions.]

I have attached some screen shots that show that WINE uses/requires a USERNAME, and refers to assistance from BOARD ADMINISTRATORS.  I.E., "If you continue to have problems, please contact the Board Administrators".  

Given I cannot get back into WINE Forums, I will tackle the WINE installation problem on this forum with a new post.

---

### Post by TheFu on 2024-04-24
Wine forums has nothing to do with Ubuntu or these forums, FWIW.  There's no secret channel that forum moderators or admins chat over. Sorry.

Basically, you have a new Toyota with a problem covered by the new car 1 yr warranty and you are taking it to a Ford dealer, asking them to fix it.  

Disclosure: I used to work for a company owned by Ford.  We didn't work on Toyota vehicles.

---

### Post by mark bower on 2024-04-24
Your distilled response:  the Ubuntu Forum is the place I need to go with a WINE install problem?

---

### Post by TheFu on 2024-04-24
> **mark bower said:**
> Your distilled response:  the Ubuntu Forum is the place I need to go with a WINE install problem?

That isn't what I said.  Your question was about _Wine Forums_ and I said _this is NOT the place_ to get help with other forums.
You said nothing about issues with a WINE install, at least I didn't see anything related to a local version of WINE in the posts above.  It was all about a forum login on some other forum.

That's what I said - or meant to convey.  I tried to make an analogy.  Don't take a broken Toyota to a Ford dealer for warranty service.  Guess that was also misunderstood.

---

