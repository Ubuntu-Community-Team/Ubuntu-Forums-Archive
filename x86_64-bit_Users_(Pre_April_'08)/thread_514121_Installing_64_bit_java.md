---
title: "Installing 64 bit java"
date: 2007-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by bharathan100 on 2007-07-31
I am an absolute newbie to Ubuntu.I made the shift to Uubuntu 7.04 64 bit version (Running on Intel core2 Duo).I read the various threads related to making java 6 , flash et all work. I now have a working 32bit firefox with all plugins installed set up and working.


There are 3 questions I have:

1)Is it a good idea to get the 64 bit version of Java

2)When I go to this page ([http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)), it refuses to recognize that I have Java 6.Applications>Add/Remove programs shows Java6 is installed.
BTW I have java 5 web start installed but it doesn't show up on ADD/Remove

3)Can I get Active X to work on Linux?

I appreciate your help and time...Please reply soon

---

### Post by bbzbryce on 2007-07-31
> **bharathan100 said:**
> I am an absolute newbie to Ubuntu.I made the shift to Uubuntu 7.04 64 bit version (Running on Intel core2 Duo).I read the various threads related to making java 6 , flash et all work. I now have a working 32bit firefox with all plugins installed set up and working.


There are 3 questions I have:

1)Is it a good idea to get the 64 bit version of Java

2)When I go to this page ([http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)), it refuses to recognize that I have Java 6.Applications>Add/Remove programs shows Java6 is installed.
BTW I have java 5 web start installed but it doesn't show up on ADD/Remove

3)Can I get Active X to work on Linux?

I appreciate your help and time...Please reply soon

I installed Java 6 through automatix. ( [http://www.getautomatix.com/](http://www.getautomatix.com/) ). However like you that page does not work properly in Firefox, however it does work when I browse there using swiftfox which is 32bit (also through automatix) however I get this message as of now: 

"Oops! You don't have the recommended Java installed.
Your Java version is 1.6.0. Please click the button below to get the recommended Java for your computer. "

Well that's not too big of a deal. Regarding activex it appears if you install internet explorer through wine then this will work.

---

### Post by bharathan100 on 2007-07-31
I think you can get Active X on Mozilla...Not sure... I found a link for that when I clicked download plugin for some web page...

---

### Post by bharathan100 on 2007-07-31
The link was too complex for a noob like me to use... I would appreciate some pointers

---

### Post by Kilz on 2007-07-31
> **bbzbryce said:**
> 
Well that's not too big of a deal. Regarding activex it appears if you install internet explorer through wine then this will work.

Using IE under wine to browse with is not recommended, it is a huge security risk, as is active x.

---

### Post by bharathan100 on 2007-07-31
Thanks kilz. Thanks for your 32 bit firefox install script and the nspluginswrapper install script as well. I won't use activeX then. Are we going to get a stable 64 bit java once java7 releases? Can I hope for something good with gutsy?

---

### Post by bharathan100 on 2007-07-31
I get the same oops! message......

---

### Post by bharathan100 on 2007-07-31
Firefox hangs if I simultaneously open both the thirty two bit and the sixty four bit versions...

---

### Post by bharathan100 on 2007-07-31
Upgrading firefox removes all plugins from 32 bit firefox. Is there a workaround?

---

### Post by bbzbryce on 2007-07-31
> **bharathan100 said:**
> Upgrading firefox removes all plugins from 32 bit firefox. Is there a workaround?

Try to consolidate all you're questions before posting, it makes it easier to respond.

I've never tried an actual 32 bit firefox, but 32 bit swiftfox works pretty well, though it cannot be run at the same time as 64 bit firefox, and I've never had a problem with plug-ins.

---

### Post by bharathan100 on 2007-07-31
Yeah, I'll consolidate my questions, sorry. So I can upgrade w/o problems? I'll try now.

---

### Post by bharathan100 on 2007-07-31
Nope  the plugins(flash , java and mplayer) stopped working as soon as I upgraded. I ran kilz's script again to fix the problem.

---

### Post by kuja on 2007-07-31
> **bharathan100 said:**
> I am an absolute newbie to Ubuntu.I made the shift to Uubuntu 7.04 64 bit version (Running on Intel core2 Duo).I read the various threads related to making java 6 , flash et all work. I now have a working 32bit firefox with all plugins installed set up and working.


There are 3 questions I have:

1)Is it a good idea to get the 64 bit version of Java

2)When I go to this page ([http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)), it refuses to recognize that I have Java 6.Applications>Add/Remove programs shows Java6 is installed.
BTW I have java 5 web start installed but it doesn't show up on ADD/Remove

