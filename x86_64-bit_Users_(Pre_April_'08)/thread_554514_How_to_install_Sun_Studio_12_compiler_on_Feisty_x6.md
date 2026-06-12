---
title: "How to install Sun Studio 12 compiler on Feisty x64"
date: 2007-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ipina on 2007-09-19
Sun Studio 12 from Sun Microsystems is a C and Fortran GUI (IDE) compiler. I installed it on Ubuntu Feisty x64 in two x64 machines - AMD and Intel processors, respectively - I didn't have any problem in the one with the AMD processor following this procedure,
 1.- Download the Sun Studio 12  tarfile product, not the package installer.
 2.- Download the package JDK 6 Update 2 with NetBeans 5.5.1 and install it according to instructions.
 3.- Download  the System Preparation tool - tarfile install - and install and run it. This in spite of the fact that I'm not sure about its performance as, for example, being NetBeans installed, this tool warns about its lack - in such a case, ignore the warning -
 4.- Install the Sun Studio 12 tarfile which is an image.
 5.- It's important to read basic instructions in order to run properly the compiler. In this sense, the JDK_HOME environment variable and the PATH to the command 'sunstudio' should be included in the .profile file.
I wouldn't like to mean that because of the Intel processor I found problems installing SunStudio 12, I mean simply that in the machine with such a processor I had to do the following,
 A.- Download the tarfile product.
 B.- Download and install [COLOR="Red"]separately[/COLOR] JDK 6 and NetBeans 5.5.1. This as a consequence that the message 'the installer unable to run in graphical mode' appeared when I tried to follow 2.- above.
 C.- Download  the system preparation tool - tarfile install - and install and run it, if you like.
 D.- Install the Sun Studio 12 tarfile which is an image.
 E.- Taking care of 5.- above, I run the Fortran compiler and, however, I found two errors. The first involved 'ld: -lpthread'  and the second 'ld: -lm'. To be honest, I don't remember how the first one was exactly solved, although it was easy to find the library concerned by doing a Google search. I have to say that it wasn't the case with '-lm'. Anyway, the message 'ld: cannot find -lm' was overcame by installing libc6-dev.
Hope this helps someone with the same problems. Regards.

---

### Post by ipina on 2007-12-28
I've installed an update of the Sun Fortran compiler, the installation was fresh on a machine with Intel processor and Ubuntu 7.10. I had got visual effects because AWN on my desktop and my theme was Mac4Lin (Emerald theme manager). I followed instructions as on my former post but installation didn't work since my visual settings - an error occurred regarding gtk2,  which didn't allowed installation of netbeans - So I advise not to have such settings checked - System Preferences and Appearance, then in the Visual Effects tab check None - when installing the compiler. Once installed, visual effects may be allowed if you prefer. Hope this helps.

---

