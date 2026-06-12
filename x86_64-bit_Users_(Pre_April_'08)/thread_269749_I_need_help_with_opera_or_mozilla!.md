---
title: "I need help with opera or mozilla!"
date: 2006-10-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by 64bit_trouble on 2006-10-02
I'm trying to install either mozilla (not firefox) or opera on my 64bit system, I'm very new to this and I'm trying to use a website that will not allow me to use firefox. I have browsed pervious threads about forcing architecture, but I'm not having any luck. If anyone has any code or help they can swing my way it would really help out.

---

### Post by pay on 2006-10-02
I think that you can install opera with Automatix. To install Automatix do```
wget http://www.getautomatix.com/files/automatix-installer
chmod 755 ~/automatix-installer
./automatix-installer
```

---

### Post by 64bit_trouble on 2006-10-02
I have automatix and opera is not included.

---

### Post by pay on 2006-10-02
Oh okay then. It might not e included in the 64bit version. You can run a 32bit chroot but that might be overkill for seeing a webpage with a browser.

---

### Post by 64bit_trouble on 2006-10-02
i'm sorry I'm really new, but what does "*You can run a 32bit chroot*" mean?

---

### Post by pay on 2006-10-02
It basically means that you will have a 32bit ubuntu installation inside your 64bit installation. Have a look at these and decide weither it's for you or not.
[http://www.ubuntuforums.org/showthread.php?p=904320](http://www.ubuntuforums.org/showthread.php?p=904320)
[http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575)

---

### Post by fabertawe on 2006-10-02
Where's Kilz when you need him ;) Try his [How-To]("http://www.ubuntuforums.org/showthread.php?p=1174435") for 32bit Firefox and all the plugins. You can also try [Swiftfox]("http://www.getswiftfox.com/"). There is also an automated install for IE6 (via Wine) which worked flawlessly for me and will give you a fallback if you absolutely need to view something with Flash 8+ for example. Check [this thread]("http://www.ubuntuforums.org/showthread.php?t=267469&highlight=IE6+wine").

Paul

---

### Post by Colonel Kilkenny on 2006-10-02
I have no experience with 64bit systems but I think that you can install opera after you have downloaded the deb file from opera.com with: 
"sudo dpkg -i --force-architecture youroperadebfile.deb" or something similar.

---

### Post by Kilz on 2006-10-02
> **fabertawe said:**
> Where's Kilz when you need him ;) Try his [How-To]("http://www.ubuntuforums.org/showthread.php?p=1174435") for 32bit Firefox and all the plugins. You can also try Swiftfox. There is also an automated install for IE6 (via Wine) which worked flawlessly for me and will give you a fallback if you absolutely need to view something with Flash 8+ for example. Check [this thread]("http://www.ubuntuforums.org/showthread.php?t=267469&highlight=IE6+wine").

Paul

Im here, I also dont recommend Swiftfox, its non free software. You cant distribute it. The person who compiles it found a loophole in the mozilla license that alows him to change the license on what he compiles. Its kind of like a Tivo of browsers.
32bit Firefox and plugins are avilable from my howto. The link is in my signature. But if Im not around its also in the 64bit sticky thread for program howto's.
I also do not recommend surfing with IE under wine. For one or 2 must have sites its ok. But for general browsing its to big of a security risk.

---

### Post by 64bit_trouble on 2006-10-02
Everyone....thanks a lot I got the problem solved my forcing opera into 64bit. Everything is working great.

---

### Post by Stirling on 2006-10-02
Just to clarify Kilz's comment a bit, Swiftfox is provided free of charge and available through Automatix.  His definition of free differs from what most ordinary people consider it to mean.

---

### Post by Kilz on 2006-10-02
> **Stirling said:**
> Just to clarify Kilz's comment a bit, Swiftfox is provided free of charge and available through Automatix.  His definition of free differs from what most ordinary people consider it to mean.

It is NON free as in freedom. It is not redistributable. That makes it non free. This is a debian based distro. That definition is not strange in any way shape or form. It is a untruth to say it is.

---

### Post by tOz666 on 2006-10-02
Now you have successfully installed opera, you should see [this thread]("http://www.ubuntuforums.org/showthread.php?t=269170") below for making the plugins work with it ;)



</SPAM>

---

### Post by fabertawe on 2006-10-02
> **Kilz said:**
> Im here, I also dont recommend Swiftfox, its non free software. You cant distribute it. The person who compiles it found a loophole in the mozilla license that alows him to change the license on what he compiles. Its kind of like a Tivo of browsers.

I'm not familiar with Tivo but I get your point. I've been using Swiftfox since I started my Ubuntu (and Linux) adventure and don't feel passionately enough about Swiftfox's author's behaviour to switch to 32bit Firefox just yet but may change over at some point.

> I also do not recommend surfing with IE under wine. For one or 2 must have sites its ok. But for general browsing its to big of a security risk.

I've been wondering about this... what damage could be done?

Paul

---

### Post by Kilz on 2006-10-02
> **fabertawe said:**
> I'm not familiar with Tivo but I get your point. I've been using Swiftfox since I started my Ubuntu (and Linux) adventure and don't feel passionately enough about Swiftfox's author's behavior to switch to 32bit Firefox just yet but may change over at some point.
Tivo takes the linux operating system and because of a loophole in the glp makes it so you cant modify the software and run it on your tivo. Swiftfox takes the free Firefox code and through a loophole is able to change the license to whatever it wants on the compiled binaries. Both take whats basicly Free software and limit your freedoms.
I understand. It may have been something you were not aware of. You may not understand exactly who this hurts. After all it didn't cost you anything. But Redistribution is a software freedom the [Free Software Foundation]("http://www.gnu.org/philosophy/free-sw.html") believes in. The longer you use Free software, the more you may come to realize that its the freedoms that are important. I am realistic in my personal definition of Free Software. I will use free software over a non free software if the functionality that I need exists in the free software. An example of this is ATI drivers. I use the non free ATI drivers (non free because the source isn't available, but its redistributable) because the free ones do not have 3d acceleration. If they did I would uninstall the non free ones.
Swiftfox is basically Firefox. What makes it faster is how its compiled. Things are taken out of it or disabled so it starts faster. Once its running IMHO it isn't any faster than Firefox.
It isn't 64bit, its available for 64bit, bit its still a 32bit binary. Some people are under the mistaken belief that since its a says its compiled for 64bit, that its 64bit. It isn't. That's why 32bit plugins work on it.
So the Disadvantages (not free software) outweigh the advantages (starts 1 second faster) for me. Personally I think all users of Free software should stop using Non Free software where they can. If this happens we may get the people who make Non Free software to license it as Free software.



