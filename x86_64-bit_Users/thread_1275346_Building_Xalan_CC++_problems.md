---
title: "Building Xalan C/C++ problems"
date: 2009-09-25
forum: x86 64-bit Users
---

### Post by B Yoder on 2009-09-25
I am using 64-bit Ubuntu 8.04 LTS and building the C/C++ ICU, Xerces, and Xalan 10 libraries (for portable Unicode, XML, and XSLT support, respectively). All has been running well for a long time now.

But with the most recent kernel and kernel header updates (made available last week, but I delayed installation until this morning), something has gone seriously wrong with my otherwise unchanged application.

When rebuilding the same ICU, Xerces, and Xalan libraries that I've been using successfully on 8.04 for the past year, I noticed that the runConfigure and make all went OK, but the **sudo make install** failed for the ICU and Xalan. The ICU's failure didn't look too serious (some verification tests that I don't need), but Xalan failed right away because it couldn't find the file:

/version.incl

Looking inside the Makefile, I see the file it's looking for is:

include $(XALANCROOT)/version.incl

Which then implies that $(XALANCROOT) was evaluated as an empty string (not found in the environment or by definition. This doesn't seem as if it is behaving correctly, especially since it has always worked properly before, including two months ago when I most recently rebuilt and reinstalled it.

I verified that the XALANCROOT environment variable is set correctly. And this make install command used to work flawlessly on all previous Fedora and Ubuntu releases and also on the current Ubuntu 8.04 release up until the latest kernel updates.

In the past, I've had to update the ICU, Xerces, and Xalan libraries as needed to match the stricter and more correct behaviors of the progression of gcc and g++ changes. But this time, the only change was the most recent kernel / kernel header patch.

 I have another problem with my application that popped up first when an Ubuntu update changed the runtimes and headers enough to cause incompatibility between libraries built with the old headers and libraries built using the new headers.When that finally occurred to me, I felt really stupid, deleted all my application libraries' old objects, and rebuilt every nook and cranny from scratch. The application worked perfectly after that.

But after the latest update, my application is exhibiting the same erroneous behavior. So I again deleted all of the objects from every nook and cranny of my application and rebuilt the whole thing... except for the ICU, Xerces, and Xalan libraries (as the problem is not related to them in any way). But this time, the erroneous behavior remains.

Any thoughts? It seems as if a header file has changed but the library that it describes wasn't included in the list of updates, or else doesn't match the latest updates.

[COLOR=Navy]UPDATE: I spoke with a very good friend, and he offered two suggestions on my issues:
1. Ubuntu's security team has made changes to the shell in which a subset of the environment variables are not passed along to child processes. He thought this would explain my missing XALANCROOT issue.
2. Having kernel header files that don't match the run-time objects is becoming a more common problem.

He stressed that these are his guesses. He also recommended the Long-Term Support releases of Ubuntu. Well, I am running 8.04 LTS. I also tried rebuilding my application on AIX and on RedHat ES 4 and it built and ran perfectly. It definitely appears to be an Ubuntu 8.04 problem.[/COLOR]

---

### Post by B Yoder on 2009-10-06
Today I applied the latest Ubuntu 8.04 updates, including the kernel headers and C runtimes. After restarting, Ubuntu refused to boot completely. It dropped out of its GUI boot screen into plain text mode. At the bottom of the screen it said that the kernel was running. Near the middle of the screen was the prompt (replacing my computer's host name with <hostname>):

<hostname> login:

It would appear to timeout and retry this screen several times. Then the monitor dropped into power saver mode.

So once I pulled the power and restarted, I intercepted the Grub menu and booted the old 2.6.24-22 generic kernel. Now I was able to boot.

I then configured my system to always boot this kernel by:

$ sudo gedit /boot/grub/menu.lst

At the end of this file are a collection of stanzas, one per kernel. They aren't explicitly numbered; you have to do that yourself. Counting down from the first kernel which is 0, and counting each stanza as a separately numbered kernel, both the recovery and non-recovery stanzas, I found that stanza 4 pointed to the kernel.

So near the top of this file is the default keyword and it was initialized to 0. I changed it to 4. Now I can reboot (killing Gnome with Ctrl-Alt-Backspace, for some reason) and come back to a working kernel.

I am not sure why Ubuntu 8.04 LTS has suddenly turned into a dyfunctional and broken C/C++ development platform. My custom-built (from the ground up) database application compiles and runs perfectly on Red Hat ES and AIX. And on Ubuntu 8.04 up to a month ago.

Ubuntu is a compelling desktop distribution, but I get paid to write code. So Ubuntu has slipped out of the role of a development platform, and is now just an X-Server to other functioning development platforms. I don't have time to explore all of the myriad combinations, so for now I'll just leave things in their almost-working state and move forward. For instance, I've been told to run Fedora Core 10 (not 11), but I'd hate to fix one thing and find 20 more that no longer work.

So for now, this is an evidence trail for others to heed, and not a plea for help. If help is forthcoming, I trust that its being developed behind the scenes and I will patiently await the future.

---

### Post by edo1080 on 2009-11-01
about your xml-xalan problem, I have the same error when I try to install it; have you tried to make tests before? 

I've one more error before trying to install, please look here:
```

make -C Tests tests
make[1]: ingresso nella directory «/home/edoardo/Librerie/xml-xalan/c/Tests»
mkdir -p ../lib
mkdir -p ../bin
g++ -O2 -DNDEBUG     -fno-elide-constructors -Wall -fPIC -DLINUX -D_REENTRANT -DXALAN_INMEM_MSG_LOADER -c -I/home/edoardo/Librerie/xml-xalan/c/src -I/home/edoardo/Librerie/xml-xalan/c/include -I../nls/include -I/home/edoardo/Librerie/xerces-c-3.0.1/src/ -I/home/edoardo/Librerie/xerces-c-3.0.1/include/xercesc -I/home/edoardo/Librerie/xerces-c-3.0.1/include/  -o ../obj/conf.o /home/edoardo/Librerie/xml-xalan/c/Tests/Conf/conf.cpp
In file included from /usr/local/lib/gcc/i686-pc-linux-gnu/4.4.2/../../../../include/c++/4.4.2/backward/strstream:46,
                 from /home/edoardo/Librerie/xml-xalan/c/src/xalanc/Harness/XalanFileUtility.hpp:30,
                 from /home/edoardo/Librerie/xml-xalan/c/Tests/Conf/conf.cpp:61:
/usr/local/lib/gcc/i686-pc-linux-gnu/4.4.2/../../../../include/c++/4.4.2/backward/backward_warning.h:28:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated.
/home/edoardo/Librerie/xml-xalan/c/Tests/Conf/conf.cpp: In function &#8216;int main(int, char**)&#8217;:
/home/edoardo/Librerie/xml-xalan/c/Tests/Conf/conf.cpp:507: error: no matching function for call to &#8216;xercesc_3_0::XMLPlatformUtils::Initialize(const char [], int, int, xalanc_1_10::XalanDiagnosticMemoryManager*, bool)&#8217;
/home/edoardo/Librerie/xerces-c-3.0.1/src/xercesc/util/PlatformUtils.hpp:173: note: candidates are: static void xercesc_3_0::XMLPlatformUtils::Initialize(const char*, const char*, xercesc_3_0::PanicHandler*, xercesc_3_0::MemoryManager*)
/home/edoardo/Librerie/xerces-c-3.0.1/src/xercesc/util/PlatformUtils.hpp:227: note:                 static void xercesc_3_0::XMLPlatformUtils::Initialize(XMLSize_t, XMLSize_t, XMLSize_t, const char*, const char*, xercesc_3_0::PanicHandler*, xercesc_3_0::MemoryManager*)
make[1]: *** [../obj/conf.o] Errore 1
make[1]: uscita dalla directory «/home/edoardo/Librerie/xml-xalan/c/Tests»
make: *** [tests] Errore 2

``` 

Please let me know if you have the same error on tests, failing make test would mean Xalan would fail even if I could solve the install issue?

---

