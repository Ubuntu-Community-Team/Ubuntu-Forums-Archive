---
title: "Azureus under AMD-64"
date: 2006-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bitch-Face Jones on 2006-01-31
Has anyone been able to get Azureus running under Ubuntu with AMD-64?  I've installed Sun's JRE (1.5_06) and Azureus starts fine, but I'm unable to download anything.  In fact, I get this spammed on the terminal window I've invoked Azureus from as long as I'm trying to download anything:
```

DEBUG::Tue Jan 31 19:37:47 EST 2006::org.gudy.azureus2.core3.peer.impl.transport.PEPeerTransportProtocol$1::exceptionThrown(java.lang.Throwable)::-1:
    NetworkConnectionImpl::notifyOfException(java.lang.Throwable)::-1,MultiPeerDownloader::doProcessing()::-1,ReadController::doHighPriorityRead()::-1,ReadController::readProcessorLoop()::-1,ReadController::access$100(com.aelitis.azureus.core.networkmanager.impl.ReadController)::-1,ReadController$2::runSupport()::-1,AEThread::run()::-1,::GC_start_routine::-1,::__clone::-1
java.nio.BufferOverflowException
   at java.nio.Buffer.checkForOverflow(int) (/usr/lib/libgcj.so.6.0.0)
   at java.nio.ByteBuffer.put(byte[], int, int) (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.nio.SocketChannelImpl.read(java.nio.ByteBuffer) (/usr/lib/libgcj.so.6.0.0)
   at com.aelitis.azureus.core.networkmanager.impl.TCPTransportHelper.read(java.nio.ByteBuffer[], int, int) (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.impl.TCPTransportImpl.read(java.nio.ByteBuffer[], int, int) (Unknown Source)
   at com.aelitis.azureus.core.peermanager.messaging.bittorrent.BTMessageDecoder.performStreamDecode(com.aelitis.azureus.core.networkmanager.TCPTransport, int) (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.IncomingMessageQueue.receiveFromTransport(int) (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.impl.MultiPeerDownloader.doProcessing() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.impl.ReadController.doHighPriorityRead() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.impl.ReadController.readProcessorLoop() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.impl.ReadController.access$100(com.aelitis.azureus.core.networkmanager.impl.ReadController) (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.impl.ReadController$2.runSupport() (Unknown Source)
   at org.gudy.azureus2.core3.util.AEThread.run() (Unknown Source)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/libc-2.3.5.so)
DEBUG::Tue Jan 31 19:37:51 EST 2006
  java.lang.NullPointerException
   at org.gudy.azureus2.core3.tracker.client.impl.bt.TRTrackerBTAnnouncerImpl.setRefreshDelayOverrides(int) (Unknown Source)
   at org.gudy.azureus2.core3.peer.impl.control.PEPeerControlImpl.updateTrackerAnnounceInterval() (Unknown Source)
   at org.gudy.azureus2.core3.peer.impl.control.PEPeerControlImpl.mainLoop() (Unknown Source)
   at org.gudy.azureus2.core3.peer.impl.control.PEPeerControlImpl.access$200(org.gudy.azureus2.core3.peer.impl.control.PEPeerControlImpl) (Unknown Source)
   at org.gudy.azureus2.core3.peer.impl.control.PEPeerControlImpl$4.runSupport() (Unknown Source)
   at org.gudy.azureus2.core3.util.AEThread.run() (Unknown Source)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/libc-2.3.5.so)

```
If anyone knows what the problem is I'd love to hear from you...

---

### Post by CyberAngel on 2006-02-01
I Have download Azureus for AMD64 from this location:
```
http://prdownloads.sourceforge.net/azureus/Azureus_2.3.0.6_linux-x86_64.tar.bz2?download
```
and it is working fine.

Just run the file azureus from the folder you have extracted it.

---

