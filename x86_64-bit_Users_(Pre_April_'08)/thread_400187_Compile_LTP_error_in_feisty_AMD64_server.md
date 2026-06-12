---
title: "Compile LTP error in feisty AMD64 server"
date: 2007-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hooman on 2007-04-03
I have just installed ubuntu 7.0.4 beta AMD64 on my new PC yesterday. 
And now I'm trying to compile LTP 20070331 but get following error:

```
make[4]: Entering directory `/opt/testSuite/ltp-full-20070331/testcases/network/tcp_cmds/ftp'
../../generate.sh
../../generate.sh: 60: arith: syntax error: "cnt--"
make[4]: *** [generate] Error 2
```

Using Google I find something like that > LTP 20061222 does not even compile on Ubuntu 6.10. The error message is ../../generate.sh: 60: arith: syntax error: "cnt--" and the line in question is while [ $((cnt--)) -gt 0 ] ; do. If you do a loop unrolling by hand it fails later when you try to run the LTP tests even before it tries the first test.

I realy want to know how to resolve this issue, and how to use LTP with my ubuntu.

---

### Post by un1xl0ser on 2007-04-10
There seems to be ltp packages that come with Ubuntu. Those should work better. As far as your current issue, it has to do with the fact that the decrement on line 60 of generate.sh is not working properly for some reason.

BASH can behave differently depending on if it is called as /bin/sh or /bin/bash. The #! in that script used /bin/sh, so on a hunch I ran it with /bin/bash and it worked fine.

Try something like this...
```

cd /opt/testSuite/ltp-full-20070331/testcases/network/tcp_cmds/ftp
bash ../../generate.sh
cd /opt/testSuite/ltp-full-20070331
make

```

YMMV

---

