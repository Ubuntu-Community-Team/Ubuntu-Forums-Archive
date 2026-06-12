---
title: "Swiftdove Refuses To Open Links In Swiftweasel32-Athlon64"
date: 2007-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mark76 on 2007-12-16
I downloaded and installed Swiftweasel32 for AMD 64 bit computers to solve problems I was having with Flash and Java.  Out of curiosity I decided to give the email application, Swiftdove, a go as well.  Unfortunately it's impossible to set a preferred browser for opening links in emails anywhere in Swiftdove, and Swiftdove refuses to even acknowledge that my system preferred applications (the browser component of which is set to swiftweasel32)  even exist.

Quite frankly I'm getting fed up ](*,)

---

### Post by firecat53 on 2007-12-16
Did you set your system preferred browser (system -> preferences -> preferred applications) to custom (/path/to/swiftweasel32)?

Scott

---

### Post by Mark76 on 2007-12-16
The path is set to /usr/local/swiftweasel32/swiftweasel-bin %s

There doesn't seem to be an executable for Swiftweasel32

---

### Post by firecat53 on 2007-12-16
Hmmm...I'm running swiftweasel (athlon 64) right now, and I've got the swiftweasel executable in both /usr/local/swiftweasel and /usr/local/bin. I'm also running swiftdove.  I've run swiftweasel32 in the past and had no troubles with that issue. 

Perhaps try a reinstall? Are you installing on gutsy or earlier ubuntu? Did you install the deb from the Sourceforge page? I think the problem is not having the swiftweasel32 executable. I just tried launching swiftweasel-bin from the command line, and it didn't work. 

Good luck :) Works great when you get there finally!!

Scott

---

### Post by Mark76 on 2007-12-16
Yep, I downloaded it from the Sourceforge site 

