---
title: "where to find firefox32 bit"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by tmfs on 2008-01-22
I have ubuntu amd64. I'm trying to install firefox32. However when I download firefox from firefox.com, I just get the 64 bit version. Does anyone know where to get the 32 bit firefox?

PS - I know that there is a script for installing firefox32 and setting up flash, java, etc. but I want to do things manually

---

### Post by DJ_Peng on 2008-01-22
Have you tried checking at [http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)? If that page still gets you 64-bit versions you can go to [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0/linux-i686/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0/linux-i686/) for i686 versions for Linux.

---

### Post by incubus on 2008-01-22
Yep, Kilz got it for you:
[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

I got swiftweasel here running flawlessly.

incubus

---

### Post by DJ_Peng on 2008-01-23
He actually says he knows about the script but wants to do it manually. I don't blame him. That's how I'm running both Firefox 2 and the beta of Firefox 3 and I personally like it much better this way. Even though I had to copy all my plugins manually I find I'm having much more freedom (of choice) in how I use and update the Fox. Plus if we do it manually we don't have to worry about remembering to sudo anything to get updates. But to each their own. That's why FOSS is so great. We're not locked in to anything just because devs decide they want to do it a certain way.

---

### Post by stmiller on 2008-01-23
Yeah I just downloaded a 32bit Firefox from mozilla.org. Auto-updates itself, installs flash automatically, etc. It has an installer, and is painless.

---

### Post by Kilz on 2008-01-23
> **DJ_Peng said:**
> He actually says he knows about the script but wants to do it manually. I don't blame him. That's how I'm running both Firefox 2 and the beta of Firefox 3 and I personally like it much better this way. Even though I had to copy all my plugins manually I find I'm having much more freedom (of choice) in how I use and update the Fox. Plus if we do it manually we don't have to worry about remembering to** sudo anything to get updates. **But to each their own. That's why FOSS is so great. We're not locked in to anything just because devs decide they want to do it a certain way.

The script does not requirre sudo anything to get updates. It also has deb files that make updating very easy, just double click on the file and gdebi installs it. You can also use the swiftweasel from its repository and get updates automatically. But to each thier own.

---

### Post by incubus on 2008-01-25
I've never run Kilz's script myself, I just read it and do it by hand (I change a few things).  It's a fantastic compilation of information.

incubus

---

### Post by sulusulu on 2008-01-25
I installed Firefox from the Ubuntu and I have flash working.  What am I missing?

---

### Post by Kilz on 2008-01-25
> **sulusulu said:**
> I installed Firefox from the Ubuntu and I have flash working.  What am I missing?

Java. The Java plugin in my 32bit firefox/flash/java script is Sun Java. It works on all sites. The 64bit Blackdown java and icedtea plugins do not work on all sites, and blackdown can cause the browser to crash. There is no 64bit Sun Java plugin.

---

### Post by DJ_Peng on 2008-01-25
> **Kilz said:**
> The script does not requirre sudo anything to get updates. It also has deb files that make updating very easy, just double click on the file and gdebi installs it. You can also use the swiftweasel from its repository and get updates automatically. But to each thier own.
Ah, cool. I must not have seen your script. I may check it out when Firefox 3 goes live. Once a few more extensions get updated, that is. Thanks for the info.

---

### Post by sulusulu on 2008-01-25
> **Kilz said:**
> Java. The Java plugin in my 32bit firefox/flash/java script is Sun Java. It works on all sites. The 64bit Blackdown java and icedtea plugins do not work on all sites, and blackdown can cause the browser to crash. There is no 64bit Sun Java plugin.

Thanks!  I guess I will have to switch then. :)

---

### Post by sulusulu on 2008-01-25
Sweet!  I switch to Swiftweasl.  It does seem to be a bit faster.  And the Firetray add-on works now so I can minimize Firefox to the system try now.  :)

---

