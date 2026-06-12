---
title: "How do I install the mozilla java plugin with nswrapper?"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Auax on 2007-10-26
I have flash working fine, but I don't know how to get java to run on 64-bit firefox.

---

### Post by aphirst on 2007-10-26
NSPluginwrapper doesnt work with java. If you're on Gutsy; get the icedtea java plugin. its in the repos.

I had todo some symbolic linking to make the plugin get recognised (linking from a gcjwebplugin.so into the firefox plugins folder; but it works :D .

---

### Post by Auax on 2007-10-26
That works too, thanks. :D

---

### Post by Auax on 2007-10-26
Ok, I installed the icedtea plugin, and now applets don't show the "Download Plugin" thing, but they just stay blank white. Do I need to do that symbolic link thing? And how do I do it?

---

### Post by whistl on 2007-10-26
So far, my experience has been that the icedtea java plugin is worthless.  Not one java app I've tried works with 64-firefox+icedtea.  They all appear to start up, and just hang forever.

---

### Post by Ryan450 on 2007-10-26
> **whistl said:**
> So far, my experience has been that the icedtea java plugin is worthless.  Not one java app I've tried works with 64-firefox+icedtea.  They all appear to start up, and just hang forever.

I'm having the same problem. I downloaded and installed from the repository but it just doesnt work. If somebody comes up with a solution to this please post/sticky it.

---

### Post by loupy on 2007-10-26
The one from the official repos did not work for me either, but this repo did:

deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

Hope that helps.

---

### Post by whistl on 2007-10-26
I tried those too.  No joy.

If you have it working, please post the output from
```

ls -l /etc/alternatives/*java*

```

so we can see how your java alternatives are configured.

---

### Post by loupy on 2007-10-26
This is the output:

lrwxrwxrwx 1 root root 57 2007-10-22 08:33 /etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root 57 2007-10-22 08:33 /etc/alternatives/iceape-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root 57 2007-10-22 08:33 /etc/alternatives/iceweasel-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root 40 2007-10-20 12:33 /etc/alternatives/java -> /usr/lib/jvm/java-7-icedtea/jre/bin/java
lrwxrwxrwx 1 root root 57 2007-10-22 08:33 /etc/alternatives/midbrowser-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root 57 2007-10-22 08:33 /etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root 57 2007-10-22 08:33 /etc/alternatives/xulrunner-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so

---

### Post by Auax on 2007-10-27
> **whistl said:**
> I tried those too.  No joy.

If you have it working, please post the output from
```

ls -l /etc/alternatives/*java*

```

so we can see how your java alternatives are configured.

All of the sudden my flash stopped working and is doing the same as Java now too.

```
administrator@hades:~$ ls -l /etc/alternatives/*java*
lrwxrwxrwx 1 root root 57 2007-10-26 05:11 /etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root 57 2007-10-26 05:11 /etc/alternatives/iceape-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root 57 2007-10-26 05:11 /etc/alternatives/iceweasel-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root 40 2007-10-26 05:09 /etc/alternatives/java -> /usr/lib/jvm/java-7-icedtea/jre/bin/java
lrwxrwxrwx 1 root root 57 2007-10-26 05:11 /etc/alternatives/midbrowser-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root 57 2007-10-26 05:11 /etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root 57 2007-10-26 05:11 /etc/alternatives/xulrunner-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so

```

---

### Post by Angelbeast on 2007-10-27
> **aphirst said:**
> NSPluginwrapper doesnt work with java. If you're on Gutsy; get the icedtea java plugin. its in the repos.

I had todo some symbolic linking to make the plugin get recognised (linking from a gcjwebplugin.so into the firefox plugins folder; but it works :D .

How do you do the symbolic linking?

---

### Post by steveneddy on 2007-10-27
> **loupy said:**
> The one from the official repos did not work for me either, but this repo did:

deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

Hope that helps.

This did it for me - I deleted the listing that was in the repos and added the alternate repo and tried it again. 

Perfecto! Works.

Cool - thanks.

:popcorn:

---

### Post by veeravalli on 2007-10-27
> **Angelbeast said:**
> How do you do the symbolic linking?

I would also like to know, please.

---

### Post by aphirst on 2007-10-29
It took a bit of pratting; but I used the find files / folders option on the upper deskbar to find the firefox plugins folder (sadly I'm on a Windoze PC atm, but I'll update the post later with specific locations); then found the file "gcjwebplugin.so". Then I ran

```
sudo ln -s /path/to/gcjwebplugin.so /path/to/firefox/plugin/folder/gcjwebplugin.so
```

I do believe I hac to manually install gcj related packages (like gcjwebplugin4.2 and other such like) from synaptic beforehand; but like I say, I shall update this post later on with specific locations.

Hope this helps...

---

### Post by deruberhanyok on 2007-10-29
> **loupy said:**
> The one from the official repos did not work for me either, but this repo did:

deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

Hope that helps.

This also worked for me. Sun's java verify page wouldn't show using the files in the main repository. Any idea if these will be added to the main one soon?

---

### Post by Auax on 2007-10-29
I've tried everything suggested here, but I'm still having the same problem.

Now all Flash and Java applets don't load.

---

### Post by Robocoastie on 2007-10-29
i get dependency errors.

---

