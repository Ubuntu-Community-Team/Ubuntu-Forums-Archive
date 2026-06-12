---
title: "Can I install two instances of WINE?"
date: 2008-10-06
forum: Wine
---

### Post by X-Legs on 2008-10-06
I want to know if it is possible to install two instance of WINE. One would be the stable 1.0 release and the other will be tied to the repository of updated (but less stable) WINE releases. I don't want anything that works to be changed by a later release.

If you do know, please explain to me in a n00bish way. I am a slight n00b in Linux (knowing zip in the command line.)

Thanks

---

### Post by david_kt on 2008-10-07
> **X-Legs said:**
> I want to know if it is possible to install two instance of WINE. One would be the stable 1.0 release and the other will be tied to the repository of updated (but less stable) WINE releases. I don't want anything that works to be changed by a later release.

If you do know, please explain to me in a n00bish way. I am a slight n00b in Linux (knowing zip in the command line.)

Thanks

Yes, but you have to compile the stable one you want to keep at different place, and let the new wine to be updated frequently at the default place.

To do that, this is the step:

Prepare dependency:

```
sudo apt-get build-dep wine
```

Download the source code of wine 1.0 from [here]("http://downloads.sourceforge.net/wine/wine-1.0.tar.bz2?modtime=1213719421&big_mirror=1")

Extract it, open terminal and cd to that directory.

And than configure wine passing non-default variable, for example as follow:

```
./configure --prefix=/home/username/wine
```

The reason to install it in home directory is to avoid messing up with system file. If it could configure without any problem, continue with make:

```
make depend && make
```

It would take sometimes to make. If everything is ok (wine is already build) then install it WITHOUT SUDO (as it is install in home directory).

```
make install
```

If it is completed, you could run the wine-1.0 by using absolute path:

```
/home/username/wine/bin/wine yourprogram.exe
```

Or you could make a link to /usr/bin/wine-1.0 for example, linking to /home/username/wine/bin/wine. If you do this, you could run using:

```
wine-1.0 yourprogram.exe
```

Hopefully it is clear enough for you.

DK

---

### Post by X-Legs on 2008-10-07
Is it possible to do the same with wine-doors? Or if there is a more user friendly GUI, can you kindly suggest it to me?

Thanks

---

### Post by david_kt on 2008-10-07
> **X-Legs said:**
> Is it possible to do the same with wine-doors? Or if there is a more user friendly GUI, can you kindly suggest it to me?

Thanks

I have not tried wine doors, but I am sure wine doord just create bottles, not wine version. Even the crossover also only using 1 wine version, but many bottles.

I have not tried to use multiple wine as well. The above steps I tried just to answer your questions, and so far I am not using it yet.

I could make script with gui to make it easy to install multiple wine, but that would take sometimes for me to write.

DK

---

### Post by david_kt on 2008-10-09
I have just completed an installer to install multiple wine. Please check out below link:

[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

DK

---

