---
title: "Mac On Linux Blues"
date: 2005-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by elliotcater on 2005-11-17
Goddamn! 

I've hit one of those barriers that no one else on the forum has run into. I think. 

I'm trying to install mol despite poor documentation and assumption that all "human beings" are geeks.  I get to the,     

[COLOR="SeaGreen"]sudo debian/rules binary-mol-modules[/COLOR]      

step and am confronted by error messages advising      

[COLOR="SeaGreen"]dh_testroot
dh_installdocs
dh_installmodules
dh_installchangelogs
Use of uninitialized value in hash element at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 369.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
Use of uninitialized value in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
Use of uninitialized value in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 323.
found eof where expected first heading at /usr/lib/dpkg/parsechangelog/debian line 136.
dh_installchangelogs: changelog parse failure
make: *** [binary-mol-modules] Error 1
[/COLOR]

proper stuck now and have exhausted all literature available to me at this point!

Dyin for some help

Regards  Elliot

---

### Post by elliotcater on 2005-11-17
Actually just read the previous post in ppc users section, it appears I am up to the same point! I'll watch for his replies.  the last line of the return dialogue is 

"touch build-stamp"

mmkay...

---

### Post by tmeier on 2005-11-17
I hit the same point at one time also, are you sure that your previous step worked without errors.  I found that I did not have m4 installed and so my "sudo debian/rules build" did not work even though it showed a long list of things it might have done.

If it says nothing to build if you try the previous step, just "sudo rm build-stamp" and then do the "sudo debian/rules build" again and it will go through the whole thing.

To get m4, do a "sudo apt-get install m4" or do it from the synaptic package manager, which I did.

A thought anyway.

---

