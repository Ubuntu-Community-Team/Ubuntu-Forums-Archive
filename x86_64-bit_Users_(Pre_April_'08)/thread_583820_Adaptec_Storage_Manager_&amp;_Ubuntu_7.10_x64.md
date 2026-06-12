---
title: "Adaptec Storage Manager &amp; Ubuntu 7.10 x64"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by LoneWolfJack on 2007-10-20
As I have been looking for some confirmation that ASM is working with Gutsy64 myself some weeks ago, here's the official thumbs up.

As Adaptec doesn't deliver a deb package, it needs to be converted from the rpm package using alien.

Once installed, there will be a "StorMan" folder in /usr that has a tar file in it containing the JRE kit. I suppose it is possible to point all scripts to the JRE kit you have installed (if you have one installed), but for ease of use, you can simply extract the contents of the tar file into /usr/StorMan.

I believe ASM is intended to be used as an applet, but if you are having problems running applets with Gutsy64, you may also run /usr/StorMan/StorMan.sh through the terminal which will open ASM as a program.

Tested with Ubuntu 7.10, Alien v8.68, ASM v5.01-00 and an Adaptec 2130SLP raid controller.

---

### Post by MMoudry on 2007-12-18
Hi,
I have tried to convert the package from RPM to DEB bu this is what happend. I am using Ubuntu 7.10 64 bit.

Here is the output :

mipam@origin:~$ sudo alien -v –scripts asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{SUMMARY} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{POSTIN} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{NAME} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{POSTUN} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{PREUN} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{RELEASE} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{PREFIXES} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{CHANGELOGTEXT} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{COPYRIGHT} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{DESCRIPTION} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{ARCH} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{VERSION} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qp –queryformat %{PREIN} asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qcp asm_linux_x64_v5_20_17414.rpm
rpm -qpi asm_linux_x64_v5_20_17414.rpm
LANG=C rpm -qpl asm_linux_x64_v5_20_17414.rpm
mkdir StorMan-5.20
chmod 755 StorMan-5.20
rpm2cpio asm_linux_x64_v5_20_17414.rpm | (cd StorMan-5.20; cpio –extract –make-directories –no-absolute-filenames –preserve-modification-time) 2>&1
Unpacking of ‘asm_linux_x64_v5_20_17414.rpm’ failed at /usr/share/perl5/Alien/Package/Rpm.pm line 153.
find StorMan-5.20 -type d -exec chmod 755 {} ;
rm -rf StorMan-5.20

MM

---

### Post by MMoudry on 2008-01-08
Nevermind, it works now.....

---

### Post by thedude88 on 2008-02-11
well i got this thing installed, but when i start it up it always says that it was unable to start on port 34571 and this keeps me from monitoring my debian server. I'm using ASM 5.20 java6 and ubuntu gutsy, if you guys have any advice i would really appreciate, and sorry if i'm hijacking this thread, but i figured i would give a shot.
Also when i boot into windows i'm able to completely manage my server, so i'm having no problems with the server...
Either way, thanks
James
**EDIT**
I just tried 5.01 and i had the same error, i'm thinking its java, but i've tried all kinds of different versions and ASM comes with its own jre in its directory... this is just driving me crazy...

---

### Post by MMoudry on 2008-02-11
Are you sure you are using the SUN's JDK and not one of the free JDK's?

Make sure that your java -version says it's a JDK from SUN.

MM

---

### Post by thedude88 on 2008-02-11
> **MMoudry said:**
> Are you sure you are using the SUN's JDK and not one of the free JDK's?

Make sure that your java -version says it's a JDK from SUN.

MM

ya, i've tried sun-java6.. and sun-java5, i also tried icedtea-java7 (or whatever it was named...) with no luck. Whats got me confused though is that ASM ships with its own JRE and keeps it in its folder so to test the other versions of java i had to go in and edit the bash file (StorMan.sh) to use a different java  interpreter.
Thanks for the help though, i appreciate it.
James

---

### Post by thedude88 on 2008-02-11
heres the output in the terminal when running java-6-sun-1.6.0.03
```

Unwritten string: February 12, 2008 4:25:14 AM GMT      INF    10576:A00C-S--L--        Local only      Adaptec Storage Manager started.
Unable to write to Event Log. IOException: java.io.FileNotFoundException: /usr/lib/jvm/RaidEvt.log (Permission denied)
Unwritten string: February 12, 2008 4:25:14 AM GMT      WRN    30535:A00C-S--L--        Local only      Adaptec Storage Manager failed to start at port number 34,571.

```

---

### Post by MMoudry on 2008-02-12
hmm looks like you have a permission problem, the java process is attempting to acess a file and it's refused access, try to run it as root :
sudo *yourcommand*

MM

---

### Post by thedude88 on 2008-02-12
I guess i forgot to mention this, but everytime i've tried running it from StormMan.sh i've used sudo and had no luck. This last time i just tried doing it form the terminal rather then the script, and i didn't try sudo because i figured it would just end up with the same result... Either way i'll still give it a shot when i get home, and i'll report back with my findings. Again thanks for the help
James

---

### Post by thedude88 on 2008-02-12
I juust gave running it as root a shot, and still no luck...

---

### Post by MMoudry on 2008-02-12
still same access denied message?

---

### Post by thedude88 on 2008-02-12
no, it gets rid of the permission denied error when it tries to right the logs, but it still gives me the same error saying unable to start on port 34571, and because of that i'm unable to connect to my debian server which has the raid controller in it.

---

### Post by MMoudry on 2008-02-12
hmm try to change the port on which the agent is started, try something low like 81.... maybe your server is configured to disallow port openings over a certain limit, or the port is already used..... thats all I can think of without mroe info, try to post an extract from your logs

MM

---

### Post by thedude88 on 2008-02-12
no dice.. i tried changing agent.startupPortNum to 81 and 1024 and both times it gave me the same just with the new port i had given it.
heres my RaidErrA.log
```

09 Feb 2008 10:29:43,922 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
09 Feb 2008 10:29:45,465 [main] ERROR SLPManager.instance:214 - Could not get SLPManager singleton
java.net.SocketException: bad argument for IP_MULTICAST_IF: address not bound to any interface
        at java.net.PlainDatagramSocketImpl.socketSetOption(Native Method)
        at java.net.PlainDatagramSocketImpl.setOption(PlainDatagramSocketImpl.java:299)
        at java.net.MulticastSocket.setInterface(MulticastSocket.java:420)
        at org.ch.ethz.iks.slp.impl.SLPManager.<init>(SLPManager.java:289)
        at org.ch.ethz.iks.slp.impl.SLPManager.instance(SLPManager.java:212)
        at org.ch.ethz.iks.slp.ServiceLocationManager.<clinit>(ServiceLocationManager.java:52)
        at com.ibm.sysmgt.raidmgr.agent.AutoDiscoveryEngine.<init>(AutoDiscoveryEngine.java:168)
        at com.ibm.sysmgt.raidmgr.agent.AutoDiscoveryEngine.instance(AutoDiscoveryEngine.java:836)
        at com.ibm.sysmgt.raidmgr.agent.ManagementAgent.<init>(ManagementAgent.java:311)
        at com.ibm.sysmgt.raidmgr.agent.ManagementAgent.main(ManagementAgent.java:981)
09 Feb 2008 10:30:32,519 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
09 Feb 2008 18:42:45,190 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
09 Feb 2008 19:05:41,255 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
09 Feb 2008 19:18:44,121 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
09 Feb 2008 19:31:58,874 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
09 Feb 2008 19:35:16,793 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
09 Feb 2008 19:38:26,535 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
09 Feb 2008 19:39:24,460 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
09 Feb 2008 19:40:51,013 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
11 Feb 2008 04:56:04,606 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
11 Feb 2008 04:56:40,020 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
10 Feb 2008 21:12:38,225 [main] WARN  MasterDataProc.<init>:135 - Discovered controllers: None
10 Feb 2008 21:12:40,425 [main] ERROR SLPManager.instance:214 - Could not get SLPManager singleton
java.net.SocketException: bad argument for IP_MULTICAST_IF: address not bound to any interface
        at java.net.PlainDatagramSocketImpl.socketSetOption(Native Method)
        at java.net.PlainDatagramSocketImpl.setOption(PlainDatagramSocketImpl.java:299)
        at java.net.MulticastSocket.setInterface(MulticastSocket.java:420)
        at org.ch.ethz.iks.slp.impl.SLPManager.<init>(SLPManager.java:289)
        at org.ch.ethz.iks.slp.impl.SLPManager.instance(SLPManager.java:212)
        at org.ch.ethz.iks.slp.ServiceLocationManager.<clinit>(ServiceLocationManager.java:52)
        at com.ibm.sysmgt.raidmgr.agent.AutoDiscoveryEngine.<init>(AutoDiscoveryEngine.java:168)
        at com.ibm.sysmgt.raidmgr.agent.AutoDiscoveryEngine.instance(AutoDiscoveryEngine.java:719)
        at com.ibm.sysmgt.raidmgr.agent.ManagementAgent.<init>(ManagementAgent.java:310)
        at com.ibm.sysmgt.raidmgr.agent.ManagementAgent.main(ManagementAgent.java:980)
10 Feb 2008 21:13:41,629 [main] WARN  MasterDataProc.<init>:135 - Discovered controllers: None
10 Feb 2008 21:14:16,699 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
10 Feb 2008 21:14:18,242 [main] ERROR SLPManager.instance:214 - Could not get SLPManager singleton
java.net.SocketException: bad argument for IP_MULTICAST_IF: address not bound to any interface
        at java.net.PlainDatagramSocketImpl.socketSetOption(Native Method)
        at java.net.PlainDatagramSocketImpl.setOption(PlainDatagramSocketImpl.java:299)
        at java.net.MulticastSocket.setInterface(MulticastSocket.java:420)
        at org.ch.ethz.iks.slp.impl.SLPManager.<init>(SLPManager.java:289)
        at org.ch.ethz.iks.slp.impl.SLPManager.instance(SLPManager.java:212)
        at org.ch.ethz.iks.slp.ServiceLocationManager.<clinit>(ServiceLocationManager.java:52)
        at com.ibm.sysmgt.raidmgr.agent.AutoDiscoveryEngine.<init>(AutoDiscoveryEngine.java:168)
        at com.ibm.sysmgt.raidmgr.agent.AutoDiscoveryEngine.instance(AutoDiscoveryEngine.java:836)
        at com.ibm.sysmgt.raidmgr.agent.ManagementAgent.<init>(ManagementAgent.java:311)
        at com.ibm.sysmgt.raidmgr.agent.ManagementAgent.main(ManagementAgent.java:981)
12 Feb 2008 18:42:03,410 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None
12 Feb 2008 18:42:28,129 [main] WARN  MasterDataProc.<init>:133 - Discovered controllers: None

```
I haven't dealt with java that much, but i'm going to look IP_MULTICAST_IF error
RaidErr.log
```

12 Feb 2008 17:43:53,934 [main] ERROR ManagedSystems.createRegistryAndExport:217 - GUI Alert Processor can not be exported.  Exception: 
java.rmi.ConnectException: Connection refused to host: 206.112.100.132; nested exception is: 
        java.net.ConnectException: Connection refused
        at sun.rmi.transport.tcp.TCPEndpoint.newSocket(TCPEndpoint.java:574)
        at sun.rmi.transport.tcp.TCPChannel.createConnection(TCPChannel.java:185)
        at sun.rmi.transport.tcp.TCPChannel.newConnection(TCPChannel.java:171)
        at sun.rmi.server.UnicastRef.newCall(UnicastRef.java:306)
        at sun.rmi.registry.RegistryImpl_Stub.rebind(Unknown Source)
        at com.ibm.sysmgt.raidmgr.mgtGUI.ManagedSystems.createRegistryAndExport(ManagedSystems.java:213)
        at com.ibm.sysmgt.raidmgr.mgtGUI.Launch.setupManagedSystems(Launch.java:4504)
        at com.ibm.sysmgt.raidmgr.mgtGUI.Launch.initLaunch(Launch.java:700)
        at com.ibm.sysmgt.raidmgr.mgtGUI.Launch.main(Launch.java:3385)
Caused by: java.net.ConnectException: Connection refused
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
        at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
        at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
        at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
        at java.net.Socket.connect(Socket.java:516)
        at java.net.Socket.connect(Socket.java:466)
        at java.net.Socket.<init>(Socket.java:366)
        at java.net.Socket.<init>(Socket.java:179)
        at sun.rmi.transport.proxy.RMIDirectSocketFactory.createSocket(RMIDirectSocketFactory.java:22)
        at sun.rmi.transport.proxy.RMIMasterSocketFactory.createSocket(RMIMasterSocketFactory.java:128)
        at sun.rmi.transport.tcp.TCPEndpoint.newSocket(TCPEndpoint.java:569)
        ... 8 more
12 Feb 2008 17:43:57,337 [RaidMan:Console:GUIEventListener] ERROR ManagedSystems.findManagedSystemForEvent:515 - Could not find Managed System for localhost
12 Feb 2008 17:43:57,337 [RaidMan:Console:GUIEventListener] ERROR GUIEventListener.run:123 - Event from unknown system: localhost
12 Feb 2008 17:43:57,338 [RaidMan:Console:GUIEventListener] ERROR ManagedSystems.findManagedSystemForEvent:515 - Could not find Managed System for localhost
12 Feb 2008 17:43:57,338 [RaidMan:Console:GUIEventListener] ERROR GUIEventListener.run:123 - Event from unknown system: localhost
12 Feb 2008 17:43:57,338 [RaidMan:Console:GUIEventListener] ERROR ManagedSystems.findManagedSystemForEvent:515 - Could not find Managed System for localhost
12 Feb 2008 17:43:57,339 [RaidMan:Console:GUIEventListener] ERROR GUIEventListener.run:123 - Event from unknown system: localhost
12 Feb 2008 17:43:57,339 [RaidMan:Console:GUIEventListener] ERROR ManagedSystems.findManagedSystemForEvent:515 - Could not find Managed System for localhost
12 Feb 2008 17:43:57,340 [RaidMan:Console:GUIEventListener] ERROR ManagedSystems.findManagedSystemForEvent:515 - Could not find Managed System for localhost
12 Feb 2008 17:43:57,340 [RaidMan:Console:GUIEventListener] ERROR ManagedSystems.findManagedSystemForEvent:515 - Could not find Managed System for localhost

```
I don't know what the ip address in this log is for... Also the raid card is in my server and not the computer im on right now, so thats why i'm getting the errors on localhost
Thanks again fror the help
James

---

### Post by scsikid on 2008-06-27
has anyone gotten to the bottom of this?

Personally I have an Adaptec 2410SA. Id like to run Storage Manager for it. I've tried following tihs link [http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1296399,00.html]("http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1296399,00.html") and everything is great until I try and run StorMan.sh I get the following error.

./StorMan.sh: 154: ./jre/bin/java: not found

I'm not sure if this is related to this thread but it was the closest thing I could fine. Any help would be appreciated.

---

### Post by scsikid on 2008-06-27
I downloaded Sun's JRE package and installed it in the Storman directory and did an apt-get on libxtst6 libxext6 libxi6.


I now get the display to appear. But can't log in as root or a regular user. Shell works fine with the passwords I'm providing.

---

