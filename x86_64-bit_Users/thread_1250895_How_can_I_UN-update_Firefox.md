---
title: "How can I UN-update Firefox?"
date: 2009-08-27
forum: x86 64-bit Users
---

### Post by fortyG on 2009-08-27
I have Ubuntu 7.04 and last night I updated Firefox to 2.0.0.17
<Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.17) Gecko/20061201 Firefox/2.0.0.17 (Ubuntu-feisty)>
but it's not working right. I had a hell of a time getting it to open, and discovered that I could do so using the Terminal, but it will close if I close the terminal. Also, certain features don't work, like Street View in Google (not okay! I love street view!) Probably some more I forgot I noticed/haven't discovered yet.

Maybe I could fix what's wrong but it might be easier to go back a step to an earlier release (as I imagine it, roll back the update.) What do you recommend?

Obviously I am one of those people who installed Ubuntu because it was free and is not actually very knowledgeable. It's a good thing there is a community I can ask for help!

---

### Post by j7%&lt;RmUg on 2009-08-27
Well is there a specific reason why your still using 7.04? How did you install 2.0.0.17? If you are running a program through a terminal and close the terminal the process gets killed, so the program closes.

---

### Post by Yellow Pasque on 2009-08-27
How did you update it? Ubuntu doesn't offer updates for Feisty anymore, so my guess is that you installed a third-party version of FF (possibly a 32-bit version).

---

### Post by fortyG on 2009-08-27
I tried to update from 7.04 and it didn't work (lately I get "Could not find the release notes. The server may be overloaded." I used to get a different error message, I forget what.) I poked around the Ubuntu site but this page [http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710) suggested I follow the instructions on this page [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) which only discusses 9.04, and I don't know how to apply that to 7.10. Then I decided I had better things to do and went back to them.

How did I install 2.0.0.17... OH! I remember now. Firefox suggested it itself! And I thought, oh, new features, okay! Why not? So I followed the instructions. I wish I could tell you what they were. I don't remember exactly what I did. Firefox did most of the work.

---

### Post by Yellow Pasque on 2009-08-27
> I tried to update from 7.04 and it didn't work 
FF 2.0.0.17 is available from the Feisty repositories, but you have to edit your sources list, because those repos are archived on a different server since Feisty is no longer supported. See: [http://ubuntuforums.org/showthread.php?t=1188175](http://ubuntuforums.org/showthread.php?t=1188175)

---

