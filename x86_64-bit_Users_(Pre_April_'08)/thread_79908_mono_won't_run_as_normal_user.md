---
title: "mono won't run as normal user"
date: 2005-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by ianikeev on 2005-10-21
I deleted the version of mono I compiled for use with Hoary and installed 1.1.8.3 from the repository. Everything went perfectly, but I observe that it only works correctly (i.e. compiles or runs compiled code) under root account. That's really weird and does anyone know the reason for this? The same goes for monodoc and monodevelop. Mono is kind of vital for my extra work and it would be a pita to have to recompile it myself each time I want to install and upgrade.:confused:

---

### Post by RAOF on 2005-10-22
I would guess that you don't have the permissions set correctly.  Run in a console "ls -lah /usr/bin/mono", and you should get the full info should start with "-rwxr-xr-x" or somesuch.  That's the permissions for the mono binary, in this case:
Owner: read,write,execute
Owner's Group: read,execute
Everyone Else: read, execute.

If it's something different, you should probably try "sudo chmod +rx /usr/bin/mono"

EDIT:  Sorry.  Looking again, I see that you've installed the version from the repository.  I still imagine that it's a permissions problem, but you could try removing and reinstalling the package.  That might fix the problem?

---

### Post by ianikeev on 2005-10-24
Hi,

No, it wasn't a permissions problems, because when run as

$ mono

it would print out all kinds of usage info. mcs would also seem to run, but stalled at once. Anyway, with permissions I'd expect smth like "permission denied."

The real question is, however, when we are going to get recent support for mono. I still had to install the newest versions by hand and checkinstall (the 1.1.8.3 had a nasty bug that interfered with my work, so I just didn't investigate it further as soon as I remembered). I could make my builds available, but they are not proper .debs and don't have all kinds of dependency info and so on.

---

### Post by RAOF on 2005-10-24
Unless there's some security bugfix, what we've got in the repositories now is pretty much it, for the supported stuff at least.

Once Dapper's really up and running you can expect a backports repository with the best stuff from there.

Back to the actual problem:  what happens if you try "mcs helloworld.cs" or somesuch?  My mono works fine...

Possibly the library paths aren't set up right?  Maybe?  Wrong permissions on some of the libaries? ;)

---

### Post by ianikeev on 2005-10-24
well, mcs hello.cs would end in silence until I press Ctrl-C. OF course, now with self-compiled stuff it doesn´t happen.

---

### Post by TimT on 2005-10-24
Hmm, solved problems with tomboy and beagle just now..

Turns out Ihad an old .wapi directory in my home,containing some shared_data.
(Probably left over from an older install, in a chroot..) 

anyway:removed the directory and now beagle and tomboy start.. 

 Hope this helps.

---

### Post by RAOF on 2005-10-24
[QUOTE=ianikeev]well, mcs hello.cs would end in silence until I press Ctrl-C. OF course, now with self-compiled stuff it doesn´t happen.[/QUOTE]
Well, I'm glad it works now.  I still have no idea why that would happen :)

---

### Post by DancingSun on 2005-11-29
I got the same problem.  When I launch a mono application in my userspace, the process will spawn, and I can see the CPU usage go up.  But the GUI does not come up.

---

### Post by DancingSun on 2005-11-29
Hmm...removing ".wapi" directory worked for me as well...what is this directory?

---

