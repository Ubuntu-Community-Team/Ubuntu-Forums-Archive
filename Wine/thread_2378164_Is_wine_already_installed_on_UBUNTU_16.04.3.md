---
title: "Is wine already installed on UBUNTU 16.04.3?"
date: 2017-11-20
forum: Wine
---

### Post by ultratamale on 2017-11-20
And if not, how do you install it? And on that note, how do I install the programs from the program store? I click on the available on software center button and then I get a message that I got to choose and app to do that. What app?


And why does WINE download so fast? My connections is slow and should take half a minute, but it shows instantly.

---

### Post by ultratamale on 2017-11-20
When I download WINE it downlaods almost instantly even though it should  take half a minute, and in the Archive Manager I always see an older  file for it, downloaded earlier today no matter how many times I delete  it from downloads and from the Archive manager. Why is this?

---

### Post by ultratamale on 2017-11-21
[ATTACH=CONFIG]277613[/ATTACH]

Like this. Why are there 2 times here for the same file?

---

### Post by ultratamale on 2017-11-21
I hope I did not just do something stupid. I did what this page said [http://sourcedigit.com/22831-install-wine-stable-2-0-3-release-on-ubuntu-17-10](http://sourcedigit.com/22831-install-wine-stable-2-0-3-release-on-ubuntu-17-10)/ 
 
 which was to jam this 
 
 sudo apt-get update 
 wget -nc [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key) && sudo apt-key add Release.key 
 sudo apt-add-repository [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu)/ 
 sudo apt-get update 
 sudo apt-get install --install-recommends winehq-stable 
 
 into the terminal 
 
 it did some things 
 
 then I got "sudo apt-get install --install-recommends winehq-stable" 
 
 then I hit enter then Yes... 
 
 Did I do wrong? 
 
 
 This was for 17.10, but wouldn't it be the same for 16.04.3? 
 
 How do I know if it is actually installed? 
 
 
 Installing quake says I need gecko and mono. What exactly should I search for in the software store?

I did not install gecko and mono as I do not know how.

Then I got the errors shown below when I installed quake.[ATTACH=CONFIG]277615[/ATTACH][ATTACH=CONFIG]277616[/ATTACH][ATTACH=CONFIG]277617[/ATTACH][ATTACH=CONFIG]277618[/ATTACH][ATTACH=CONFIG]277619[/ATTACH]

[ATTACH=CONFIG]277620[/ATTACH][ATTACH=CONFIG]277621[/ATTACH][ATTACH=CONFIG]277622[/ATTACH][ATTACH=CONFIG]277623[/ATTACH][ATTACH=CONFIG]277624[/ATTACH]

I have more files to upload but it won't let me upload them... Kinda important to upload them here...and how do I delete the excess?

---

### Post by slickymaster on 2017-11-21
*Thread moved to **Wine**.*

---

### Post by ultratamale on 2017-11-21
Okay...Oh, and right now I am just trying to run quake.

I keep getting winsockIPX bind failed whenever I try to start quake. And how do I install Gecko and Mono? I have downloaded both 32 and 64 bit gecko from WineHQ, but how do I use it? And what am I supposed to do with Mono?

How do I undo all this and why aren't there simple instructions on how to do this?

I think it would be best if I just reload the operating system and start this over from scratch. How exactly do you install wine? I see on WineHQ there is stuff to download, but what do I do with it once it is downloaded? And what do I do with the Gecko and Mono from WineHQ? I am trying to play games off GOG.com. Right now I just wanna play quake.

---

### Post by slickymaster on 2017-11-21
Please be patient and understand that this is a forum populated by VOLUNTEER users from every time zone around the world. That means that some questions may go unnoticed by the person with the perfect answer. In such cases, it is appropriate to bump a thread (by simply adding a new post with the word "bump") if you do not get a reply in a reasonable amount of time.

We have relaxed the 24 hour restriction on bumping. A 12 hour bump would expose your thread to a different group of people somewhere in the world.

---

### Post by ajgreeny on 2017-11-21
Threads merged to avoid total confusion.

---

### Post by slickymaster on 2017-11-21
Also merging this one with the ones ajgreeny merged.

[B][U]@ultramale:

[/U][/B]Please stop creating duplicate threads, it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

### Post by ultratamale on 2017-11-22
[I didn't realize those would be considered duplicate as they seemed different enough to me.

Anyway. I will upload some pics of the errors but...

[ATTACH=CONFIG]277631[/ATTACH][ATTACH=CONFIG]277632[/ATTACH][ATTACH=CONFIG]277629[/ATTACH][ATTACH=CONFIG]277633[/ATTACH][ATTACH=CONFIG]277630[/ATTACH]


Now I am following the instructions I have thus far set forth:
 
 
ALWAYS TYPE IN COMMANDS!!! DO NOT COPY AND PASTE THEM!!! THEY DO NOT WORK WHEN YOU COPY AND PASTE THEM!!! AND DO NOT INCLUDE THE QUOTATION MARKS WHEN YOU ENTER THE COMMANDS INTO THE TERMINAL WINDOW!!!
 --------------------------------------------------------------------------------------------------------------------------
Instructions for installing AMD GPU drivers.
 
1)  I download the driver file from [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx)
  
 
  Go down to the part where it says Ubuntu file. At the time of this writing it looked like &#8220;[AMDGPU-Pro Driver Version 17.40 for Ubuntu 16.04.3]("https://www2.ati.com/drivers/linux/ubuntu/amdgpu-pro-17.40-492261.tar.xz")&#8221;
 
 
 I download the file directly to the temporary folder I made on my desktop. But you can also copy and paste the downloaded file to a temporary folder. I called my folder &#8220;AMD driver&#8221; or something like that.
 
 
 2) STAY ONLINE!
 
 
 3) Right click on the downloaded file and select &#8220;extract here&#8221; (once it is in its own folder)
 
 
  4) Right click on home screen and open terminal window. Paste &#8220;dpkg -l amdgpu-pro&#8221; into the terminal. This tells me if any AMD drivers are installed. None were. Great!
 
 
 5) Right click ON THE WINDOW OF THE FOLDER THAT CONTAINS THE DOWNLOADED AND EXTRACTED DRIVER!!! and then left click open terminal in the menu that shows.
 
 
 6) In my case I inserted &#8220;cd amdgpu-pro-17.40-492261&#8221; into the command terminal. In your case you will replace the &#8220;17.40-492261&#8221; with whatever number is on the file name.
 
 
  7) Then  put &#8220;./amdgpu-pro-install &#8211;y&#8221; into the command terminal and hit enter.  Then  hit enter and typed in my password (the password will not show when you type it in!). Be patient. Don&#8217;t do anything until you see your user name ( it will be in color) again.
 
 
 8) Then type in &#8220;sudo reboot&#8221;. You can be offline for this part.
 
 
 9) After restarting and logging in, right click on the home screen and type &#8220;groups&#8221;. It will show some data
 
 
 10) Then type &#8220;sudo usermod -a -G video $LOGNAME&#8221;. Type in your password again when prompted. (it will not show as you type it!). It will seem as though nothing happened. I think this is normal. Now log out and log in again.
 
 
 11) And I think that is it!
 
 
