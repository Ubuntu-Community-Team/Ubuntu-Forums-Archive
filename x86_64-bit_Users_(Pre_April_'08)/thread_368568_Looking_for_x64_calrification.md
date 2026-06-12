---
title: "Looking for x64 calrification"
date: 2007-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by CounterStrike on 2007-02-23
First off this is my first post after using Ubuntu and lurking in these forums for probably 6 months. I am officially turned (in my attitude anyway), as I am now looking to linux whenver the oppurtunuity comes up for replacing a MS box. I am a systems admin, and have always worked in/with MS products, and my comapny is a MS partner.
    I have some questions that I have been unable to find answers to (searching these forums or google) and was hoping I could get some help so I can move forward.

 - I am aware of the advantages of 64bit vs 32bit, but am unclear as to the differences in the amd64 kernel as opposed to the amd64-server, amd64-generic and amd64-xeon. I ask because I installed dapper and even though I chose the server install, I ended up with the xeon kernel. The processor it was installed on is a P4 HT 3GHZ (Intel processor stupid nomenclature 630). I am interested (for this discussion anyway) to specifically address a server install - ending up with just a command line and no desktop manager of any kind (no need for the extra overhead). I guess I need to understand what features are bundled into different kernel versions, and if the "server" kernel has specific features that the others don't have.
-  I was under the assumption that the problem with 64bit windows was that there was not a great many 64 bit applications to run on it. I figured that this would not be the case in dapper 64, since you have the oppurtunity to (and sometimes forced to due to no package available) compile with your own compiler (being 64bit) and thereby creating 64 bit versions of applications. Since further looking into this on the forums, several people state that 64 bit is backwards compatible with the 32 bit older brother, and I in turn see a lot of instructions on how to install and force a 32 bit version of an app onto a 64 bit system. So...Am I completely off in thinking that if you have the source code for an app, that you can simply compile it into a 64bit app?
-  This sort of goes to the question above but is specific to the scenario I am trying to implement. I have a 64bit system (hardware) with 8gb of RAM. My plan is to install 64bit dapper and then vmware server. The unclear part is the vmware server, as I am not sure if it really is 64bit or 32 bit after it is installed. My intenet was to use the 64bit version of dapper to allow vmware server to address the >4gb of memory without using PAE (not that I have even seen the linux equivalent yet, but assume it is possible). So basically, the ideal thing  there would be for vmware server to host multiple vm's and utilize (fully and unimpeded) the 8GB of memory. Am I way off here? 

As I am coming over from the windows server world, I also am trying to implement Raid and other rendundancies, but I know that raid is definetly nothing specific to the 64bit world so I will post to another forum.

Thanks,

Brian

---

### Post by Kilz on 2007-02-23
> **CounterStrike said:**
> 
-  I was under the assumption that the problem with 64bit windows was that there was not a great many 64 bit applications to run on it. I figured that this would not be the case in dapper 64, since you have the oppurtunity to (and sometimes forced to due to no package available) compile with your own compiler (being 64bit) and thereby creating 64 bit versions of applications. Since further looking into this on the forums, several people state that 64 bit is backwards compatible with the 32 bit older brother, and I in turn see a lot of instructions on how to install and force a 32 bit version of an app onto a 64 bit system. So...Am I completely off in thinking that if you have the source code for an app, that you can simply compile it into a 64bit app?


Most of the things that need to be forced in are proprietary codecs and plugins and the applications that use the 32bit codecs and plugins. There are also a few proprietary applications that some force in. But the number is real small. The reason we do is because we dont have the source for them, if we did , it wouldnt need to be done. Most (if not all) of the applications are only needed for desktop use. So you may not even have to install any if you are running a server.

---

### Post by CounterStrike on 2007-02-27
Thanks for the answer Kilz.

Thanks,

Brian

---

### Post by CounterStrike on 2007-03-07
Kilz,


    I came across your posts regarding the genric kernel for edgy and the non-coninutation of the specific kernel compilations that exist for dapper last night. As this generic compilation now makes the kernel question not applicable for edgy, I still have a question regarding the dapper kernels. I was planning on using dapper due to the long term support and still am unable to find the answer as to what the difference is between the amd64-xeon, amd64-server and other compilations of the kernel. Although I am asking about the 64 bit kernels, this is more of a general question as I am curious about the differences between all the kernel versions (more than the obvious difference of being a kernel for a 386 or powerpc). Can anyone point me to a link that states what is inlcuded in each specific kernel or just shed some light on this? 

Thanks,

Brian

---

### Post by Mongoose on 2007-03-07
Well, in general the server builds of the kernel include more modules and built-in features for things such as knfsd ( nfs server in kernel ).  Architectures are for optimizations for those specfic CPUs and chipsets.  You can read changelogs and detailed descriptions about the various kernel builds in the documentation inside each package.   Also you can try to fetch such changelogs here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Also the server install opposed to the desktop install of ubuntu assumes headless, but you can add-on X and GNOME if needed.  From your other post it doesn't seem you understand the module nature of ubuntu / debian.  Basically, you can strip down or add-on as many componets as you wish to fulfill your needs -- and there are several meta-packages that provide base configurations for desktop-kde, desktop-gnome, server (headless), etc.  Coming from Windows this might be a change, since the GUI isn't considered a core part of the OS.   However on a desktop or certain monitoring servers you'd want it -- hence the meta-package profiles to make things easy to install subsystems with many dependencies.  ^_^

Welcome to Linux.  Also be aware of other sister forums here focused on things such as gaming, development, etc.  =)

---

### Post by CounterStrike on 2007-03-07
Mongoose,

   Thanks for the clarification. You are correct that I don't fully have a handle on the module approach to the kernel. I do understand the headless aspect and the non-need for a gui on most server instances. I have a problem that most of the how-to's are written from the perspective of installing ubuntu from the live cd. With my servers I am using a pxe server to install dapper server, which makes things confusing trying to relate to setting up raid (which assumes you are installing from live cd).
    I guess at the end of the day, with respect to the 64bit portion anyway,  I just want to ensure that the kernel I will be using is going to take advatage of the capabilities of the processor and not be so overburden with features that will not be used (being that it will be a server without a desktop manager).

Thanks,

Brian

---

### Post by Mongoose on 2007-03-07
I mostly work on graphics and odds and ends with visualization -- so I can't speak for raid setup.  I'm sure in the future if you have specific questions others here can help out.  ^_^

---

