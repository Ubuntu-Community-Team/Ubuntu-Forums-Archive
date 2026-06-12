---
title: "java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM"
date: 2009-09-14
forum: x86 64-bit Users
---

### Post by Zilioum on 2009-09-14
I use the Azsmrc Remote control tool on my notebook to control my download server. I now want to use Azsmrc on my new Desktop that runs jaunty 64bit. I copied the Azsmrc folder from my notebook to the desktop, ran the script and got the following error. 

```
java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:177)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
	at org.eclipse.swt.internal.C.<clinit>(C.java:21)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:130)
	at lbms.azsmrc.remote.client.swtgui.RCMain.init(RCMain.java:619)
	at lbms.azsmrc.remote.client.swtgui.RCMain.start(RCMain.java:168)
	at lbms.azsmrc.remote.client.swtgui.Starter.launch(Starter.java:22)
	at lbms.tools.launcher.Launcher.main(Launcher.java:63)

```

I did install Java and I also tried to solve the problem by installing the swt packages, nothing worked. Any suggestions?

Update: You can find the solution to this problem [here]("http://ubuntuforums.org/showthread.php?t=1352579").

---

