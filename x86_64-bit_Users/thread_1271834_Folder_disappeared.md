---
title: "Folder disappeared"
date: 2009-09-21
forum: x86 64-bit Users
---

### Post by Skillachi on 2009-09-21
So I've been running ubuntu 9.04 (64bit of course) since it released earlier this year. Also I formatted the drive to ext4.
I have it installed on my HP dv6700t.

I've had this laptop for roughly a year and a half now and have been loving it. I take all my notes on it and so on and so forth. Now the other day I go into the My Documents folder... only to see that there are 3 folders within my documents missing. Nowhere to be found. I checked if it was hidden. Did a sudo nautilus. Even tried a ls -la on my documents folder and the folder that I was looking for (with all my 3 years of university work) is gone!. I dunno what to do and am thoroughly confused.... Any ideas?

---

### Post by hellmet on 2009-09-21
Those probably got 'fsck'd. Check them in your .trash folder.

---

### Post by Skillachi on 2009-09-21
Where is the .trash folder?

---

### Post by hellmet on 2009-09-21
I'm not too sure as I'm on Windows as of now. When you do 'ls -la' do you see anything like .Trash or Lost+Found? If yes, what's in there?
Else try checking in '/'

And try 'sudo du /home/<user>/Documents' 
Do you see your folders now?

---

### Post by Skillachi on 2009-09-21
I see a lost+found but there is nothign in there.

No .trash at all though

Did the sudo and still nothing

---

### Post by hellmet on 2009-09-22
I'm sorry my friend. My knowledge ends there.

---

### Post by stumbleUpon on 2009-09-22
> **Skillachi said:**
> I see a lost+found but there is nothign in there.

No .trash at all though

Did the sudo and still nothing

the Trash folder is located in .local/share/ folder of your home directory. Type

```
 cd ~/.local/share/Trash 
```

to there.

---

### Post by Skillachi on 2009-09-24
I did that stumble but it still led to no new headways... I want back my folder :(:(

---

### Post by arrange on 2009-09-24
Do you happen to remember the names of the folders or files (or part of a name)? Or the last modification time?

---

### Post by Skillachi on 2009-09-24
The folder itself was named 'UWI' it had internal folders named 'h35b', 'h35a', 'gt35m',

Um... the file names are all lecture dates so they would be like '9-3-09' or 'final project' etc

Last date modified would be somewhere around April 24 2009 and last viewed would be something like May 5 2009

---

### Post by arrange on 2009-09-25
I would try to search for them in the filesystem, for example this way```
sudo find / -type d -iname '*h35b*' 2> /dev/null
```(will look at all the folders in the system for a possible match to *h35b* and "remove" error messages to reduce clutter in the output)

---

### Post by Skillachi on 2009-09-27
I tried your suggestion arrange... still nada. *sigh* i'm going to cry very very soon.

Are there any recovery software available to find files that got deleted? I remember my bro doing this with windows soemtime back and it found files which were even emptied from the recycle bin. I know I didnt delete the folder but I'm willing to try anything right about now

---

### Post by hellmet on 2009-09-28
As a last resort, try using the LiveCd. Just can't think of anything else. 
There was this strange thing that happened to me sometime back with my USB drive. Whenever I copied a file to it, it would show while mounted and disappear when remounted. However the space would remain occupied. I never solved the issue. I then used Windows and the file did not disappear. Shame.

---

### Post by arrange on 2009-09-28
Undelete: have a look [here]("http://ext4.wiki.kernel.org/index.php/Undeletion"), but I guess your chances are slim.

And - and I think you know now - with every OS and filesystem - and especially if you're using the newest technology (*ext4*) - always backup. It takes just a few seconds.

---

