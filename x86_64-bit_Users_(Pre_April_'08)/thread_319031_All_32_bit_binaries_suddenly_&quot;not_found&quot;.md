---
title: "All 32 bit binaries suddenly &quot;not found&quot; when trying to run them"
date: 2006-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by foxmajik on 2006-12-14
Hello,

I made some change to my system that broke all of my 32-bit applications.

I don't know what I did.

Previously, I could run Second Life and Swiftfox, but now I cannot.

When I try to run their launcher scripts I get this:

$ ./secondlife
./secondlife: 41: bin/do-not-directly-run-secondlife-bin: not found

or:

4$ swiftfox
/opt/swiftfox/run-mozilla.sh: 424: /opt/swiftfox/swiftfox-bin: not found

However the files are in fact there:

$ ls
app_settings      gridargs.dat            lsl_guide.html    secondlife.ico
bin               help                    README-linux.txt  skins
character         launch_url.sh           releasenotes.txt  unicode.ttf
featuretable.txt  lib                     res-sdl
fonts             licenses.txt            >>>secondlife<<<
gpu_table.txt     linux-crash-logger.bin  secondlife~

$ ls /opt/swiftfox | grep swiftfox-bin
swiftfox-bin

I also get "not found" when I attempt to execute the binaries directly.

I don't understand why I'm being told the file is "not found" when it is in fact there..?

---

### Post by xopher on 2006-12-15
This might be a permissions problem. Make sure they are still executables and that you are allowed to run them without superuser permissions.

---

### Post by foxmajik on 2006-12-16
> **xopher said:**
> This might be a permissions problem. Make sure they are still executables and that you are allowed to run them without superuser permissions.

I decided to backup the files  I needed, erase the 64bit install of Ubuntu and re-install the 32 bit version.

I don't foresee requiring the ability to run any applications that are strictly 64 bit anytime soon.

I don't understand why Ubuntu has to make running 32-bit applications on a 64-bit platform so difficult when other popular distros come with that functionality built in... ](*,)

BTW, this can't be a permissions problem, that's the wrong error for that problem.  The error for that would be "is not allowed to execute" or "permission denied" not "not found."

The error leads me to believe that the issue is that the system doesn't recognize the file as an executable because it's in the wrong format (32 bit) when that never happened before I did whatever I did to hose it.

Anyways, compare:

It took two weeks to iron out the 64-bit vs. 32-bit issues with 64 bit version of the Ubuntu distro:

"Lets see I like this program so I'll install it.  Oops there's no 64 bit version in the repositories, I guess I'll have to force architecture.  Oops now it wants libraries that aren't in the  "ia32" or "gtk32" or "linux32" packages so I'll have to download the 32bit debs and manually extract them to a folder, then copy them to another folder, then symlink them to another folder, then I'll just try it again.  Oh damn, now it says the lib is the wrong version.  Okay that's fixed, now it says it can't find the executable.

I guess I could compile it from source.  Damn, I can't do that, the compiler generates a bunch of errors I can't find on the forums anywhere.

I'll just assume the source is made for 32bit platforms and can't be compiled on a 64bit system.  Besides if I installed the app from source, if I wanted to remove it I'd have to manually find every single file installed by the 'make install' script and remove them one at a time.  And if a Debian package came out, I'd be screwed because when I tried to install it dpkg would fail and tell me that it can't because it's trying to overwrite an existing file, rather than just giving me an option to overwrite the damn file.

Or there's a 64 bit version but it's compiled once every four versions by a guy who doesn't speak English who lives at the south pole in a shack formerly inhabited by explorers and he only gets online to update his repository (which is down 3/4 of the time because someone is running a Quake server on the repository box) once a year when he travels to Germany to trade seal skins for back issues of Playboy."  (slamming face on keyboard at this point)

...only to have it break again, whereas I got the 32-bit platform version up and running, and customized with all of the applications I use, in under three hours.

So I'm coining a term for this miserable frustrated confusion to go along with "DLL hell" and "dependency hell."

I call it "platform hell."

It describes a situation where installing some software is above and beyond retarded in the amount of work required because of a difference of 32 bits.

---

