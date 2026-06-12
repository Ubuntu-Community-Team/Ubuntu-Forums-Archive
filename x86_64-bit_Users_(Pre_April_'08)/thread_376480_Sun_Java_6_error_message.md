---
title: "Sun Java 6 error message"
date: 2007-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by geakMonkey on 2007-03-04
I am troubleshooting my Sun Java 6 with Firefox. This is output from [http://serios.net/content/applets/viewinfoawt.php]("http://serios.net/content/applets/viewinfoawt.php")
What is this error message mean? Error reading registry file: 


Java Plug-in 1.6.0
Using JRE version 1.6.0 Java HotSpot(TM) Client VM
User home directory = /home/myself
network: Loading user-defined proxy configuration ...
network: Done.
network: Loading proxy configuration from Netscape Navigator ...
network: Error reading registry file: /home/myself/.mozilla/appreg
network: Done.
network: Loading browser proxy configuration ...
network: Done.
network: Proxy Configuration: Browser Proxy Configuration


----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

basic: New window ID: 2e97a3b
basic: Value of xembed: 1
basic: setWindow: call before applet exists:2e97a3b
basic: Referencing classloader: sun.plugin.ClassLoaderInfo@1ccb029, refcount=1
basic: Added progress listener: sun.plugin.util.GrayBoxPainter@1d520c4
basic: Loading applet ...
basic: Initializing applet ...
basic: Starting applet ...
basic: completed perf rollup
network: Cache entry not found [url: http://serios.net/files/applets/ViewInfoAWT.jar, version: null]
network: Connecting http://serios.net/files/applets/ViewInfoAWT.jar with proxy=DIRECT
network: Connecting http://serios.net/files/applets/ViewInfoAWT.jar with cookie "__utma=11402934.1851941234.1172380851.1172383113.1173068794.3; __utmz=11402934.1173068794.3.2.utmccn=(referral)|utmcsr=martinfowler.com|utmcct=/bliki/DebianJava.html|utmcmd=referral; __utmb=11402934; __utmc=11402934"
network: Downloading resource: http://serios.net/files/applets/ViewInfoAWT.jar
	Content-Length: 21,001
	Content-Encoding: null
network: Wrote URL http://serios.net/files/applets/ViewInfoAWT.jar to File /home/myself/.java/deployment/cache/6.0/47/269b1ef-7c8c5e78-temp
network: No certificate info for unsigned JAR file: http://serios.net/files/applets/ViewInfoAWT.jar
net.serios.awt.TextComponentContextMenu: Unable to use system clipboard. Using local clipboard.
network: Cache entry found [url: http://serios.net/files/applets/ViewInfoAWT.jar, version: null]
network: No certificate info for unsigned JAR file: http://serios.net/files/applets/ViewInfoAWT.jar
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
basic: New window ID: 2e9e364
basic: Value of xembed: 1
basic: setWindow: call before applet exists:2e9e364
basic: Referencing classloader: sun.plugin.ClassLoaderInfo@110003, refcount=1
basic: Added progress listener: sun.plugin.util.GrayBoxPainter@12940b3
basic: Loading applet ...
basic: Initializing applet ...
basic: Starting applet ...
basic: completed perf rollup
network: Cache entry not found [url: http://serios.net/files/applets/ViewProperties.jar, version: null]
network: Connecting http://serios.net/files/applets/ViewProperties.jar with proxy=DIRECT
network: Connecting http://serios.net/files/applets/ViewProperties.jar with cookie "__utma=11402934.1851941234.1172380851.1172383113.1173068794.3; __utmz=11402934.1173068794.3.2.utmccn=(referral)|utmcsr=martinfowler.com|utmcct=/bliki/DebianJava.html|utmcmd=referral; __utmb=11402934; __utmc=11402934"
network: Downloading resource: http://serios.net/files/applets/ViewProperties.jar
	Content-Length: 4,028
	Content-Encoding: null
network: Wrote URL http://serios.net/files/applets/ViewProperties.jar to File /home/myself/.java/deployment/cache/6.0/46/310319ee-5526ed07-temp
network: No certificate info for unsigned JAR file: http://serios.net/files/applets/ViewProperties.jar
java.security.AccessControlException: access denied (java.util.PropertyPermission java.home read)
java.security.AccessControlException: access denied (java.util.PropertyPermission java.class.path read)
java.security.AccessControlException: access denied (java.util.PropertyPermission java.library.path read)
java.security.AccessControlException: access denied (java.util.PropertyPermission java.io.tmpdir read)
java.security.AccessControlException: access denied (java.util.PropertyPermission java.compiler read)
java.security.AccessControlException: access denied (java.util.PropertyPermission java.ext.dirs read)
java.security.AccessControlException: access denied (java.util.PropertyPermission user.name read)
java.security.AccessControlException: access denied (java.util.PropertyPermission user.home read)
java.security.AccessControlException: access denied (java.util.PropertyPermission user.dir read)
basic: Stopping applet ...
basic: New window ID: 0
basic: Removed progress listener: sun.plugin.util.GrayBoxPainter@12940b3
basic: Finding information ...
basic: Releasing classloader: sun.plugin.ClassLoaderInfo@110003, refcount=0
basic: Caching classloader: sun.plugin.ClassLoaderInfo@110003
basic: Current classloader cache size: 1
basic: Done ...
basic: Joining applet thread ...
basic: Destroying applet ...
basic: Disposing applet ...
basic: Quiting applet ...
basic: Joined applet thread ...
basic: New window ID: 2e9f085
basic: Value of xembed: 1
basic: setWindow: call before applet exists:2e9f085
basic: Referencing classloader: sun.plugin.ClassLoaderInfo@1ccb029, refcount=2
basic: Added progress listener: sun.plugin.util.GrayBoxPainter@1af33d6
basic: Loading applet ...
basic: Initializing applet ...
basic: Starting applet ...
basic: completed perf rollup
net.serios.awt.TextComponentContextMenu: Unable to use system clipboard. Using local clipboard.

---

