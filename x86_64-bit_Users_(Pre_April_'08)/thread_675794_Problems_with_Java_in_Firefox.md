---
title: "Problems with Java in Firefox"
date: 2008-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by PC_load_letter on 2008-01-23
Hi all...I'm trying to run the Java applet Jmol from [http://jmol.sourceforge.net/](http://jmol.sourceforge.net/)   in firefox but in vain. The Jmol on-site Java check test results are as follows: 

> Your web browser seems to be mozilla/5 1.8.1.11 running on linux
      
Your web browser reports that Java is not enabled. The Jmol applet requires Java support from your web browser.
Please download Java from [www.java.com](www.java.com) and/or configure your browser to enable java applets. 

Operating System  	     * linux*
Web browser 	                *mozilla*
Browser version 	        *5*
navigator.userAgent 	      *Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.11) ecko/20061201 Firefox/2.0.0.11 (Ubuntu-feisty)*
has getElementById() 	    * true*
navigator.javaEnabled()      *false*

The output of java -version is: 
```
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) 64-Bit Server VM (build Blackdown-1.4.2-02, mixed mode)
```

I do have all the java options enabled in Firefox. Any ideas about what's wrong? 
Thanks.

---

### Post by Kilz on 2008-01-23
> **PC_load_letter said:**
> Hi all...I'm trying to run the Java applet Jmol from [http://jmol.sourceforge.net/](http://jmol.sourceforge.net/)   in firefox but in vain. The Jmol on-site Java check test results are as follows: 



The output of java -version is: 
```
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) 64-Bit Server VM (build Blackdown-1.4.2-02, mixed mode)
```

I do have all the java options enabled in Firefox. Any ideas about what's wrong? 
Thanks.

Blackdown is rather ancient, you might want to try icedtea.

---

### Post by PC_load_letter on 2008-01-23
I'm on a Windows machine right now, but I don't see Icedtea in the Feisty Universe, it's there for Hardy. So, do I have to compile it from the source? Could you post a link to the amd64 version of Icedtea?
Or could there be a less painful solution? 

Thanks.

---

### Post by Kilz on 2008-01-23
> **PC_load_letter said:**
> I'm on a Windows machine right now, but I don't see Icedtea in the Feisty Universe, it's there for Hardy. So, do I have to compile it from the source? Could you post a link to the amd64 version of Icedtea?
Or could there be a less painful solution? 

Thanks.

There is a less painful solution, you could install a [32bit firefox, Sun java, flash and multimedia plugins]("http://ubuntuforums.org/showthread.php?p=1174435") within a few minutes. Then run the 32bit browser. It will install beside the 64bit browser and will not replace it. This solution is probably a better solution, because icedtea is not 100% guaranteed for all sites. since it is not Sun java. Then in the future when Sun releases java 7 with the 64bit plugin you can uninstall the 32bit browser since its is installed from a deb file.

---

