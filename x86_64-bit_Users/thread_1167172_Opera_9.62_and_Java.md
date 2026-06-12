---
title: "Opera 9.62 and Java"
date: 2009-05-22
forum: x86 64-bit Users
---

### Post by adam-red on 2009-05-22
I'm using 64 bit Jaunty. I've had Java working in Firefox for ages but I like the look of Opera and I'd like to move over to it. Flash and YouTube etc work no problem but I still can't get Java right. I had OpenJDK and IcedTea on but when that didn't work I removed it in favour of the official sun version using this guide:
[http://ubuntuforums.org/showthread.php?t=1155925&highlight=opera+java](http://ubuntuforums.org/showthread.php?t=1155925&highlight=opera+java)

Output of Java -version is:
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)

and it still seems to be fine in FF since I've followed the guide but no joy in Opera. Any ideas?

Thanks in advance

---

### Post by cybrsaylr on 2009-05-22
I'm having the same problem with Opera with 64bit JJ.
Still can't get video to play right.
It's an Opera problem, not Jaunty.

Here's my thread:
[http://ubuntuforums.org/showthread.php?t=1155556](http://ubuntuforums.org/showthread.php?t=1155556)

Try SeaMonkey browser, it's as fast as Opera and plays all video fine and is in the repos.

---

### Post by khelben1979 on 2009-05-22
Have you looked and followed the instructions from [here]("http://www.opera.com/docs/linux/plugins/install/#java")? Feels a bit silly to ask, but I just felt I had to.

---

### Post by adam-red on 2009-05-22
Well I hadn't tried it but setting my java path to */usr/lib/jvm/java-6-sun-1.6.0.13/jre/lib/amd64/* still doesn't fix it :(...I'm sure this is an adam problem and not an Opera one

Thanks for the link by the way - I thought it'd just pick everything up from the Mozilla plugins. It's actually listed there.

---

### Post by Arup on 2009-05-22
Have you tested Java with the Java tester site at [http://www.javatester.org/](http://www.javatester.org/) In case it shows functional Java and the page doesn't work, that means its a page problem and not Opera or Jaunty. Mask as IE or FF trick for Opera might do the job. Java works fine installed from the repos in Jaunty here.

---

### Post by moledog on 2009-05-22
Java seems to be working OK here. KUBUNTU 9.04 64bit, Opera 9.64 64bit, and Sun's JDK. My java path in Opera is /opt/jdk1.6.0_13/jre/lib/amd64/.

---

### Post by cybrsaylr on 2009-05-23
> **khelben1979 said:**
> Have you looked and followed the instructions from [here]("http://www.opera.com/docs/linux/plugins/install/#java")? Feels a bit silly to ask, but I just felt I had to.
I click on that site and get the clock applet but Opera still runs screwy for me. Sometimes fast, then slow, than stalls for awhile.
Did the java tester and it show java installed and running the latest version.

It seems to be a wireless issue for me because when I go wired Opera takes off and is faster than Firefox. Then when I go back to wireless Opera is buggy again but FF runs normal. 
I switched to WICD manager and there is no change from above.

Started using SeaMonkey browser and it runs fine, as fast as Opera was before on Intrepid and even plays all video fine which Opera won't do yet.

---

### Post by adam-red on 2009-05-23
I can't see the pink box on javatester.org or the clock applet on the opera site while using opera, but I can in firefox. On the other hand, I installed the Facebook widget and that works since I changed my path. Am I right in thinking that uses it java and the problem is in fact related to the applet launcher plugin? Hmmm...again, works in firefox.
In opera : plugins I've got */usr/lib/mozilla/plugins/libjavaplugin.so* which I suppose it's picked up itself.

---

### Post by moledog on 2009-05-23
Maybe the java plugin is interfering. I seem to remember the same type of issue. I believe Opera doesn't use the java plugin, just the normal java. If I remember right, I had to move all my plugins around in the different directories that are searched and change the plugin search path in Opera so that the plugin wasn't used in Opera but was still used in Firefox. I am using Opera 9.64 and not 9.62, so maybe an issue there also.

---

### Post by Npl on 2009-05-23
Yeah, Opera uses Java directly, and its working in the 64 bit 9.64 Version for me (well most of the time anyway). Dont use the plugin (disable the path to it) maybe this is causing your problems.

---

### Post by adam-red on 2009-05-23
I didn't know how to disable the path to the Java plugin (only change the entire plugins path as opera : plugins is a static page) so I just moved libjavaplugin.so temporarily but still no joy. Thanks for the reply though

EDIT - I didn't realise 9.64 was available...I used a direct link to .62

---

### Post by cybrsaylr on 2009-05-23
Both Opera 9.62 and 9.64 still run buggy for me.

---

### Post by adam-red on 2009-05-23
Upgraded to 9.64 and Java worked straight away - didn't change anything

---

### Post by cybrsaylr on 2009-05-23
Just got video working on Opera 9.64 on 64bit Jaunty with the help from this thread:
[http://ubuntuforums.org/showthread.php?p=7333389#post7333389](http://ubuntuforums.org/showthread.php?p=7333389#post7333389)
Both plugin paths were checked in Opera which caused a conflict.
I unchecked one, the top opera/plugins, and video and audio now plays in Opera as it does in Firefox.

That solved the video problem, UTube plays video now but Opera still runs slow when loading pages.

---

### Post by cybrsaylr on 2009-05-24
FWIW:

After playing video on Opera, also noted at least for me, the video quality is not as good on Opera as it is in Firefox and SeaMonkey. In fact SeaMonkey appears to have better video quality than FF.

Opera video quality was better for me with 32bit Intrepid than 64bit Jaunty.

---

### Post by Arup on 2009-05-24
I watch youtube full screen with Opera using latest nvidia beta drivers and it works smoothly, actually in FF I see the occasional hesitation or blockiness, not in Opera. You probably have some conflict.

---

### Post by cybrsaylr on 2009-05-24
I know, Opera has been my fav browser the last 10 yrs.
It's frustrating I can't get it to run as well on 64bit JJ as it ran on 32bit Intrepid on my 15 month old AMD dual core Toshiba laptop.

SeaMonkey was a pleasant find though.

---

