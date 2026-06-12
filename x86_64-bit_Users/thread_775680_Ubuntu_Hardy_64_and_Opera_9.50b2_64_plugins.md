---
title: "Ubuntu Hardy 64 and Opera 9.50b2 64: plugins"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by sjeps on 2008-04-30
Hi everyone i need some help.

After few days i managed to install opera 9.50b2 x64 on my ubuntu 8.04 x64. I also installed the 32bit flash plugin (couldnt find 64 one)

Now the problem is...

how can i watch streaming videos on opera? i mean, totem doesn't work on opera and mplayer seems to don't work.

Also, what about java? Tried something without success..

---

### Post by studo77 on 2008-05-03
Just bumping this one up. Getting a Sun Java on it would be very sweet for my use. The streaming would also be nice.

---

### Post by fraia on 2008-05-03
A note about the video - I use VLC and have never had any problems, but honestly i don't use it too much.

about Java... 
I have not been able to get 64-bit opera to work with Java. (Note there is no 64bit Java, so you have to use the 32bit). Opera claims that their wrappers in 64 bit opera will support 32 bit plugins and i think it works for Flash, but I have had no luck with Java.

Here's how to get 32bit opera working on your 64bit Ubuntu WITH 32bit java.
 Go to the opera website [http://www.opera.com/download/?ver=9.50b2](http://www.opera.com/download/?ver=9.50b2) and under 'distrobution and vendor' choose: other/static DEB
download it and install:

```
sudo dpkg -i --force-architecture opera-static-9.5b2-20080422.1-static-qt_en_i386
```


if you want the latest Java, get it from sun [http://www.java.com/en/download/manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/manual.jsp?locale=en&host=www.java.com:80)
choose the 'linux(self-extracting file)' and copy it to your java folder, probably something like:
```
sudo mv jre-6u5-linux-i586.bin /usr/lib/jvm
cd /usr/lib/jvm
sudo chmod 755 jre-6u5-linux-i586.bin
sudo ./jre-6u5-linux-i586.bin
```
this should extract java...
then in opera->tools->preferences->advanced->content->java options
type the path to libjava.so and other libraries
for me it was
```
/usr/lib/jvm/jre1.6.0_05/lib/i386
```
Alternatively you can also put this in the ~/.opera/javapath.txt file -should do the same thing.

cheers

---

### Post by Sef on 2008-05-04
I downloaded Sun's OpenJDK.  It is the open source version of Sun Java. It is in the Universe Repository.  You may want to look at [my sticky]("http://ubuntuforums.org/showthread.php?t=774956") on OpenJDK.

---

### Post by vgrisham on 2008-05-04
removed. problem solved

---

