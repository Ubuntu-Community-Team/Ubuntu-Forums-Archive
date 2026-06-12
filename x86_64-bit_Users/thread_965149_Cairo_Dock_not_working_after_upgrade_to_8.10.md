---
title: "Cairo Dock not working after upgrade to 8.10"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by timgood on 2008-10-31
After upgrading from 8.04 to 8.10 Cairo Dock would only start in 2D mode. I uninstalled it and re-installed to find that it now will not start at all. It also no longer adds an entry under the applications menu. Can anyone think of what might be the problem?

---

### Post by silence.hr on 2008-11-01
same here, no idea why ...

---

### Post by Landara on 2008-11-01
Ditto. After much research I have found the problem(but not the solution).  The problem is that Cairo NEVER launches with 3d enabled, thats an Applet called Rendering.  We need to turn on that applet, and all our problems will go away.  Now, for the real problem, we have NO applets at all.  They are in my directory, but they don't show up in the program itself so we can't activate them :(  I am of course assuming that you guys are in the same boat here.

---

### Post by m_ad on 2008-11-01
Is there an older version available we can use? This is a major problem for me, as I've relied on Cairo-Dock quite a bit :)

---

### Post by Landara on 2008-11-01
> **m_ad said:**
> Is there an older version available we can use? This is a major problem for me, as I've relied on Cairo-Dock quite a bit :)

I don't know, but I simply turned my dock to maximum transparency. I would rather have it not show than show in 2D mode personally.

---

### Post by Nintendo01 on 2008-11-01
I did some Googleing and found that the Intrepid version of Cairo dock is a very old version that doesn't support the addons and such yet. We'll just have to wait till they update the repositories with the latest version and suffer through the temporary 2D look.

---

### Post by bopomofo on 2008-11-01
Cairo was getting so much praise in another thread that I decided to give it a try.

I tried followed the instructions here:

[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

I downloaded the most recent .deb package, but trying to install it gives the error:

"The package might be corrupted or your are not allowed to open the file. Check the permissions of the file."

(Yes, I had set the .deb as executable)

So I downloaded the the most recent source. But running ./configure I get the error:

./configure: line 10846: syntax error near unexpected token `0.35.0'
./configure: line 10846: `IT_PROG_INTLTOOL(0.35.0)'


:confused:


I am on Intrepid, and had never tried installing Cairo-dock until today (I use AWN, which, um... works!)

---

### Post by ruipalmeira on 2008-11-02
installing version 1.6.3 did the trick.. 

has anyone idea on how to make NowPlaying Screenlet themes actually work.. with the repository version?

---

### Post by Landara on 2008-11-02
> **ruipalmeira said:**
> installing version 1.6.3 did the trick.. 

has anyone idea on how to make NowPlaying Screenlet themes actually work.. with the repository version?

1.6.3 didn't work for me, sadly :( I have tried everything there is to try as far as deleting removing reinstalling upgrading and downgrading the dock, the plug-ins,even the themes! It just wont work! :(

---

### Post by fabounet on 2008-11-03
maybe because the .deb is for Hardy ?
you should wait until a package built with the 8.10 is available.

---

### Post by gyrene2083 on 2008-11-03
I can't even get passed the autoreconf part. This is what I am getting;

wild@ubuntu:~/Desktop$ autoreconf -isvf
autoreconf: `configure.ac' or `configure.in' is required
wild@ubuntu:~/Desktop$ 

Any ideas?

---

### Post by gyrene2083 on 2008-11-03
<double posted somehow>

---

### Post by christophermluna on 2008-11-09
Hey there,

I was having this exact same issue, and nothing that I did seemed to work.  I kept looking through the forums for something.

Finally, I happened upon this post:

[http://ubuntuforums.org/showthread.php?t=954474](http://ubuntuforums.org/showthread.php?t=954474)

I entered Synaptic Package Manager, marked cairo-dock and cairo-dock-plugins for complete removal.

I applied the changes, and then I downloaded the version in the above post.

I installed them in the order indicated in the post: first cairo-dock, then cairo-dock-plugins, then cairo-dock-themes.

After installing and running it, my applets came back.  I turned on rendering, and all my views were available again.

I hope that this works for you fellows as well.

---

