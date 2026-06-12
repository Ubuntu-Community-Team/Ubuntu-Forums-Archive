---
title: "Help ! how to install Java runtime environment 1.5"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by D_frag on 2006-09-22
The reason i am trying this is because alot of apps using java are not working for me , i tried azareus and i can't find it ! i go to Applications-->>Internet-->> and it'snot there , so i thought maybe i should get java runtime 1.5 i downloaded the .bin file but i would like help howto install it ?

---

### Post by acefreely on 2006-09-22
haven't done it in a while but if I remember right its something like this...cd to the download directory that contains the BIN file.

replace java.BIN with the file name

```
sudo -i
chmod 555 java.BIN
./java.BIN
```

Follow on screen instructions...

---

### Post by D_frag on 2006-09-22
i did that but it didnt work 
what i did later was >./blablabla.bin
and i got the nest line fine
does that mean it's installed /???

P.S I also installed azureus from add/remove then i find it at applications-->>internet and i click on it nothing happens it doesnt open does anyone know anything about that ?

---

### Post by acefreely on 2006-09-22
try 

```
which java
```

and if it displays something like
```

/usr/bin/java
```

then it worked.  

I am installing now, so I'll post the details in a couple of minutes...

---

### Post by jamesford on 2006-09-22
well i can tell u how i got azureus working with sun java if thats of any help
1: install sun java: sudo apt-get install sun-java5-jre
2: select sun java as the default java environment: sudo update-alternatives --config java
3: download the axureus amd64 tarball from azureus website ([http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux-x86_64.tar.bz2?download](http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.0_linux-x86_64.tar.bz2?download))
4: extract the azureus tar.bz to a folder (like /home/username/apps/azureus)
5: find the azureus shellscript inside /home/username/apps/azureus (the file is caleld just 'azureus') - open it in a text editor
6: in that file set the parameter JAVA_PROGRAM_DIR="/path/to/java/dir/"	
the path here must correspond with where your sun java is installed, u will see the path doing:sudo update-alternatives --config java  - pick the line with the word 'sun 1.5' or similar in it
in my case it looks like:JAVA_PROGRAM_DIR="/usr/lib/jvm/java-1.5.0-sun/jre/bin/"	
7: manually create a a launcher in your apps meny, panel or desktop pointing to the azureus shellscript (like  /home/username/apps/azureus/azureus) - pick and icon for it

---

### Post by William Pickett on 2007-03-25
Hello, I am attempting to learn programmer speak, and not there yet. Would someone use simple words, phrases and concepts for me and explain how I need to do/what I need to do next after the following, to use Azureus:-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-gcj/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
a21william@a21william-desktop:~$ azureus
bash: azureus: command not found
a21william@a21william-desktop:~$ sudo azureus
sudo: azureus: command not found
a21william@a21william-desktop:~$ 

I see a need for simpler explanations for non geek types. "Linux for the rest of us". AMD64 Athlon generic x86_64 Edgy. Technospeak for the non tech is not workable, and prevents the widespread use of Linux. Answers email me, I set up auto reply from the forums so will get it.
Thanks, William Pickett Albuquerque (or reply directly w/subj x86_64bit Ubuntu to [email]wkpickett0154@comcast.net[/email])

---

