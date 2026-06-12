---
title: "Where can i get a mp3 player ???"
date: 2006-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by d4rk on 2006-02-05
Like, im kinda new to linux, and ubuntu is the first Linux OS i try. I kinda liked it, but then i wanted to play off some mp3\s, and ubuntu couldn\t do this... So i went online with the great firefox explorer, and searched for something like > mp3 player for linux... I found several players, and i dl them. When i extract the files, all I get is a whole bunch of files:???:     I read a file that is named INNSTALL, and here it says something about COMPILING :confused:   Yeah, think i know what compiling is \\:D/ 
Anyways, all i want is the possibiliti to play of MP3.s !

Thanks for all the help i may get !   
Yes, I know this may shouldn\t be posted just here... or maybe it should >D

---

### Post by Perfect Storm on 2006-02-05
```
sudo apt-get install beep-media-player
```

---

### Post by d4rk on 2006-02-05
[QUOTE=Artificial Intelligence]```
sudo apt-get install beep-media-player
```[/QUOTE]


Ehh.... Where should i write in that txt ?


IM REALY SRY FOR BEING SUCH A N00B!

---

### Post by d4rk on 2006-02-05
[QUOTE=Artificial Intelligence]```
sudo apt-get install beep-media-player
```[/QUOTE]


Hey, I use that command, and like it asks for a psw, and I write in my account psw, and then this happens >

Couldnt find the beep media player...

---

### Post by d4rk on 2006-02-05
Guess linux isn\t for me :cry:

---

### Post by Casey on 2006-02-05
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by d4rk on 2006-02-05
Non of the commands works... Isn\t this a pretty bad thing in linux... Why cant they just have a standard innstall file ??    And i cant have norwegian letters:mad:

---

### Post by Lord Illidan on 2006-02-05
First off.

Linux does have a multimedia player. Your difficulty in installing it is because you are new, not because linux sucks.

Second.

You are using AMD 64 Ubuntu, I guess. You will have a far better experience if you use the standard x86 installation. Since AMD 64 bit processers can run 32 bit instructions, you won't have any problems, and regarding speed issues, there are hardly any.

Third.

Have you read the help? It is that lifebouy on the taskbar at the top. Read it.

Fourth.

You might want to follow this howto to add repositories :

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by d4rk on 2006-02-05
[QUOTE=Lord Illidan]First off.

Linux does have a multimedia player. Your difficulty in installing it is because you are new, not because linux sucks.

Second.

You are using AMD 64 Ubuntu, I guess. You will have a far better experience if you use the standard x86 installation. Since AMD 64 bit processers can run 32 bit instructions, you won't have any problems, and regarding speed issues, there are hardly any.

Third.

Have you read the help? It is that lifebouy on the taskbar at the top. Read it.

Fourth.

You might want to follow this howto to add repositories :

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")[/QUOTE]

Thanks for some answers. Im realy sry if it looked like I ment Linux sucks. It wasn\t  that i ment.   Im just totaly new to it, and need some help. Ill take a look at what u have told me :)

---

### Post by professor_chaos on 2006-02-05
Dont feel bad about it d4rk. I remember when I first started using Linux, everything was a little foreign and confusing. But after a while it because easy. The wiki guide is very helpful, read that and then try doing some google/ubuntu search bar searches for problems your having, as there is a lot of info out there that would probably relate.

You'll find that after adding the right repositorys you'll have more software that you can ever want to install at your fingertips. Games, media players, etc. The only way to find out if linux is right for you, just give a little time, enough time to learn the basics, and then decide. Good luck

---

### Post by z_diver on 2006-02-05
Rarely do people just want mp3 capability.  If you want to be able to play most multimedia formats I'd suggest installing 'automatix'.  At the moment that is the quickest and easiest method to install multimedia codecs and plugins such as acroread for your browser in addition to the latest firefox(1.5) for Ubuntu.  It's a virtual swiss army knife.  If you are using a laptop, I'd recommend that you do not install the numlock function as login problems could result.  Have fun.

---

