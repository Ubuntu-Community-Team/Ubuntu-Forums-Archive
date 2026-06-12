---
title: "best way to do eclipse"
date: 2007-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by nephish on 2007-09-13
lo there, i am new and up on ubuntu feisty x86_64

i am wanting to install eclipse, i have multiverse enabled and see that eclipse is there, but i have read some from the forums about problems with it, and with the java dependencies. 
so i have a choice of ubuntu java, sun-java5, or sun-java6.. 

what is the best way to go here to get a version of eclipse going that will also allow me to install some plugins from the update-manager in eclipse. 

also plan to grab gutsy when it's stable next month, so would also prefer something that will not break that.

thanks for any tips from any veterans.

---

### Post by Cappy on 2007-09-13
I installed sun-java6 before .. it installed java 1.4 which was completely useless for me.

I would go for the 64-bit java 6 u2 package here at the very top:
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

Install it and then ```
sudo apt-get install eclipse
```

There is a netbeans + java6u2 package but they only give you a choice of 32-bit =(

---

### Post by nephish on 2007-09-13
ok, downloading the java package now, 

should i go with the ubuntu eclipse, or the one from the eclipse site? 
or does it make a difference ? they have a 64-bit build.

thanks

---

### Post by tszanon on 2007-09-13
> **nephish said:**
> ok, downloading the java package now, 

should i go with the ubuntu eclipse, or the one from the eclipse site? 
or does it make a difference ? they have a 64-bit build.

thanks
I got eclipse from the repositories and Java from Sun. They work fine for me.

---

### Post by sloggerkhan on 2007-09-13
You can get eclipse from the repos to work, but to keep up to date, I find it easier to just download the one from the eclipse website, put it in my home folder, and make a launcher for it. 
The key thing is to make sure that you have it configured for the right version of java.

---

### Post by ynef on 2007-09-17
The best way of doing this stuff, since it doesn't break Eclipse or anything else on your system (and will allow for updates via your package manager) is to:

[LIST=1]
[*]Using the package manager, install the Java and the Eclipse version you want to use.
[*]Run "sudo update-java-alternatives" to set which JRE that will be used by default when you type "java" and the other Java commands.
[*]To make Eclipse use your Java environment, edit the file /etc/eclipse/java_home and point it to your chosen JRE.
[/LIST]

Simple!

---

### Post by max.spicer on 2007-10-09
Also, try running eclipse from the command line first.  When I did this, I found it was outputting:

Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension

The combination of running the above commands as root, and fixing up /etc/eclipse/java_home to point to the correct jre has fixed my gutsy-installed eclipse.  Previously, update manager wasn't listing any of the eclipse update sites and Manage Configuration never actually popped up a window.  Now all is fine.

Thanks for the helpful posts!

Max

---

### Post by max.spicer on 2007-10-09
> **max.spicer said:**
> Also, try running eclipse from the command line first.  When I did this, I found it was outputting:

Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension

The combination of running the above commands as root, and fixing up /etc/eclipse/java_home to point to the correct jre has fixed my gutsy-installed eclipse.  Previously, update manager wasn't listing any of the eclipse update sites and Manage Configuration never actually popped up a window.  Now all is fine.

Thanks for the helpful posts!

Max

Actually, doesn't the fact that I had to create and chmod files as root highlight a bug in the gutsy Eclipse package?

Max

---

### Post by Everywhere_at_Once on 2007-10-13
is there a way to check if eclipse is using the right version of java?
   i have edited the java_home file, but i dont know if i did it right.

---

### Post by zingo on 2007-10-14
To check the java version used use the menu

"Help" -> "About eclipse SDK"
Then select "Configuration details" 
you will find it in the text

---

