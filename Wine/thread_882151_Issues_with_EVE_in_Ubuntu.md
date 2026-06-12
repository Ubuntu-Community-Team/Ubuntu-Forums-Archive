---
title: "Issues with EVE in Ubuntu"
date: 2008-08-06
forum: Wine
---

### Post by digiport on 2008-08-06
I'm hoing this is the right place to post this...

Here is the report I get.......

Running... /home/adamann/.cedega/.ui/runGUI
/home/adamann/.cedega/.winex_ver/winex-eve-000099/bin/winex3: 160: /home/adamann/.cedega/.winex_ver/winex-eve-000099/winex/bin/pthreads_stack_test: not found
[: 160: 0: unexpected operator
/lib/ld-linux.so.2: could not open


Any thoughts?

Also when I go to the config tool it says this automatically...

You appear to be missing one or more dependencies for the system tests. This could be because your 64-bit system is missing the 32-bit emulation libraries. Without them, the tests and other auxiliary programs will not run.


not a dynamic executable

ANy assistance would be great.

---

### Post by aoanla on 2008-08-07
Since you haven't bothered to tell us, I will guess that you're running 64bit Hardy, yes?

The 32bit libraries that it asks you to install are called "ia32-libs"
Install them with Synaptic, on from a terminal if you're happy with that.

Tell us if that fixes things.

Also, which patch level are you using? The appdb entries for the different EVE patches suggest that you should be okay with 3.21 or higher.

If the fix suggested doesn't work, don't forget to give us more information about your system. We can't magically know what graphics card, version of wine, drivers, etc you have installed, and this can be important to debugging issues.

---