These instructions are a modified version of the instructions found here [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)  and are to be used for Ubuntu and AMD drivers.

 
Now to instal WINE. Instructions on how. Stay online while doing this.
1) Right click on the home screen and select open terminal window.
2) Type &#8220;sudo dpkg --add-architecture i386&#8221; into the terminal window. Type in your password when asked for it and hit enter. It will seem like nothing happened.
3) Then type in &#8220;wget -nc [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key)&#8221; and hit enter.
4)  Then type in &#8220;sudo apt-key add Release.key&#8221; and hit enter. It will say OK.
5) Then type in &#8220;sudo apt-add-repository [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)&#8221; and hit enter. It will seem like it did nothing.
6)  Then type in &#8220;sudo apt-get update&#8221; and hit enter. Some stuff will happen.
7)  Then type in &#8220;sudo apt-get install --install-recommends winehq-stable&#8221; and hit enter. You want the stable version if you are reading this. Select Yes. And a bunch of stuff will happen. Be patient and don&#8217;t do anything until your username appears again in color. Close the terminal window.

Now to install Quake from GOG.com
1) Download Quake from GOG.com after you buy it.
2) Put it in a folder and name the folder &#8220;Quake&#8221;
3) Right click on the file and hover the cursor over &#8220;open with&#8221;.
4) Then click on &#8220;Wine Windows Program Loader&#8221;.
5) Install the Gecko and Mono stuff when promted. Just click &#8220;Install&#8221;
7) When I figure out how to get all the error to stop I will finish writing this.
----------------------------------------------
Instilation odyssey notes:
  Didn't think they were duplicate anyway. I reloaded Ubuntu and am starting over from scratch. I would like to note, before I begin, that when reinstalling Ubuntu, one time it froze up right after the part where you click restart to finish the install. It had some black page with white letters and digits and stuff in the upper right corner. Anyway, I redid the install and that didn't happen.