### Post by d4rk on 2006-02-06
[QUOTE=professor_chaos]Dont feel bad about it d4rk. I remember when I first started using Linux, everything was a little foreign and confusing. But after a while it because easy. The wiki guide is very helpful, read that and then try doing some google/ubuntu search bar searches for problems your having, as there is a lot of info out there that would probably relate.[/QUOTE]

Thx for that, Ill try some googling and using some forums.. And see what i can get out of it. As told, im a total newbee in Linux...

E       Why cant I just dl a Install.exe file and innstall a mp3 player ??  Like Winamp or something. That would
         have been way better.

---

### Post by hasek on 2006-02-06
you can also go to [http://www.xmms.org/](http://www.xmms.org/), it is the most well known unix multimédia player. it looks like winamp

therefore the name for xmms was x11amp before :-)

very fast on amd64 machines very low cpu

---

### Post by d4rk on 2006-02-06
[QUOTE=hasek]you can also go to [http://www.xmms.org/](http://www.xmms.org/), it is the most well known unix multimédia player. it looks like winamp

therefore the name for xmms was x11amp before :-)

very fast on amd64 machines very low cpu[/QUOTE]


That\s probably a very good player!
*since i have used winamp, and think that rocks*

But where is the innstall file ?       I cant innstall the program, and play my mp3\s.

---

### Post by aruckert on 2006-02-06
Hi d4rk!

You'll hardly find any install files in Linux. Installation of applications is done differently.

Most of the time you can get the applications you need from the Ubuntu repositories using an application called Synaptics (you'll find it in the Administration menu).

Synaptics reads application repositories available on the internet, lists the applications avaible and lets you choose the ones you want.

The problem with mp3 is that it is copyrighted, so mp3 decoding is not included in the official Ubuntu repositories. What you have to do is tell Synaptics to read from a "unofficial" repository called Universe where you can get mp3 decoding applications and other copyrighted stuff.

There are two ways to do this:
1.- You can edit a file called /etc/apt/sources.list and uncomment the Universe repository.
Here's a howto: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2.- Add the Universe repository directly from Synaptics menu. What Synaptics does is write /etc/apt/sources.list without you noticing it.

Regarding mp3, you may have noticed that there is an application called Rythmbox. Rythmbox is perfectly capable of decoding mp3, it just needs the decoder to be installed.

Once you have enabled the Universe repositry, you can use Synaptics to search for gstreamer. To play mp3 you meed gstreamer0.8-mad. You'll find other insteresting codecs for other purpuses too :)

In any case, I strongly advise you to take a look at: [http://ubuntuguide.org/](http://ubuntuguide.org/)

Good luck!

---

### Post by d4rk on 2006-02-06
I finaly made it with all the help needed from Hasek, i just wanna thank u wery much for the help u gave me over msn. 

My problem was that im not used to linux, so i was looking for a innstall file all the time, instead of using this so called synaptic feature. Now i have innstalled XMMS trough synaptic by help from Hasek, and it all works fine.. for now. :D 

So I guess my next project will be the screen resolution... :-k 

Just 1 more thing, I see this $ UBUNTU CUPS, like the first cup of ubuntu$ .. how do i get the second ?

Thanks for help..

---

### Post by Perfect Storm on 2006-02-06
Screen resolution, read it carefully:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by hasek on 2006-02-07
[QUOTE=d4rk]I finaly made it with all the help needed from Hasek, i just wanna thank u wery much for the help u gave me over msn. 

My problem was that im not used to linux, so i was looking for a innstall file all the time, instead of using this so called synaptic feature. Now i have innstalled XMMS trough synaptic by help from Hasek, and it all works fine.. for now. :D 

So I guess my next project will be the screen resolution... :-k 

Just 1 more thing, I see this $ UBUNTU CUPS, like the first cup of ubuntu$ .. how do i get the second ?

Thanks for help..[/QUOTE]

You are welcome, xmms is the fastest way to get a winamp like resistant mp3 player in 5 minutes and some clicks no need to read documentation, or adding extra mp3 decoding applications.

---

### Post by javaTard on 2006-02-09
Every time I think i found a reason to not like ubuntu Linux,  these forums pull my butt out of the fire.
You have all made me a rabid Ubuntu user

---

