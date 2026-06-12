---
title: "Java working in firefox32 with kils script"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by brew1brew on 2007-04-20
I installed Firefox32 with Kils script and was having the same problems as every one else. It would crash every time I went to a java site. I have had no luck with blackdown java before and have always manually installed Sun's java. So I went to [www.java.com](www.java.com) and downloaded "Linux (self-extracting file)" it's the 32 bit version. I followed the instructions on the sun site. I will list the steps here.

I found that Kils script installs firefox32 and java in /usr/lib32 he puts java in /usr/lib32/java32. So here is what I did.

1. download jre-6u1-linux-i586.bin from [http://www.java.com](http://www.java.com) click on download
2. went to supper user mode
```
$ sudo su
```
3. copy it to /usr/lib32/java32
```
#cd /usr/lib32/java32
#cp /home/kat/Download/jre-6u1-linux-i586.bin jre-6u1-linux-i586.bin

```
4. changed permissions on the file to make it exacutable
```
#chmod a+x jre-6u1-linux-i586.bin
```
5. execute the file
```
#./jre-6u1-linux-i586.bin
```
6. that installed it in /usr/lib32/java32/jre1.6.0_01

ok now to setup the plugin, I found that Kils script installed the java plugin in /usr/lib32/firefox32/plugins/

I removed the plugin 

```
#cd /usr/lib32/firefox32/plugins/ 
#rm libjavaplugin_oji.so
```

I added the simlink to the sun java plugin with

```
# ln -s /usr/lib32/java32/jre1.6.0_01/plugin/i386/ns7/libjavaplugin_oji.so

```
while still being in /usr/lib32/firefox32/plugins/

restart firefox and Sun Java is now working fine.

I hope this all makes since.

Les

PS - Kils Thanks for a great little auto tool!!! 

PSS - Oh, I was on edgy and upgraded through update-manager to Feisty. Kils script was ran on Edgy and my mod to fix Java was after Feisty upgrade, but that should not make a difference.

---

### Post by st33med on 2007-04-20
Whoops, never mind! you installed something different than my thing

---

### Post by Kilz on 2007-04-21
> **brew1brew said:**
> I installed Firefox32 with Kils script and was having the same problems as every one else. It would crash every time I went to a java site. I have had no luck with blackdown java before and have always manually installed Sun's java. So I went to [www.java.com](www.java.com) and downloaded "Linux (self-extracting file)" it's the 32 bit version. I followed the instructions on the sun site. I will list the steps here.

I found that Kils script installs firefox32 and java in /usr/lib32 he puts java in /usr/lib32/java32. So here is what I did.

1. download jre-6u1-linux-i586.bin from [http://www.java.com](http://www.java.com) click on download
2. went to supper user mode
```
$ sudo su
```
3. copy it to /usr/lib32/java32
```
#cd /usr/lib32/java32
#cp /home/kat/Download/jre-6u1-linux-i586.bin jre-6u1-linux-i586.bin

```
4. changed permissions on the file to make it exacutable
```
#chmod a+x jre-6u1-linux-i586.bin
```
5. execute the file
```
#./jre-6u1-linux-i586.bin
```
6. that installed it in /usr/lib32/java32/jre1.6.0_01

ok now to setup the plugin, I found that Kils script installed the java plugin in /usr/lib32/firefox32/plugins/

I removed the plugin 

```
#cd /usr/lib32/firefox32/plugins/ 
#rm libjavaplugin_oji.so
```

I added the simlink to the sun java plugin with

```
# ln -s /usr/lib32/java32/jre1.6.0_01/plugin/i386/ns7/libjavaplugin_oji.so

```
while still being in /usr/lib32/firefox32/plugins/

restart firefox and Sun Java is now working fine.

I hope this all makes since.

Les

PS - Kils Thanks for a great little auto tool!!! 

PSS - Oh, I was on edgy and upgraded through update-manager to Feisty. Kils script was ran on Edgy and my mod to fix Java was after Feisty upgrade, but that should not make a difference.

The new Festy script does not install the 1.4 or blackdown java. But if anyone upgrades from Edgy they will have the problem you describe. They could just install the new Feisty script if they want to to fix the problem.

---

### Post by brew1brew on 2007-04-21
> **Kilz said:**
> The new Festy script does not install the 1.4 or blackdown java. But if anyone upgrades from Edgy they will have the problem you describe. They could just install the new Feisty script if they want to to fix the problem.

cool, what Java does it install? I only ask cause I've had better luck with Sun Java.

Les

---

### Post by Kilz on 2007-04-21
> **brew1brew said:**
> cool, what Java does it install? I only ask cause I've had better luck with Sun Java.

Les

sun 1.5 also called sun 5, I dont like 6 because it can be buggy.

---