Please sticky this. It will help many newbies like me.


1) This time I installed the Ubuntu 16.04.3 AMD drivers for my RX560
 a) I did what this page said [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)
 b) on the part where it says to extract, just make a new folder and paste the downloaded file there, then right click on it and select "extract here". Don't bother with the command line junk in this part.
 c) Where it says install... right click on the window of the folder you extracted the tar file into. Do not right click on the home screen! Right click on the folder window! Then select open terminal.
 Insert (don't include the quotation marks!) "cd amdgpu-pro-17.40-492261" and hit enter. The AMD website is outdated on this little part. When you insert this command look at the extracted        file name. If this is outdated by the time you read this then insert "cd amdgpu-pro-NN.NN-NNNNNN" where you replace the N's with the exact number on the file just like I did earlier in this paragraph.
 d) then insert " ./amdgpu-pro-install -y" into the terminal window. 
 e) then very carefully insert your password. As you type it your cursor will not move nor will the password show. When you have it correctly typed in then hit enter. Make sure you are online then hit enter. The first time i did this I was not online when I hit enter and it was not able to complete the task after hitting enter. In this case I went online, then typed "./amdgpu-pro-install -y" in again and hit enter. Much more stuff happened this time.
 f) then type in "sudo reboot" and hit enter again and your computer will restart
 
 
 
 
  Personally, after reboot I opened a terminal window and entered &#8220;dpkg -l amdgpu-pro&#8221; to see if it had all gone well.
 
 
 I got &#8220;u75@75:~$ dpkg -l amdgpu-pro
 Desired=Unknown/Install/Remove/Purge/Hold
 | Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
 |/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
 ||/ Name           Version      Architecture Description
 +++-==============-============-============-=================================
 ii  amdgpu-pro     17.40-492261 amd64        Meta package to install amdgpu Pr&#8221;
 
 
 I don&#8217;t know if that is good or bad. I guess since I got lower case it is all good? I was worred about the part where I tried to install it while I was not on the net. As some files were not installed due to me not being on the net when I first entered &#8220;./amdgpu-pro-install -y&#8221; I was worried that I duplicated the files that were installed. What are you supposed to do if a AMD GPU driver is already installed and shows when you enter &#8220; dpkg -l amdgpu-pro&#8221;? Did I screw up?
 
 
 
 
 g) Okay, So, I worried that I screwed up. So, after reading farther down on that page I learned I could undo everything by simply inserting &#8220;amdgpu-pro-uninstall&#8221;. So I did! Yay! Now I can restart this the RIGHT way!
  
 
  
 
  
 