> **fabertawe said:**
> I've been wondering about this... what damage could be done?
Paul
Wine is a bug for bug implementation of Windows. Running IE could mess up other applications running under wine if it installs spyware or viruses into wine. Like I said, its ok if you want to use it for a few sites to limit the danger. But surfing all over with it is something I would not do.

---

### Post by Stirling on 2006-10-02
> **Kilz said:**
> Swiftfox takes the free Firefox code and through a loophole is able to change the license to whatever it wants on the compiled binaries.
It's not actually a loophole.  That is how Mozilla designed the license.  That is one reason why they have the source licensed MPL and not just GPL.  Yes there is a difference.

> **Kilz said:**
> I use the non free ATI drivers (non free because the source isn't available, but its redistributable) because the free ones do not have 3d acceleration. If they did I would uninstall the non free ones.
Do you also browse forums bashing ATI whenever you get a chance because they have non-free drivers?

> **Kilz said:**
> It isn't 64bit, its available for 64bit, bit its still a 32bit binary. Some people are under the mistaken belief that since its a says its compiled for 64bit, that its 64bit. It isn't. That's why 32bit plugins work on it.
It says 32-bit right on the web site.  It doesn't say it's compiled for 64-bit.  It is compiled for AMD64 in gcc, there is a difference.


It is too bad that you feel the need to bash Swiftfox whenever you find a post that mentions it.  I would love to have a civil discussion about this but from past experience I know that won't ever happen. I don't hate you and am not sure why you still feel the need to carry on your campaign against me.  It is all just software afterall.  There are way more important things in this world to campaign for.  :???:

---

### Post by Kilz on 2006-10-02
> **Stirling said:**
> It's not actually a loophole.  That is how Mozilla designed the license.  That is one reason why they have the source licensed MPL and not just GPL.  Yes there is a difference.
Its sad if anyone takes whats free and then limits the freedoms of others. I seriously dought they expected someone to limit the freedoms of others. You did that , not me. Rememebr the MPL lets you chose the license, you could have licensed that Free Software Code as FREE SOFTWARE. You chose to use a NON Free license.


> **Stirling said:**
> Do you also browse forums bashing ATI whenever you get a chance because they have non-free drivers?I dont bash anyone, you licensed Swiftfox under NON FREE terms. I didnt. You chose the license, wrote it up and signed it. Not my choice. I will continue to point out its NON FREE to whoever I chose to. Dont like it, to bad.


> **Stirling said:**
> It says 32-bit right on the web site.  It doesn't say it's compiled for 64-bit.  It is compiled for AMD64 in gcc, there is a difference. Its still a 32bit application. In this forum, the 64bit users forum, some people might mistake it for 64bit. It isnt. Thats the truth. Dont like it? To bad.


> **Stirling said:**
> It is too bad that you feel the need to bash Swiftfox whenever you find a post that mentions it.  I would love to have a civil discussion about this but from past experience I know that won't ever happen. I don't hate you and am not sure why you still feel the need to carry on your campaign against me.  It is all just software afterall.  There are way more important things in this world to campaign for.  :???:

Let me get this strait. The person who changed the license on Swiftfox to stop it being redistributed to Ubuntu users in a setup script thinks Im uncivil? :-k 
Simply change the license to a Free one and I stop pointing out it its NON Free Software. You have a lot of nerv coming here and accusing me of anything. I have almost 2k posts helping Ubuntu users. Im simply helping them see that you are limiting their freedom.

---

### Post by fabertawe on 2006-10-02
> **Kilz said:**
> Tivo takes the linux operating system...[snip]

I already got this, that's why I said I get your point ;) 

At the end of the day Swiftfox's author is doing something good for Ubuntu users and that has to be applauded (IMO).

Paul

---

### Post by Kilz on 2006-10-02
> **fabertawe said:**
> I already got this, that's why I said I get your point ;) 

At the end of the day Swiftfox's author is doing something good for Ubuntu users and that has to be applauded (IMO).

Paul
In the end of the day the Author of Swiftfox is limiting freedoms of Ubuntu users. Liming its inclusion in repositories, limiting its ability to be included in setup scripts, limiting the binary packages ability to be modified then distributed to make new users life easier. He is doing what he is doing for personal gain and already gets his reward. I think the **Bronks Cheer** is appropriate for him

---

### Post by fabertawe on 2006-10-03
> **Kilz said:**
> In the end of the day the Author of Swiftfox is limiting freedoms of Ubuntu users. Liming its inclusion in repositories, limiting its ability to be included in setup scripts, limiting the binary packages ability to be modified then distributed to make new users life easier. He is doing what he is doing for personal gain and already gets his reward. I think the **Bronks Cheer** is appropriate for him

I don't want to labour this anymore as you're repeating yourself now but I will just say he is not limiting **my** freedom as I have another browser to **choose** to use. By any definition having more choice is not limiting. I fully understand and comprehend your argument but I feel you are being over zealous in your criticism. Would you prefer he stopped producing Swiftfox just so you can feel better at the expense of user choice?

Paul

---

### Post by Kilz on 2006-10-03
> **fabertawe said:**
> I don't want to labour this anymore as you're repeating yourself now but I will just say he is not limiting **my** freedom as I have another browser to **choose** to use. By any definition having more choice is not limiting. I fully understand and comprehend your argument but I feel you are being over zealous in your criticism. Would you prefer he stopped producing Swiftfox just so you can feel better at the expense of user choice?

Paul
If you have Swiftfox installed IMHO he is limiting your freedom. You do not have the freedom to package that application as a deb, tar, zip, or even take the package he supplies and pass it on to a friend.
As for being over zealous. The Linux operating system and all free software is a result of someone being the same way. I really don't understand why any Linux user would use software that limits their freedom when the functionality exists in free software. Doing so sets a bad example and gives the perception that this is acceptable.
Rather than disable some things to make it start faster, not add anything to the code, then change the license to restrict freedoms. I would rather he not compile the Firefox code and rename it Swiftfox. I do not think it adds anything to user choice and simply takes away freedoms. 
Had he added things to Firefox , like Flock does, maybe my opinions would change.

---

