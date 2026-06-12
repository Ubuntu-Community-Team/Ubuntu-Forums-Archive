---
title: "Moved file to /Desktop"
date: 2009-05-31
forum: x86 64-bit Users
---

### Post by a2z on 2009-05-31
Greetings everyone,

I'm very inexperienced with Ubuntu. But I really like the os so far.
I need to move some files which are root driven. 
I gather I need to move them using "sudo" in a terminal. Since I'm finding my root terminal is not active. 
As an experiment I moved an empty folder to /Desktop. I had the original containing folder open and watched it disappear. But when I looked on my desktop it was no where to be found. I later find that my current desktop is located under /home/a2z/Desktop.
I've looked everywhere for this file but can't find it. 
My questions are:

1) Where did this file go?
2) Is there a problem with my system configuration?

I'd like to better understand whats going on before I try to move important root files. Before I really muck things up.

Thanks to everyone for everything.

Regards,

a2z

os: jaunty x86 64

---

### Post by koenbeek on 2009-05-31
How did you move the folder ?

I'm guessing you typed the following in a terminal ?

sudo mv foldername /Desktop

as you're root when using sudo, you can do anything, and the folder named fioldername was moved (and renamed) to /Desktop

if you want it on your desktop you'll need to move it to your Desktop

sudo mv /Desktop /home/a2z/Desktop/foldername



you may find it is easier to use the file explorer with root rights as follows :

gksudo nautilus



just be very careful what you do when you have root rights, as you can do anything with your system, including screwing it up. also beware that root has a different Desktop directory (/root/Desktop) then other users (/home/userid/Desktop), you included

---

### Post by a2z on 2009-05-31
> **koenbeek said:**
> How did you move the folder ?

I'm guessing you typed the following in a terminal ?

sudo mv foldername /Desktop

as you're root when using sudo, you can do anything, and the folder named fioldername was moved (and renamed) to /Desktop

if you want it on your desktop you'll need to move it to your Desktop

sudo mv /Desktop /home/a2z/Desktop/foldername



you may find it is easier to use the file explorer with root rights as follows :

gksudo nautilus



just be very careful what you do when you have root rights, as you can do anything with your system, including screwing it up. also beware that root has a different Desktop directory (/root/Desktop) then other users (/home/userid/Desktop), you included

Yes that is what I did. I am also aware sudo can alter any state of the system. This is why I tested with an empty folder.
I followed the instructions in Ubuntu Help Center. Where it states

[COLOR="Gray"] mv foo ~/Desktop
	will move the file foo to your Desktop
	directory but [COLOR="Lime"]will not rename it[/COLOR].[/COLOR]
The above was copied & pasted from the help center. Your info contradicts what help says. I am not doubting your post, as I know errors are printed everyday. It would be good to know which is correct though. My guess is, I'm not understanding something from either end or both!
But what's weird is I have a Desktop with -0- items....
So your right and Help is misleading?
I am still not sure  what happened to this file.

I did want this practice file on my desktop. But the real files I need to move are permission denied. Which brought me to this experiment.
Thank God I didn't try to move other files.
I think I need more practice. With success before I try to move the real files.

I'm not familiar with moving files using the root file browser, But I'll definitely look into it. 

Thank you kindly for your help.

---

### Post by koenbeek on 2009-06-01
Hi,

  there is an important difference between /Desktop and ~/Desktop

  ~ is a shortcut for your home directory and ~/Desktop is = to your Desktop directory while /Desktop does normally not exist on a ubuntu system

  when you do a mv command to an unexisting name, the file is moved and renamed to this new name
  if you do a mv to an existing directory, the files are moved (not renamed) into this directory

  so maybe you did a mv to /Desktop instead of ~/Desktop

---

### Post by a2z on 2009-06-02
koenbeek,
Your absolutely right. That is what I did.  I think I forgot to put it in. **"~"** I did not see it:(.. I don't know how I missed it. Even while posting a reply to your helpful insight, 
I did not see it "~" It wasn't until yesterday while installing Yafaray that I seen "~" and wondered it's significance.
 I've been dabbling a bit in a whapatulie of computer code as of lately. So I know the importance of proper syntax. "sorta" 
But at any rate, I have been successful at moving some files.
I find being able to use a command line every bit auxillerating as they claim. 
I've used it very briefly with windows. But could see it's importance. Now I see a need to learn it's invaluable uses.
Thanks for setting me straight! Thank you thank you.

---

### Post by cariboo on 2009-06-02
I see all these command line solutions, wouldn't it just be easier to press Alt-F2 and type:

```
gksu nautilus
```

The above command will open the file manager as root. You can then navigate to the file/folder you want to put on your desktop. To make it accessible you will have to change the permissions to be able to access it.

Note: Do not move any system directories to your desktop, as you may run into problems. System directories are those that are located in Places-->Home Folder-->File System.

---

### Post by a2z on 2009-06-02
Hi,
Thanks for the reply.
I've made a note of this command.
I'd like to become comfortable using commands. 
And reading in the "HELP" which I think so many don't use, I found the command I needed. I just need to pay a bit more attention and not leave out, or add/miss spacing. 
As I have read in so many places, commands are very powerful.
My only intent was to move files I know need moving. Such as python scripts used with Blender.
Thanks for the flag not to move system files! I wouldn't. At least not intentionally. 
Cheers,
a2z

---

