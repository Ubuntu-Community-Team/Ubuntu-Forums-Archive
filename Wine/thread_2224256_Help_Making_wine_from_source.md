---
title: "Help Making wine from source"
date: 2014-05-15
forum: Wine
---

### Post by abellesle on 2014-05-15
Hi all,
        When i try to instaall wine using ./tools/wineinstall. it does some make operations for about 5 min and throws up an error
i dont know what that error means... help at the earliest possible this is the error pls help i am installing wine from source 


make[1]: Leaving directory `/home/abel/Documents/wine-1.5.22/tools/wmc'
make[1]: Entering directory `/home/abel/Documents/wine-1.5.22/tools/wrc'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -DINCLUDEDIR="\"/usr/local/include/wine\""   -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wempty-body -Wignored-qualifiers -Wstrict-prototypes -Wtype-limits -Wunused-but-set-parameter -Wwrite-strings -gdwarf-2 -gstrict-dwarf -fno-omit-frame-pointer -Wpointer-arith -Wlogical-op  -g -O2 -U_FORTIFY_SOURCE -D_FORTIFY_SOURCE=0  -o parser.tab.o parser.tab.c
parser.y: In function ‘rsrcid_to_token’:
parser.y:2841:15: error: ‘YYLEX’ undeclared (first use in this function)
   lookahead = YYLEX;
               ^
parser.y:2841:15: note: each undeclared identifier is reported only once for each function it appears in
make[1]: *** [parser.tab.o] Error 1
make[1]: Leaving directory `/home/abel/Documents/wine-1.5.22/tools/wrc'
make: *** [tools/wrc] Error 2

Compilation failed, aborting install

---

### Post by T.J. on 2014-05-15
Make sure that bison is installed, and then try again.  If that doesn't help you, I'll test compile it myself for you to see if I can find a bug.

---

### Post by abellesle on 2014-05-16
i run sudo apt-get install bison and it shows already installed and latest version but same error occurs
what might be the problem. i also ran the command sudo apt-get build-dep wine
i again ran ./tools/wineinstall and i get the same error after 5min
pls help guys on a limited internet pack thats why

---

### Post by T.J. on 2014-05-16
Where and what version of the source are you downloading please?  I will see if I can help you by test compiling it. Also I need to know which version of Ubuntu you are using, please.

---

### Post by abellesle on 2014-05-16
I'm trying to compile wine 1.6 On ubuntu 14.04 LTS
even if i try to comile wine 1.5.23 it displays the same error

---

### Post by T.J. on 2014-05-17
> **abellesle said:**
> I'm trying to compile wine 1.6 On ubuntu 14.04 LTS
even if i try to comile wine 1.5.23 it displays the same error

 I'm not trying to sound rude, but I have some questions in order to find the best way to help you:

1) 14.04 already contains a copy of Wine 1.6. Is there a specific reason you need to compile a new version?
2)  Are you trying to compile source from WineHQ or from somewhere else?
3) Which version of Wine do you prefer please: version.revision numbers?

---

