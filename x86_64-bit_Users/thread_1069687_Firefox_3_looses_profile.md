---
title: "Firefox 3 looses profile"
date: 2009-02-14
forum: x86 64-bit Users
---

### Post by bobwdn on 2009-02-14
I am frustrated. Over the course of the last six to eight months Firefox3 has crashed many times. (Ubuntu 64bit)

When this crash happens, I loose all my *bookmarks*, my *add ons* are gone, my *homepage* and many other settings. Deleting profiles, etc. makes matters worse. My hardware is new at the time I installed Ubuntu 8.04.1 LTS 64bit.

When attempting to restore my bookmarks (from backups) Firefox will no longer "import."

I have read forums. Searched Google and find no simple repair and have resorted to using SeaMonkey. Most of the suggestions I find tend to make matters worse.

I am disappointed that during the last several months Firefox has not fixed this crash issue, but they have not. Or I have missed the "fix." And in their defense, this crashing issue may not solely be a Firefox 3 issue?

Okay, sorry about the vent. MANY good things have come from Linux and Ubuntu and I like them. I have benefited from them and for that I thank Linux community and Ubuntu community. But, if anyone is aware of a howto post or a tutorial that will help me solve this once and for all, I am listening!

Now, I do not know if it is just an Ubuntu64 issue or if Ubuntu32 users are experiencing the same, but another computer at work (Ubuntu 8.04.1 32bit) running an LTSP setup with Firefox3 does not crash and loose bookmarks, add ons, etc. So, 64-bit users, any suggestions? Is Intrepid the answer?

---

### Post by philinux on 2009-02-14
I must admit this has never happened to me on 32 or 64 bit. You dont say what you've tried.

Couple of things to try, and report any errors after a crash.

1. run firefox in safe mode

```
firefox -safe-mode
```

2. run firefox from the terminal normally

```
firefox
```

3. backup you're bookmarks, close firefox and delete or rename you're ~/.mozilla folder. Restart FF to create a new profile folder.

---

### Post by ATLfletch on 2009-02-14
Same thing just happened to me today when I installed the updates to Firefox 3 and restarted. Zap, no more bookmarks or history whatsoever. 

I searched to some info on the Mozilla site that said the bookmarks might not be lost. It was like it overwrote my user profile (I was using the 'default' profile, unfortunately I didn't back it up because I never had this problem before with any version of Firefox). As suggested by Mozilla site I found where the default profile is located in file structure and tried to see if I could either locate an old profile or bookmarks file to reinstall but no luck on that. 
Then I tried using profile manager to open a new profile. I'm not sure what happened but now I can't get F-fox to start up at all. 

I even reinstalled Firefox 3 and it still won't start up past the Profile Manager's 'select user' dialog box. Since Firefox is the only browser installed now my laptop is kind of dead in the water. It won't let me create a new user either... I get a box that reads, 

[INDENT]Profile Creation Failed

Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIToolkitProfileService.createProfile]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: chrome://mozapps/content/profile/createProfileWizard.js :: onFinish :: line 233"  data: no][/INDENT]


I'm walking away for a while to clear my head. I didn't plan to spend all Saturday afternoon messing with some silly browser problem. 
Any suggestions??? 

Next I'm thinking I'll try to install an alternate browser so I can use it until I get a working version of Firefox up again. 

Maybe I should then try to completely uninstall Firefox and then reinstall it, hopefully that will fix the browser issue, but I think my old bookmarks, history, & passwords are a goner. 

Thanks in advance. 

(FYI - Running Ubuntu 8.04 on a Thinkpad 600x laptop)

---

### Post by bobwdn on 2009-02-14
Well, to answer **philinux** post.

Firefox(3) will start and it looks just like ```
firefox -safe-mode
``` when it comes up.

I have backedup my bookmarks and deleted my profile (during one of the many Firefox rebuilds in the past) and *(not that I am against work)* it was a lot of work for the fourth or fifth time. So, see I am getting a little tired of "fixing" my forefox3. (Sorry, venting!)

And the **ATLfletch** post.

Yes, your experience is identical to mine. 

I am going to proceed to the Firefox forum (as soon as I find it) and post there to see if there is a fix or not.

This is the thing that I love about Linux. The ability to turn to the community, determine where to look for help and "usually" help will be found.

Thanks guys.

******************

Shortly after posting above, I found fix at Mozillazine.

Go there and search for "lost bookmarks" and you will find a discussion regarding a broken "places.sqlite" file within our profiles.

I know how to manually backup my bookmarks, time to find out if it can be done automatically?

See ya there.

---

### Post by dcstar on 2009-02-14
> **ATLfletch said:**
> Same thing just happened to me today when I installed the updates to Firefox 3 and restarted. Zap, no more bookmarks or history whatsoever. 
.........
(FYI - Running Ubuntu 8.04 on a Thinkpad 600x laptop)

In Linux all your Firefox profile stuff is in the (hidden) .mozilla folder.

Rename this folder and start Firefox and a fresh one will be created, then you can copy/import stuff from the renamed folder (Extensions, Bookmarks etc) into the new one.

---

### Post by simgriff on 2009-05-18
The exact thing has happened to me.  This is the second time and I have spent so much time trying to get Firefox 3 working again.  The first time I deleted my whole profile file and reloaded Firefox and it all went okay for a couple of months - got my bookmark toolbar back back button working etc etc.- had to import a bookmark .html form another computer.  Then it just happened again and I did all the same things but now I can't create a profile (exact error message as below) so can't even get Firefox started to find out if things are working again.  I am giving up and using Seamonkey for a while until someone comes up with a fix.  (I am on an EEEPC 900 running with the latest eeebuntu.

> **ATLfletch said:**
> Same thing just happened to me today when I installed the updates to Firefox 3 and restarted. Zap, no more bookmarks or history whatsoever. 

I searched to some info on the Mozilla site that said the bookmarks might not be lost. It was like it overwrote my user profile (I was using the 'default' profile, unfortunately I didn't back it up because I never had this problem before with any version of Firefox). As suggested by Mozilla site I found where the default profile is located in file structure and tried to see if I could either locate an old profile or bookmarks file to reinstall but no luck on that. 
Then I tried using profile manager to open a new profile. I'm not sure what happened but now I can't get F-fox to start up at all. 

I even reinstalled Firefox 3 and it still won't start up past the Profile Manager's 'select user' dialog box. Since Firefox is the only browser installed now my laptop is kind of dead in the water. It won't let me create a new user either... I get a box that reads, 

[INDENT]Profile Creation Failed

Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIToolkitProfileService.createProfile]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: chrome://mozapps/content/profile/createProfileWizard.js :: onFinish :: line 233"  data: no][/INDENT]


I'm walking away for a while to clear my head. I didn't plan to spend all Saturday afternoon messing with some silly browser problem. 
Any suggestions??? 

Next I'm thinking I'll try to install an alternate browser so I can use it until I get a working version of Firefox up again. 

Maybe I should then try to completely uninstall Firefox and then reinstall it, hopefully that will fix the browser issue, but I think my old bookmarks, history, & passwords are a goner. 

Thanks in advance. 

(FYI - Running Ubuntu 8.04 on a Thinkpad 600x laptop)

---

