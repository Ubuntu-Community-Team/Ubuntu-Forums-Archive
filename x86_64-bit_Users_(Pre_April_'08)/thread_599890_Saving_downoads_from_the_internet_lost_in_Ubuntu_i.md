---
title: "Saving downoads from the internet lost in Ubuntu instead of being saved to Desktop"
date: 2007-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by TWFJR on 2007-11-01
At one time Ubuntu saved downloads to the Desktop. Now nothing gets saved to the Desktop.  I found downloads in /tmp.  But now I am finding that is not always the case.  How does one change where downloads are saved?

---

### Post by haldean on 2007-11-01
If you're using Firefox, go to Edit -> Preferences -> Main, then under Downloads, choose "Save files to..." and then select your Desktop folder.

---

### Post by TWFJR on 2007-11-01
> **haldean said:**
> If you're using Firefox, go to Edit -> Preferences -> Main, then under Downloads, choose "Save files to..." and then select your Desktop folder.

Investigating via your instructions confirms that the Desktop is chosen as the folder where downloads are saved.  I think that something is corrupted.  Thanks for your advise. Still searching for a solution.

---

### Post by haldean on 2007-11-02
Does anything show up on your desktop? Can you see other files when you put them there?

You might want to try setting the download directory to something else and seeing if it works if it's different.

---

### Post by TWFJR on 2007-11-02
> **haldean said:**
> Does anything show up on your desktop? Can you see other files when you put them there?

You might want to try setting the download directory to something else and seeing if it works if it's different.

I did try setting another directory.  I get the download window with "Open" and "Save" options.  Only "Open" works, opening and saving.  Saved downloads are stored in /tmp.

---

### Post by haldean on 2007-11-02
Strange... what version of Firefox and Ubuntu are you using?

---

### Post by TWFJR on 2007-11-03
> **haldean said:**
> Strange... what version of Firefox and Ubuntu are you using?

I am using Ubuntu 64 bit 7.10, but the problem was also with 7.04.  FireFox ver. 2.0.0.6.

---

### Post by TWFJR on 2007-11-03
> **TWFJR said:**
> I am using Ubuntu 64 bit 7.10, but the problem was also with 7.04.  FireFox ver. 2.0.0.6.

I might add that I have installed Flock, Java 6, Flash, codecs for DVD and streaming media.

---

### Post by haldean on 2007-11-03
Does the same thing happen with Flock?

---

### Post by Mr_bleu on 2007-11-04
> **TWFJR said:**
> I did try setting another directory.  I get the download window with "Open" and "Save" options.  Only "Open" works, opening and saving.  Saved downloads are stored in /tmp.
Did you change the Save to setting in Firefox? I didn't see you state that.  Try saving to your home/<name here>/documents folder.  You might not have permissions to save to /tmp.

---

### Post by TWFJR on 2007-11-04
[QUOTE=Mr_bleu;3701775]Did you change the Save to setting in Firefox? I didn't see you state that.  Try saving to your home/<name here>/documents folder.  You might not have permissions to save to /tmp.[/QUOTE

Changing "Save" setting works on directory under /home/tom/ except /home/tom/Directory.  I have a few files on Directory that I cannot move to trash.  Seems to me that, when a file is opened, Ubuntu automatically saves a copy in /tmp.

---

### Post by jaybombalous on 2007-11-04
u need update to 2.0.0.8, try that first. U can also delete the .mozilla folder in your ~/ dir to reset the configuration for firefox.

---

### Post by TWFJR on 2007-11-04
> **jaybombalous said:**
> u need update to 2.0.0.8, try that first. U can also delete the .mozilla folder in your ~/ dir to reset the configuration for firefox.

FireFox "Help" indicates ver. 2.0.0.6 but Synaptic indicates that I have installed ver. 2.0.0.8.  Which ver. do I have?  Will Apt-get Firefox install ver. 2.0.0.9?

---

### Post by jaybombalous on 2007-11-04
> **TWFJR said:**
> FireFox "Help" indicates ver. 2.0.0.6 but Synaptic indicates that I have installed ver. 2.0.0.8.  Which ver. do I have?  Will Apt-get Firefox install ver. 2.0.0.9?

A good question that I do not know the answer too. But, my help says 2.0.0.8 so that is probably some of your problem. I am not sure how it happened, but maybe u should uninstall firefox and clear the *.deb packages out apt-get cache and then reinstall forefox.

Thats just my advice if u want something to try or u could wait for someone who may have a better approach.

---

### Post by TWFJR on 2007-11-04
> **jaybombalous said:**
> A good question that I do not know the answer too. But, my help says 2.0.0.8 so that is probably some of your problem. I am not sure how it happened, but maybe u should uninstall firefox and clear the *.deb packages out apt-get cache and then reinstall forefox.

Thats just my advice if u want something to try or u could wait for someone who may have a better approach.

Many thanks for hanging in there with me. I've yet to update Firefox and delete mozilla folder.  I think that you are right about the problem being with Firefox.  Something may be broken after installing EasyUbuntu, and all that allows for Flash, Java, and DVD/streaming media.

---

### Post by jaybombalous on 2007-11-04
Try using ubuntuzilla, its in the 3rd party projects sub forum on this forum.

It will install 2.0.0.9 :)

Goto sourceforge, d/l the latest ubuntuzilla *.deb package and install it.

Then u wanna run this command from terminal
```

ubuntuzilla.py -a install -p firefox

```

---