3)Can I get Active X to work on Linux?

I appreciate your help and time...Please reply soon

1) Sure - however, keep in mind thaty you **do  not** get a browser plugin with it. Something to keep in mind, if you want to install the 32-bit version as well, run "sudo apt-get install ia32-sun-java6-bin"

3) If there's one thing I've learned about Micro$oft windows, it's to avoid IE and it's gaping security hole plastered ActiveX like the plague.

---

### Post by bharathan100 on 2007-07-31
Thanks kuja. Can I run both 32 and 64 bit java simultaneously,if so how? Sorry if I'm repeating myself.

---

### Post by kuja on 2007-07-31
Installed simultaneously certainly, run simultaneously I don't know as I've never tried.

---

### Post by bharathan100 on 2007-07-31
Well could you clarify further?  Can I run Java64 (Where can I use the Java install in genral?) , stop that and then run Java 32 bit when I want to? I am pretty confused... Ihave used jdk for doing simple core java programs. I am a stranger to the rest except plugins working in browsers and java games, which I've seen.

---

### Post by kuja on 2007-07-31
It'll take a little more setup, but the short answer is yes.

---

### Post by bharathan100 on 2007-07-31
Thanks man. Can you tel me how to set it up or guide me to a link for it. I'm too much of a noob to figure it out by myself yet.

---

### Post by kuja on 2007-07-31
Here's how I would do it (it may be overkill, but I don't take chances (or lazy ways out :P)) (another note, make sure the paths below are correct for your install, it won't work if they aren't):

Open up your ~/.bash_profile (note the dot after the slash) with any editor and add this to it (oh, if the file doesn't exist, create it)

```
export OLDPATH = $PATH
export JAVA32 = /usr/lib/ia32-java6-sun/bin
export JAVA64 = /usr/lib/jvm/java-6-sun-1.6.0.00/bin
export JAVA32_HOME = /usr/lib/ia32-java6-sun/
export JAVA64_HOME = /usr/lib/java-6-sun-1.6.0.00/

#Now, you're going to have to pick a default here, 32 or 64, for sake of example
I'll use 64

export PATH = $JAVA64:/$OLDPATH
export JAVA_HOME = $JAVA64_HOME

```

Next we need to see if there are alternatives setup for update-alternatives, because update-alternatives is just so nice.

Run "sudo update-alternatives --config java" and see what the options are. If you're not seeing either or or both, you'll need to do this (again, make sure the paths are correct instead of blindly using the ones I have)

```

sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/ia32-java6-sun/bin/java 900
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-6-sun-1.6.0.00/bin/java 1000
sudo update-alternatives --config java

```

Next, we're going to create a script to switch on the fly, Lets call the file switchjava, put it whereever you'd like so long as it's in your $PATH (unless you want to type the full path of it every time, and that would just be a pain ... or you could put an alias to it in your ~/.bashrc, that'd work too. After creating the file change it's permissions to allow execution by running chmod +x switchjava)
You'll run the script by typing in "./switchjava 32" note the space before the 32. Same thing for 64.
```

#!/bin/sh
if [ $1 = 32 ]; then
sudo update-alternatives --set java $JAVA32
export PATH = $JAVA32:/$OLDPATH
export JAVA_HOME = $JAVA32_HOME
echo "Setting java to 32-bit"

elif [$1 = 64]; 
sudo update-alternatives --set java $JAVA64
export PATH= $JAVA64:/$OLDPATH
export JAVA_HOME = $JAVA64_HOME
else
echo "Bad argument, 32 and 64 are the only valid ones.";
fi;

```

Seeing as I just cooked this script up I'm not positive it works. I'm relying on you to give it a test run :)

---

### Post by bharathan100 on 2007-08-01
Thanks man, I am going to try this out and let you know ASAP...

---

