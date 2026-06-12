---
title: "64-bit Ubuntu Doesn't See 32-bit Program?"
date: 2008-12-31
forum: x86 64-bit Users
---

### Post by LaneLester on 2008-12-31
From encouragement I got in another thread, I just switched from 32-bit Intrepid to 64-bit Intrepid, realizing I might have to deal with one or more 32-bit programs. It turns out that I only have one such program for now, but I'm getting an error message that I'm not sure about.

The program that's the stopper for me is my weather station software. It's 32-bit, there's no 64-bit version, and no chance of the developer producing one. I tried executing it from the terminal and got this:

    root@PC1:/opt/wdisplayK# ./GoWeather.sh
    ./GoWeather.sh: line 14: ./WeatherD: No such file or directory
    root@PC1:/opt/wdisplayK# ./WeatherD
    bash: ./WeatherD: No such file or directory
    root@PC1:/opt/wdisplayK# 

WeatherD is present, in spite of the above error messages. Maybe that's how a 64-bit OS rejects a 32-bit app. But it leaves me not knowing what 32-bit libraries are needed.

Lane

---

### Post by Kilz on 2008-12-31
Is the file set to be executable?

---

### Post by hyperdude111 on 2008-12-31
you have to "cd" to the file. Then force the os to install it using dkpg if that fails install the 32 bit libraries, just do all of them it works for me.

---

### Post by rbmorse on 2008-12-31
Is there a really simple guide on how-to on this?  I never even considered the possibility, but I have a couple of 32-bit apps that I'd like to use from my 64-bit installation if such things can be done.

---

### Post by LaneLester on 2008-12-31
> **Kilz said:**
> Is the file set to be executable?
Well! It was executable for user and group, but not others. When I added others, it executed! What makes it strange to me is that this is in my /opt partition which is used by 32-bit Intrepid (and others) and the original permissions worked just fine.

Now I get this:
root@PC1:/opt/wdisplayU# ./GoWeather.sh
./WeatherD: error while loading shared libraries: libglib-1.2.so.0: cannot open shared object file: No such file or directory

So now I need to go looking for 32-bit libraries... I think my 32-bit Intrepid partition should do the job.

It may not come up in this case, but I'm wondering what one does if one has 32- and 64-bit libraries with the same filename.

Lane

---

### Post by LaneLester on 2008-12-31
I see that just copying the needed library from my 32-bit Intrepid partition to the 64-bit one doesn't do the job. The program still reports that it is not present.

So how do I install a 32-bit library with Synaptic? Use the sources.list from 32-bit Ubuntu Intrepid?

Doing an "install 'em all" won't work for me, because the libraries this program uses are the older versions and have to be specifically installed. For example the current version of libglib is 2.x and I need 1.2.

Lane

---

### Post by jocko on 2008-12-31
[getlibs]("http://ubuntuforums.org/showthread.php?t=474790") should be able to solve your dependencies for you.

The first "usage example" listed in the linked post should help you figure out how to do it.

---

### Post by LaneLester on 2008-12-31
> **jocko said:**
> [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") should be able to solve your dependencies for you.

The first "usage example" listed in the linked post should help you figure out how to do it.
Yesssssss! The program complained about needing three libraries (one at a time). After installing the getlibs package, I just entered "getlibs name-in-error-message" each time. getlibs figured out the exact package needed for each one.

Thanks to everyone who contributed to this thread.

Lane

---

### Post by jespdj on 2009-01-01
> **LaneLester said:**
> Well! It was executable for user and group, but not others. When I added others, it executed! What makes it strange to me is that this is in my /opt partition which is used by 32-bit Intrepid (and others) and the original permissions worked just fine.
This sounds like the user and group ownership settings of the directories and files for that program are not set right. If you do:
```
ls -l
```
in the directory, then what names do you see for user and group names? Do you see someting like "root root", "user user" (where 'user' is your own username) or do you see something else (perhaps even just two numbers)?

You can change the ownership of a directory and all the files in it (recursively) with the following command:
```
sudo chown -R user:user dirname
```
(where 'user' is ofcourse your own username again; you could also use 'root:root').

Note that you can use the 'man' command (which stands for 'manual') to get more information about terminal commands. For example:
```
man chown
```

---

### Post by LaneLester on 2009-01-01
> **jespdj said:**
> If you do:
```
ls -l
```
in the directory, then what names do you see for user and group names?
Thank you for that information. Almost everything in /opt is root root (I run as root). But the folder that contains those executables is 500 500. Inside the folder, the executables are root root.

I should say "were" above, because I've use the command you supplied to change everything to root root.

But for me the mystery remains why I've never seen this in 32-bit Ubuntu releases or other distros (Puppy and Crunchbang, for example). I always use the same /opt partition with all of them.

Lane

---

### Post by jespdj on 2009-01-01
The problem has nothing to do with 32-bit or 64-bit. This could just as well have happened with two 32-bit systems. So it's not a problem that has anything to do with 64-bit.

You've copied the files from one system to the other while preserving the ownership information. The new system doesn't know the user and group from the old system, so it shows them as numbers (user 500 and group 500).

---

### Post by hyperdude111 on 2009-01-01
the reason copying the /usr/lib/ from 32 bit to 64 did not work was because in 64 bit you have to place the 32 bit libs in /usr/lib32/ rather than lib.

---

### Post by Kilz on 2009-01-01
> **hyperdude111 said:**
> the reason copying the /usr/lib/ from 32 bit to 64 did not work was because in 64 bit you have to place the 32 bit libs in /usr/lib32/ rather than lib.

It could also be quite a problem if you copy over libraries that your system needs like that. The 64bit system would no longer see them.

---

