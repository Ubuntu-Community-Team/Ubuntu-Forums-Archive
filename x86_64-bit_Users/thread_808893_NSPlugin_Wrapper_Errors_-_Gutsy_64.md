---
title: "NSPlugin Wrapper Errors - Gutsy 64"
date: 2008-05-26
forum: x86 64-bit Users
---

### Post by coldstatue on 2008-05-26
EDIT: the issue below was resolved the second time i re-ran the script from the sticky. 


Hey all, FireFox has been stalling at strange times for me over the last few days, so I decided to run from a term and got this 

```

*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Connection was NULL
sh: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** ERROR: NP_Initialize() invoke: Connection was NULL
sh: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client conn

```

I can't think of any recent changes I've made. I installed everything as per the sticky in this forum over a month ago. All was fine until the last few days. Now YouTube and Google Video are jacked up, but I don't have to be on a page with a video for it to stall. It seems like every 15 seconds or so, I have to wait 5-10 seconds for non-responsiveness. I re-ran the script, but it didn't fix anything. Suggestions?
Thanks.

---

### Post by asuastrophysics on 2009-11-16
i have the exact same problem. this started because i followed a "workaround" for a bug regarding un-clickable flash players.

nice workaround.

---

### Post by efflandt on 2009-11-16
It looks like you have remnants of the 64-bit nsplugin wrapper for 32-bit flash.  See if Synaptic shows flashplugin-installer installed and choose **Mark for Complete Removal**.  Or if that does not show it installed, install it and then completely remove it.

Then put the 64-bit libflashplugin.so back where it belongs.

With all the problems some people seem to be having with 64-bit and flash, I was surprised that flashplugin-installer worked fine when that was installed on 64-bit 9.10 live/install on bootable USB.

I had trouble with flashplugin-installer not working properly on my older Athlon64 and the real 64-bit flash crashing Firefox.  But my cpu is missing the lahf instruction, and the lahf fix plugin resolved that.  So now real 64-bit flash works fine.

---

### Post by asuastrophysics on 2009-11-16
i think this is a bug:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/444757](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/444757)

note un-clickable flash only happens when compiz is enabled. a (ghetto) workaround is to middle-click at the same time you left-click. not very practical though.

---

