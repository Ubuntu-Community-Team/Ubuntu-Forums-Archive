---
title: "Installing Wine 1.5 on Ubuntu 11.10 [64-bit]"
date: 2012-03-23
forum: Wine
---

### Post by DarthKreeaj on 2012-03-23
I just finished installing Ubuntu, and Wine is a current priority.  The reasoning?  I was only comfortable switching to a Linux OS because of Wine, so that now I can still play my current game of choice; Star Wars The Old Republic.  The problem is, whilst following the instructions found here: [http://www.noobslab.com/2012/03/install-wine-15-on-ubuntulinux-mint.html](http://www.noobslab.com/2012/03/install-wine-15-on-ubuntulinux-mint.html)

I encounter an error on the final step.  The error being "configure: error: Cannot build a 32-bit program, you need to install 32-bit development libraries."  However, throughout all my searching so far, I find negligible hints at Wine 64-bit instead, but nothing seems to be for version 1.5.  I was rather surprised that even in the Ubuntu Software Center, I could only find Wine 1.2 and 1.3, is there any reason for this?

---

### Post by DarthKreeaj on 2012-03-23
Bump...for great justice.

---

### Post by uRock on 2012-03-23
Moved to *Wine*. 

Please wait 24 hours before bumping your thread.

---

### Post by DarthKreeaj on 2012-03-24
My apologies.  I've just been scouring for hours now, trying to figure it out for myself.  So I was getting a little impatient.  I had missed the Wine section as well.  Duly noted.

---

### Post by cwwilson721 on 2012-03-24
The "wine 1.3" in the PPA is actually wine 1.4 (Read the stickies at the top of this forum for some hints and tips)

Just add the PPA and "sudo apt-get install wine1.3".

I've stopped compiling my own wine, just because the Ubuntu Wine PPA makes a good product. But, if you want to "roll your own", just search this forum on compiling. You'll get some good tips, and probably the answer to why your compile effort didn't work.

---

### Post by DarthKreeaj on 2012-03-24
Yeah, this is my first time to work with Linux in over three years.  I haven't tried to "roll my own."  I'm just trying to get this God damned game working, THEN I'm going to actually put in the time to learn Linux, once I'm playing.  I do most of my learning during my in-game downtime.  Also, I don't care about 1.4, I want 1.5; the first reported version to run the game well.

---

### Post by dino99 on 2012-03-24
you'll will get 1.5 compiled soon

[https://launchpad.net/~portis25/+archive/test/+packages](https://launchpad.net/~portis25/+archive/test/+packages)

---

### Post by DarthKreeaj on 2012-03-24
Thanks for the link, I was actually about to mark this thread closed.  I'll post a link to the site that helped me though.

Site: [http://m.ashwinraon.com/2012/03/installing-wine-1-5-with-itunes-10-x-support-on-ubuntu-12-0411-1011-04/](http://m.ashwinraon.com/2012/03/installing-wine-1-5-with-itunes-10-x-support-on-ubuntu-12-0411-1011-04/)

Completely ignore the line "Install some packages."  I found this line incredibly confusing, as well as my friend who is a networking professional with extensive Linux training, we both decided it'd be best to just skip it and it worked out wonderfully.

How do I mark this thread as Solved?

---

### Post by dino99 on 2012-03-24
> **DarthKreeaj said:**
> 

How do I mark this thread as Solved?

the Treads Tool link on top of that page on the right side

---

### Post by skenmy on 2012-03-24
Just to add a little context - the line 'Install some packages' appears to be a comment that someone has copied in and not deleted out of the code block.

---

### Post by dino99 on 2012-03-24
> **skenmy said:**
> Just to add a little context - the line 'Install some packages' appears to be a comment that someone has copied in and not deleted out of the code block.

from where is that comment ?

---

### Post by ashwinrao on 2012-03-24
Thanks @ [DarthKreeaj]("http://ubuntuforums.org/member.php?u=1589473") for the heads up! Even, I'm in confusion how this error happened. Any how I have corrected the code error in the web page.:popcorn:  That blog is my little effort to boost OpenSource and Ubuntu in India.[URL="http://ubuntuforums.org/member.php?u=1589473"]
[/URL]

---

### Post by DarthKreeaj on 2012-03-24
Well, I'm glad I could help, in some form, and I thank you for providing the only working method I could find for installing Wine 1.5  I even had SWTOR launcher working for a bit last night and patching while I slept.  Unfortunately it locked up and is maintaining the previous error of being all black on the launcher now.  Is there any way to fix this or should I just keep attempting to open and close until it works?

---

### Post by ashwinrao on 2012-03-25
Unfortunately, I'm not much gaming person so that I can assist you here. However, you could seek advice [here]("http://www.swtor.com/community") and also wait for other community member's replies who successfully installed this and using on their machines. I also found this [bug]("http://bugs.winehq.org/show_bug.cgi?id=29168") in Wine HQ which might be helpful for you. There are many gamers here in this forum. Some one might help you with this.

---

### Post by DarthKreeaj on 2012-03-25
I managed to navigate through to the install directory.  However, I have no idea how to edit files from the terminal.

---

### Post by ashwinrao on 2012-03-26
You can use '[vi]("http://www.computerhope.com/unix/uvi.htm")' command or '[gedit]("https://help.ubuntu.com/community/gedit")' for opening and editing files using terminal. Use 'sudo' with command in-case you encountered with permissions issues.

---