### Post by Bitch-Face Jones on 2006-02-01
[QUOTE=CyberAngel]I Have download Azureus for AMD64 from this location: ```
http://prdownloads.sourceforge.net/azureus/Azureus_2.3.0.6_linux-x86_64.tar.bz2?download
``` and it is working fine. Just run the file azureus from the folder you have extracted it.[/QUOTE] Yeah, that's basically what I'm doing. Out of curiosity, what JRE are you running? Are you running the blackdown (or whatever it's called) JRE, or Sun's?

---

### Post by awi on 2006-02-02
[QUOTE=Bitch-Face Jones]    NetworkConnectionImpl::notifyOfException(java.lang.Throwable)::-1,MultiPeerDownloader::doProcessing()::-1,ReadController::doHighPriorityRead()::-1,ReadController::readProcessorLoop()::-1,ReadController::access$100(com.aelitis.azureus.core.networkmanager.impl.ReadController)::-1,ReadController$2::runSupport()::-1,AEThread::run()::-1,::GC_start_routine::-1,::__clone::-1
java.nio.BufferOverflowException
   at java.nio.Buffer.checkForOverflow(int) (/usr/lib/libgcj.so.6.0.0)
   at java.nio.ByteBuffer.put(byte[], int, int) (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.nio.SocketChannelImpl.read(java.nio.ByteBuffer) (/usr/lib/libgcj.so.6.0.0)
   at [/QUOTE]
Those particular lines, tell you at is running the standar installation from (k)ubuntu, the alternative JVM from GNU. GNU's java implementation are not complete, and maybe that is why your are getting this error.
I know that SUN's JVM is not as free as GNU, but I'm wondering, if the people who include software like Eclipse or Azureus or almost any graphic java application, have done real heavy testing, to say that they "run" with the alternative implementation, I have no luck with those, and end up installing SUN's always. :(
Try setting an environment variable JAVA_HOME pointing to your JRE or JDK installation, and also putting in front of the path, like this:

```
$ export JAVA_HOME=/usr/local/jdk
$ export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
$ [ cd to your azureus directory]
$ [ run from the terminal the azureus]
```

For some reason, that I still have not looked at, when you launch from the menues, it does not get the /etc/profile or /etc/basrh or any profile or rc that is on your home, and it gets different environment that when you run it from the terminal.

---

### Post by MF_III on 2006-02-02
I have succesfully run and download for Azureus with Kubuntu 5.10 Breezy (AMD64). I have j2re 1.4 installed :)

---

### Post by CyberAngel on 2006-02-02
[QUOTE=Bitch-Face Jones]Yeah, that's basically what I'm doing. Out of curiosity, what JRE are you running? Are you running the blackdown (or whatever it's called) JRE, or Sun's?[/QUOTE]

Yeap..

That`s what I have installed.

j2re1.4

---

### Post by beefsprocket on 2006-02-02
j2re1.4 here as well. With 1.5 I get gzip header corrupt or something like that -- the same error happens in 32bit version IIRC. Curiously, Azureus was crashing every minute or two the other day, for no apparent reason. I didn't change anything, reboot, or do anything drastic, but it has been rock solid for the past 2 days straight now. 

Which version is configured when you do: update-alternatives --config java? Yours should look like this:

There are 3 alternatives which provide `java'.

Selection    Alternative
-----------------------------------------------
      1        /usr/lib/jvm/java-gcj/bin/java
      2        /usr/bin/gij-wrapper-4.0
*+  3        /usr/lib/j2se/1.4/bin/java

---

### Post by Bitch-Face Jones on 2006-02-02
[QUOTE=awi]Those particular lines, tell you at is running the standar installation from (k)ubuntu, the alternative JVM from GNU. GNU's java implementation are not complete, and maybe that is why your are getting this error.[/QUOTE]
Yep, that was it.  I didn't know that another JVM was installed by default, and apperently that JVM was in my path even after installing Sun's with java-package.
> 
Try setting an environment variable JAVA_HOME pointing to your JRE or JDK installation, and also putting in front of the path, like this:

```
$ export JAVA_HOME=/usr/local/jdk
$ export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
$ [ cd to your azureus directory]
$ [ run from the terminal the azureus]
```

For some reason, that I still have not looked at, when you launch from the menues, it does not get the /etc/profile or /etc/basrh or any profile or rc that is on your home, and it gets different environment that when you run it from the terminal.

Yeah, AFAIK the only workaround for that is to just make a wrapper script that exports those environment variables, and launch Azureus/Eclipse/whatever using that.

Thanks for your help!

---

