---
title: "My Ubuntu x86_64 experience! + HOWTO's"
date: 2007-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by LuisGMarine on 2007-05-14
So after digging around for sometime, I finally made the move over to a complete Ubuntu 64-bit system.  I got the partitions running just the way I wanted them to be, set a different partition for /home , / , and /mystuff ( where I keep my music/videos/games ).  I got the applications I wanted the most to work, which are Cedega 6.0, Frostwire, Azureus, and Firefox with Flash + Java, here are the things that I did to get these applications installed.  For some people it might help them too!

**[SIZE="4"]_[COLOR="DarkOrange"]Cedega 6.0 + Ubuntu Feisty AMD-64[/COLOR]_[/SIZE]**

I wrote a quick HOWTO on this on my new blog, the link is below:
[Cedega + Ubuntu Feisty AMD64 install howto]("http://luisgmarine.blogspot.com/2007/05/installing-cedega-60-on-ubuntu-704.html")

**[SIZE="4"]_[COLOR="DarkOrange"]Firefox with Flash + Java[/COLOR]_[/SIZE]**

For this part I used the script, and howto provided by Kilz, simply an outstanding script, worked like a charm.  Many thanks go out to him:
[URL="http://ubuntuforums.org/showthread.php?p=1174435"]
Firefox with flash/java[/URL]

[SIZE="4"]_[COLOR="DarkOrange"]**Azureus + Ubuntu Feisty AMD-64**[/COLOR]_[/SIZE]

This was quite a development for me, I found out that Azureus provides and AMD64 version of their program.  To me that was great news, and the install was a complete breeze.  Here's how:

First download the AMD64 version of Azureus from this website [here.]("http://azureus.sourceforge.net/download.php")

Next I untarted the file, using the command below, in return it created a folder named 'azureus':
```
tar -xjf Azureus_2.5.0.4_linux-x86_64.tar.bz2 
```
Navigate to the folder named azureus, keep in mind, this is the folder where the script to run the program is located.  Once you are in the folder 'azureus' type this in to run the Azureus installation script.  You can do it two ways:

One, run it from terminal, cd into the azureus folder and type this in:
```
./azureus
```
Second you can open up Nautilus and double click on the file named azureus , then click on " Run in Terminal "

After that follow the on screen directions, and you are good to go!  Here is another link to a quick way to increase your speed on Azureus, I don't think a lot of people know about this option.  NOTE: THIS WORKS FOR BOTH AMD64 AND 32-BIT UBUNTU.  IT IS NOT PLATFORM SPECIFIC!

[Azureus good settings]("http://www.azureuswiki.com/index.php/Good_settings")

[SIZE="4"]_[COLOR="DarkOrange"]**Frostwire + Ubuntu Feisty AMD64**[/COLOR]_[/SIZE]
Download the .deb from the [Frostwire website.]("http://www.frostwire.com/?id=downloads")
Then install the package with dpkg + forcing the architecture:
```
sudo dpkg -i --force-architecture *packagename.deb* 
```
Substitute *packagename.deb* with the actual frostwire .deb

So there it is, my Ubuntu experience.  I want to think the people who helped convince me a little to give it a try, and I can't say that I'm disappointed.  Hope these little howto's help someone along the line, and I hope to see you around in the forums!  Peace!

---

### Post by LuisGMarine on 2007-05-15
I would also like to add that my dmix and sorround sound work out of the box!  Amazing!  I never could get either or to work back in 32-bit feisty, always gave me trouble!  Here comes AMD64-Ubuntu to save the day, then there are people still out there that say how Ubuntu-AMD64 isn't ready for mainstream yet, lmao! :lolflag:

---

### Post by stmiller on 2007-05-15
Hey great thanks I'm going to check this out on my amd64 box.

[And PS: the cedega link doesn't work.]

---

### Post by Cappy on 2007-05-15
Cedega is double-click easy to install anyway.

---

### Post by LuisGMarine on 2007-05-15
Not double click for say.  I did need a couple of extra packages, the ia32-libs didn't fix all the problems.  

Even though it might be easy for you, keep in mind that this might help new people out in the future.  People are impatient, me and you know that.  The second that they see something doesn't work, they start freaking out and start bashing on AMD64 , saying things like its not " mature " enough.  

Trust me, I used to be one of those pricks :)

Anyhow, yeah I noticed the link doesn't work either, going to fix it right now.

---

### Post by struess on 2007-05-31
Thanks LuisG..  concise and functional post :)

---

