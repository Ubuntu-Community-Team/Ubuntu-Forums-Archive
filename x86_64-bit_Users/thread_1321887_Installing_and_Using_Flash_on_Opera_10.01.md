---
title: "Installing and Using Flash on Opera 10.01"
date: 2009-11-10
forum: x86 64-bit Users
---

### Post by Pernig on 2009-11-10
I installed Ubuntu 9.10 64 bit edition this weekend, and am very impressed :cool:. From dabbling around in 64-bit Linux (Gutsy and Mandriva 2007.1) a couple of years back I vaguely remembered having problems getting Flash player to work. However, I didn't have too much trouble at all getting it to work this time, so I will share my experiences by writing a step-by-step guide on how i did it:

1. Download Opera 10.01 from the Opera website by selecting the .deb package for 9.10 Karmic Koala. 

2. Before installing this you may need to go onto System > Administration > Software Sources and tick all of the boxes on the first tab.

[ATTACH]135616[/ATTACH]

3. Execute the installation package. You may need to download some dependencies but this will be done for you by Synaptic.

4. Once this is done, go to System > Administration > Synaptic Package Manager and install 'flashplugin-installer'. This is a non-free package so for it to be available you may have to enable extra software sources. If you cannot see it, double check you have done step 2.

[ATTACH]135617[/ATTACH]

5. Start up Opera and go to Tools > Preferences. Click the advanced tab. go to Content and click the 'Plug-in Options' button. You will be presented with this screen:

[ATTACH]135612[/ATTACH]

6. Untick the /usr/lib/mozilla/plugins. Make sure the /usr/lib/flashplugin-installer path is ticked. Also if you are running any other plugins make sure the /usr/lib/opera/plugins path is ticked too.

Now Opera is all set to use Flash. If you are having trouble, give it a go and let me know if it works for you!

---

### Post by Arup on 2009-11-10
Actually its quite simple, as long as you have the untarred libflashplayer.so in /usr/lib/mozila/plugins, Opera picks it up nicely with no issues. I now use Open Java instead of Sun and to make that work in Opera you have to specify the path which usually is /usr/lib/jvm/java-6-openjdk/jre/lib/amd64

Java tester works on this and most Java enabled sites do as well with few exceptions.

---

### Post by 9170 on 2009-11-12
Hi!

I have sometime trouble with the Flash on homepages. Opera become slow and the Flash doesn't work well at all. This happened on both computers so that it not depends on the graphic card. 

An example for slow a homepage [http://www.max-biaggi.com/index_en.php]("http://www.max-biaggi.com/index_en.php") and for a page that crash [http://svenskaspel.se/p4.aspx?pageid=3]("http://svenskaspel.se/p4.aspx?pageid=3")

I use Opera 10.01.

---

### Post by sarsbretta on 2009-11-12
> **9170 said:**
> I have sometime trouble with the Flash on homepages. Opera become slow and the Flash doesn't work well at all. This happened on both computers so that it not depends on the graphic card.

I would check:
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)
then
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

to make sure its working
I had/have problems with Firefox after the upgrade from 9.04 to 9.1. I noticed it when tried to watch something on youtube and the video part just stayed black. Then I tried Opera with the same URL but instead of black, it was white.

---

### Post by HappyFeet on 2009-11-12
> **9170 said:**
> Hi!

I have sometime trouble with the Flash on homepages. Opera become slow and the Flash doesn't work well at all. This happened on both computers so that it not depends on the graphic card. 

An example for slow a homepage [http://www.max-biaggi.com/index_en.php]("http://www.max-biaggi.com/index_en.php") and for a page that crash [http://svenskaspel.se/p4.aspx?pageid=3]("http://svenskaspel.se/p4.aspx?pageid=3")

I use Opera 10.01.
Are you using the 64bit flash file?

---

### Post by 9170 on 2009-11-14
Hi Sarsbretta

Testing those sides, [http://www.adobe.com/shockwave/welcome/]("http://www.adobe.com/shockwave/welcome/") it shows that the flash is installed but not the shockwave. 

[http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml") tells me that "Something is wrong. Java is not working"

It seams that I have some basic problems.

Using 9.04 I never had this problems.

---

### Post by 9170 on 2009-11-15
Hi!

I have added Sun Java and Java works now in Opera and all seams to be okay. 

Thank you Guys!

---