REDO!!! ALWAYS TYPE IN COMMANDS!!! DO NOT COPY AND PASTE THEM!!! THEY DO NOT WORK WHEN YOU COPY AND PASTE THEM!!! AND DO NOT INCLUDE THE QUOTATION MARKS WHEN YOU ENTER THE COMMANDS INTO THE TERMINAL WINDOW!!!
  
 
  This is what I am doing now!
  
 
  1)  I am redownloading the driver file from [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx)
  
 
  Go down to the part where it says Ubuntu file. At the time of this writing it looked like &#8220;[/SIZE][AMDGPU-Pro Driver Version 17.40 for Ubuntu 16.04.3]("https://www2.ati.com/drivers/linux/ubuntu/amdgpu-pro-17.40-492261.tar.xz")&#8221;
 
 
 I download the file directly to the temporary folder I made on my desktop. But you can also copy and paste the downloaded file to a temporary folder.
 
 
 2) This time I will stay online!
 
 
 3) Right click on the downloaded file and select &#8220;extract here&#8221;
 
 
  4) Right click on home screen and open terminal window. Paste &#8220;dpkg -l amdgpu-pro&#8221; into the terminal. This tells me if any AMD drivers are installed. None were. Great!
 
 
 5) Right click ON THE WINDOW OF THE FOLDER THAT CONTAINS THE DOWNLOADED AND EXTRACTED DRIVER!!! and then left click open terminal in the menu that shows.
 
 
 6) In my case I inserted &#8220;cd amdgpu-pro-17.40-492261&#8221; into the command terminal. In your case you will replace the &#8220;17.40-492261&#8221; with whatever number is on the file name.
 
 
  7) Then I put &#8220;./amdgpu-pro-install &#8211;y&#8221; into the command terminal and hit enter. It failed the first two times because I pasted it into the terminal instead of typing it in.
 
 
 8) Then I hit enter and typed in my password (the password will not show when you type it in!)
 
 
  9) Now I will re-enter &#8220;amdgpu-pro-uninstall&#8221; to start all over again :(
  
 
 10) Now I am redoing 1-8. This time I am TYPING it all in.
  
 
  11) Then type in &#8220;sudo reboot&#8221; and be patient while it restarts. You can be offline for this part.
  12) Then I right clicked on the home screen, selected open terminal, and typed in &#8220;groups&#8221; and got some info
  
 
  13) Then I typed in &#8220;sudo usermod -a -G video $LOGNAME&#8221; and then typed in my password. It will seem as though nothing happened. I think that is normal.
 
 
 14) Now, log out and then in again
 
 
 15) I am redoing everything AGAIN just to make sure. Don&#8217;t want to waste time going forward if it is done wrong. Type right click on the home page and click open terminal. Then I type &#8220;amdgpu-pro-uninstall&#8221;. Then I reboot.
 After this I did what is shown in the instructions above.

---

### Post by ultratamale on 2017-11-22
Here is the winsock IPX bind fail image. I can only post 5 images per post. That is why I am making this post.
[ATTACH=CONFIG]277634[/ATTACH]




I found this "This is an unsual error. You can work around it by running the game with the **-noipx**  parameter (simply add it to the launch properties), but you should  probably also check your OS network options for related settings or  protocols and disable them if possible."

here

[http://steamcommunity.com/app/2310/discussions/0/882962960833509394/](http://steamcommunity.com/app/2310/discussions/0/882962960833509394/)

But how do you "add it to the launch properties"? And what exactly does that do?

---

### Post by slickymaster on 2017-11-22
**_@ultramale_**:

I have completely edit your post [here]("https://ubuntuforums.org/showthread.php?t=2378164&p=13713899&viewfull=1#post13713899"), due to fact that you haven't complied to the forum posting guidelines to which I now redirect your attention and to which I do advise to have a thorough read: [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945")

Also, typing in all caps is Internet code for shouting, which eventually can be regarded as a crutch for the angry and inarticulate, and it is rude. Please refrain yourself from doing it.

---