[http://sourceforge.net/project/downloading.php?groupname=swiftweasel&filename=swiftweasel32-2.0.0.11_athlon64-32bit_ubuntu_7.10_AMD64.deb&use_mirror=dfn](http://sourceforge.net/project/downloading.php?groupname=swiftweasel&filename=swiftweasel32-2.0.0.11_athlon64-32bit_ubuntu_7.10_AMD64.deb&use_mirror=dfn)

Should I reinstall from the Synaptic or from Sourceforge?

---

### Post by Mark76 on 2007-12-16
Okay. I did a complete removal from Synaptic, reinstalled and...

I still don't get an executable in usr/bin.

---

### Post by Mark76 on 2007-12-16
Update.

I redownloaded the deb package from SF and opened it with Archive Manager.  After a bit of looking around I found the Swiftweasel32 bin file and manually installed it in the usr/bin folder by going into XFE as root and telling it to move from the folder it was in to that one.

I suspect it was there all along but for some reason it didn't get installed

---

### Post by Mark76 on 2007-12-16
And *still* Swiftdove doesn't open links in swiftweasel32.

My preferred browser is definitely set to Swiftweasel32, so whatever is going wrong must be at the Swiftdove end

---

### Post by Mark76 on 2007-12-16
Hey Firecat.  Do you have either Firefox or Thunderbird installed?

I'm beginning to suspect it's something to do with me having neither of those.

---

### Post by Mark76 on 2007-12-16
Can someone who has the app post the relevant part of the about:config file so I can see if mine is the same?

Oops. Forgot to mention: I'm on Gutsy

---

### Post by gwilson on 2007-12-17
Just to add a bit to this, I installed Swiftweasel 32 with Thunderbird already installed. When I go to open a link within an email message, Swiftweasel starts up, opens my home page, and just sits there. It never opens the expected link.

---

### Post by Mark76 on 2007-12-18
At least yours *starts* opening.

I have to copy/paste the links into the browser address bar to get mine to open.

---

### Post by Kilz on 2007-12-18
> **Mark76 said:**
> At least yours *starts* opening.

I have to copy/paste the links into the browser address bar to get mine to open.

Did you by chance use [my howto ]("http://ubuntuforums.org/showthread.php?p=1174435")to install swiftweasel32?

---

### Post by firecat53 on 2007-12-18
Wow, that sucks it's giving you such a hard time!! Definitely try Kilz's how-to -- and make sure you start from scratch and make sure everything is deleted first. 

You did check /usr/local/bin for the executable, right? That's where it's installed in my 64-bit install. Perhaps there's a path issue and /usr/local/bin isn't in your path?

Yes, I have firefox installed, but not thunderbird. I can't imagine that would have an effect, but who knows???

Maybe try installing the 64 bit version and see if that works for you? That's what I use, then if I realllly need java, I'll try out the built-in java in konqueror (no, I'm not running kde :) ) or install swiftweasel32 again. 

Good luck!
Scott

---

### Post by Mark76 on 2007-12-18
> **Kilz said:**
> Did you by chance use [my howto ]("http://ubuntuforums.org/showthread.php?p=1174435")to install swiftweasel32?


Erm. Yes.

---

### Post by Kilz on 2007-12-18
> **Mark76 said:**
> Erm. Yes.

You might have missed this, in the common problems section. 

> **Kilz said:**
> 
**[SIZE="4"][COLOR="Sienna"]Common Problems[/COLOR][/SIZE]**
IF YOU HAVE ANY PROBLEMS CHECK THE SECTIONS FOR FIXES TO COMMON PROBLEMS. If you make a post requesting help please state if you followed the howto or installed the script, also list all steps you have made to try and correct the problem.

**You must setup what program is called for some things. There is [a post on the settings for email]("http://ubuntuforums.org/showpost.php?p=2582830&postcount=11") here**, and this one is for [making the "open" in the downloads window to work]("http://ubuntuforums.org/showpost.php?p=2685097&postcount=11") . untill I have time to expand it a little.


---

### Post by Mark76 on 2007-12-18
I pasted the code into my swiftdove and weasel32 about:config files but changed firefox to swiftweasel32 and thunderbird to swiftdove.  IS that okay?

---

### Post by Kilz on 2007-12-18
> **Mark76 said:**
> I pasted the code into my swiftdove and weasel32 about:config files but changed firefox to swiftweasel32 and thunderbird to swiftdove.  IS that okay?

Yes, but where it says /path/to/application you have to have the path to the application. The path to swiftweasel32 would be ```
/usr/local/swiftweasel32/swiftweasel
``` swiftdove would be ```
/usr/local/swiftdove/swiftdove
```

---

### Post by Mark76 on 2007-12-18
Cool.

Now all I have to do is figure out how to delete the new entries in the Swiftdove about:config file so I can make the changes.

---

### Post by Kilz on 2007-12-18
> **Mark76 said:**
> Cool.

Now all I have to do is figure out how to delete the new entries in the Swiftdove about:config file so I can make the changes.

You should be able to edit them.

---

### Post by Mark76 on 2007-12-18
There isn't a delete option.

---

### Post by Kilz on 2007-12-18
> **Mark76 said:**
> There isn't a delete option.

Please read response 20.

---

### Post by Mark76 on 2007-12-20
Okay. When it asks me to enter a value for network.protocol-handler.app.ftp/http/https , /usr/local/swiftweasel32 the guide I'm following doesn't mention anything.

---

### Post by Kilz on 2007-12-20
> **Mark76 said:**
> Okay. When it asks me to enter a value for network.protocol-handler.app.ftp/http/https , /usr/local/swiftweasel32 the guide I'm following doesn't mention anything.

[The link in post 16]("http://ubuntuforums.org/showpost.php?p=3974201&postcount=16"), gives information on that. Please read the post the link in 16 shows.
If you have combined network.protocol-handler.app.ftp/http and network.protocol-handler.app.ftp/https into one you may need to reinstall swiftdove and follow the information supplied.

---

### Post by Mark76 on 2007-12-20
I had to reinstall my entire system, thanks to the bloody partitioner; so I took the opportunity to reinstall Swiftweasel32 and Swiftdove as well

I haven't combined them into one the / indicates "or".  So I have (for example)

**network.protocol-handler.app.ftp , /usr/local/swiftweasel32** on one line and yadda yadda http yadda yadda on another.  I also added the line to the Swiftweasel32 about:config "**network.protocol-handler.app.mailto , /usr/local/swiftdove**, set **Swiftweasel32** and **Swiftdove** as preferred apps for browsing and email and it still doesn't work.

I can redo it a million times and unless someone tells me where I'm going wrong it will never work.

---

### Post by Mark76 on 2007-12-22
This line

network.protocol-handler.app.http , /path/to/firefox

In my  Swiftdove about:config now reads

network.protocol-handler.app.http , /usr/local/swiftweasel32/swiftweasel

Is that correct?

---

### Post by Kilz on 2007-12-22
> **Mark76 said:**
> This line

network.protocol-handler.app.http , /path/to/firefox

In my  Swiftdove about:config now reads

network.protocol-handler.app.http , /usr/local/swiftweasel32/swiftweasel

Is that correct?

It should be.

---

### Post by derrick81787 on 2008-01-14
I found a really good solution.  Just open Swiftweasel and go to Edit >> Preferences >> Main and click the button that says "Check Now" in order to check if Swiftweasel is your default browser.  Whenever it says that it isn't, tell it to be, and that should fix your problem.  This worked for me, even whenever setting it in my Preferred Applications did not.

By the way, I'm running Xubuntu Gutsy.  I hope this works for you as well.

- Derrick

---

### Post by Mark76 on 2008-01-15
Yikes

---

### Post by derrick81787 on 2008-01-15
> **Mark76 said:**
> Yikes

Try resizing the preferences window to make it bigger.  I'm willing to bet the option is there.

- Derrick

---

### Post by Mark76 on 2008-01-16
What's supposed to happen when you click on Check Now?

---

### Post by derrick81787 on 2008-01-16
If it is already your default browser, a window should pop up telling you so.  If not, it should ask you if you want it to be the default browser and you should click "Yes" or "Make Default" or something like that.  What did it do when you tried it?

---

### Post by Mark76 on 2008-01-16
Nothing.

---

