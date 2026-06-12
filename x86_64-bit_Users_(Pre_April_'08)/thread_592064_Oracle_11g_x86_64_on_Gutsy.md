---
title: "Oracle 11g x86_64 on Gutsy"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by mb0108 on 2007-10-26
Hi all, 

I try to get Oracle 11g installed on my Gutsy installation, 10gR2 64 bit is installed and runs. It was installed in Feisty and it still runs after all upgrades to Gutsy. 
Now I get errors in the installation of 11g in Gutsy. I think the error is, that some parts in /lib are 64 bit whereas they are 32 bit in Redhat or suse. The 32 bit part linking fails 
Here is a part of the make:

Linking external procedure agent (/opt/oracle/11G/rdbms/lib/extproc32)
rm -f /opt/oracle/11G/rdbms/lib/extproc32
gcc -m32 -o /opt/oracle/11G/rdbms/lib/extproc32 -L/opt/oracle/10g/product/10.2.0/db/rdbms/lib32/ -L/opt/oracle/10g/product/10.2.0/db/lib32/ -L/opt/oracle/10g/product/10.2.0/db/lib32/stubs/   /opt/oracle/10g/product/10.2.0/db/rdbms/lib32/hormc.o  /opt/oracle/10g/product/10.2.0/db/rdbms/lib32/defopt.o  /opt/oracle/10g/product/10.2.0/db/rdbms/lib32/homts.o              -lagtsh -lpls10  -lplp10 -lpthread  -lclntsh -lsnls10 -lnls10  -lcore10 -lsnls10 -lnls10 -lcore10 -lsnls10 -lnls10 -lxml10 -lcore10 -lunls10 -lsnls10 -lnls10 -lcore10 -lnls10 /opt/oracle/10g/product/10.2.0/db/lib32/libgeneric10.a   `cat /opt/oracle/10g/product/10.2.0/db/lib32/sysliblist` -Wl,-rpath,/opt/oracle/10g/product/10.2.0/db/lib -lm    `cat /opt/oracle/10g/product/10.2.0/db/lib32/sysliblist` -ldl -lm   -L/opt/oracle/10g/product/10.2.0/db/lib  -lvsn10
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libgcc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld gab 1 als Ende-Status zurück
make: *** [/opt/oracle/11G/rdbms/lib/extproc32] Fehler 1

Thanks for help, 
Michael

---

### Post by Ehtetur on 2007-11-01
> **mb0108 said:**
> Now I get errors in the installation of 11g in Gutsy. I think the error is, that some parts in /lib are 64 bit whereas they are 32 bit in Redhat or suse. The 32 bit part linking fails 

I don't think you can compile the x86 version of 11g on Ubuntu x64_86...
If you're set on trying, first install the lib32 dependencies...

Why not save yourself some headaches and use the x64_86 version of 11g?
 
As a side note, unlike for Oracle 11g, Ubuntu **is** certified for IBM's DB2!! :KS
[http://www.ubuntu.com/news/db2cert]("http://www.ubuntu.com/news/db2cert")

---

### Post by Rmantingh on 2007-11-02
I'm a newbie and had similar problems with installing 11g x86_64 on Gutsy.
I followed the instructions more or less as per [http://www.dizwell.com/prod/node/1046](http://www.dizwell.com/prod/node/1046)
but they are aimed at 32-bit installation.
During the linking stage I ran into problems with 'incompatible' nonshared libraries
such as /usr/lib/libpthread_nonshared.a and /usr/lib/libc_nonshared.a but the
way I got it to working (somehow - by trial and error) is by removing the
$ORACLE_HOME/lib32 directory (leaving the /lib one) and changing the make files
(.mk) to remove the 32 bit references. Apparently Oracle tries to link some
32-bit counterparts along with 64-bit. Not sure why.
The only tool I couldn't get to link was "ctxhx" as Oracle only supply a
32-bit object for that. If you don't need text searching facilities (CTX) then
I guess you can ignore it. I have been able to create a database without it.
As said before I'm a newbie to Linux and am just messing around but I did
get it to work somehow.
Oh, by the way, I started with a fresh install of Gutsy, not and upgrade.

---

### Post by Rmantingh on 2007-11-07
Mike0108 on Oracle Forums has a better solution:
[http://forums.oracle.com/forums/thread.jspa?forumID=64&threadID=577066](http://forums.oracle.com/forums/thread.jspa?forumID=64&threadID=577066)

<quote>
I 've now managed to get 11g working on Gutsy x86_64. I did it the following way:
When a link fails I looked into ORACLE_HOME/install/make.log and copy the last make to a shell. Then I added -L/usr/lib32 after the gcc -m32. Then clicked on Retry and repeat the procedure for the next error. So I do not loose some 32 bit things that may be important for some functionality.
<end quote>

It worked for me.

---

### Post by mb0108 on 2007-11-09
Thank you... I just wanted to place my solution here too :-)

---

### Post by Rmantingh on 2007-11-09
Sorry Michael, it didn't click with me..... the names.
Didn't mean to steal your thunder :-)

---

### Post by mb0108 on 2007-11-11
No problem :-)

---

### Post by mmilkin on 2008-03-14
So I tried that however i now get linker errors 

INFO: gcc -m32 -o /opt/oracle-home/oracle/11.1.0/db_1/rdbms/lib/extproc32 -L/opt/oracle-home/oracle/11.1.0/db_1/rdbms/lib32/ -L/opt/oracle-home/oracle/11.1.0/db_1/lib32/ -L/opt/oracle-home/oracle/11.1.0/db_1/lib32/stubs/   /opt/oracle-home/oracle/11.1.0/db_1/rdbms/lib32/hormc.o   /opt/oracle-home/oracle/11.1.0/db_1/rdbms/lib32/homts.o		  -lagtsh -lpthread -lclntsh   `cat /opt/oracle-home/oracle/11.1.0/db_1/lib32/sysliblist` -Wl,-rpath,/opt/oracle-home/oracle/11.1.0/db_1/lib32 -lm    `cat /opt/oracle-home/oracle/1
INFO: 1.1.0/db_1/lib32/sysliblist` -ldl -lm   -L/opt/oracle-home/oracle/11.1.0/db_1/lib32 

INFO: /
INFO: usr
INFO: /
INFO: bin
INFO: /
INFO: ld
INFO: :
INFO:  
INFO: cannot
INFO:  
INFO: find
INFO:  
INFO: -
INFO: lagtsh
INFO: 

INFO: collect2: 
INFO: ld returned 1 exit status
INFO: 

INFO: make[1]: Leaving directory `/opt/oracle-home/oracle/11.1.0/db_1/rdbms/lib'

INFO: make[1]: 
INFO: *** [/opt/oracle-home/oracle/11.1.0/db_1/rdbms/lib/extproc32] Error 1
make: *** [extproc32] Error 2

INFO: End output from spawned process.
INFO: ----------------------------------
INFO: Exception thrown from action: make
Exception Name: MakefileException
Exception String: Error in invoking target 'all_no_orcl' of makefile '/opt/oracle-home/oracle/11.1.0/db_1/rdbms/lib/ins_rdbms.mk'. See '/u01/app/oraInventory/logs/installActions2008-03-13_05-58-42PM.log' for details.
Exception Severity: 1


the libs are there in the $oracle_home/lib and $oracle_home/lib32
any Ideas?

---

### Post by Rmantingh on 2008-03-15
After the installion (and continuing whenit throws up errors) I actually change
some of the make files and relink with:-

$ORACLE_HOME/bin/relink all >relink.log 2>&1

The files I change are:-
  /opt/oracle/11g/bin/genclntsh
  /opt/oracle/11g/bin/genagtsh
  /opt/oracle/11g/ctx/lib/env_ctx.mk
  /opt/oracle/11g/rdbms/lib/env_rdbms.mk

/opt/oracle/11g is where I installed oracle.

I don't have the original contents of the files anymore but below
is the contents after the changes. Search for similar lines and
change them to the contents below.

You may have to run relink a couple of times to get rid of all the errors.

It works for me.

----------------------------------------------------------------------------------------------
vi /opt/oracle/11g/bin/genclntsh

[ "$1" = "lib32" ] &&  ULIB="lib32" &&  LOOP="DONE" && CF=-m32 && USRLIB32=-L/usr/lib32
LD="gcc ${CF} -shared -Wl,-relax ${STUBS} ${USRLIB32} -L${OLIB}"

----------------------------------------------------------------------------------------------
vi /opt/oracle/11g/bin/genagtsh

if [ $1 != "-32" ]; then
    LIB_NAME=$1                 # Library name
    LIB_VER=$2                  # Library version number
    LIB=lib
    NON64_LDOPT=
    USRLIB32=
else
    LIB_NAME=$2                 # Library name
    LIB_VER=$3                  # Library version number
    LIB=lib32
    LOOP="done"
    NON64_LDOPT="-m32"
    USRLIB32=-L/usr/lib32
fi

LD="gcc ${NON64_LDOPT} -shared ${USRLIB32} -L${ORACLE_HOME}/${LIB} -L${ORACLE_HOME}/${LIB}/stubs"

----------------------------------------------------------------------------------------------
vi /opt/oracle/11g/ctx/lib/env_ctx.mk

LDFLAGS32=$(AMD32FLAGS) -o $@ -L/usr/lib32 $(LDPATHFLAG)$(PRODLIBHOME32) $(LDPATHFLAG)$(LIBHOME32) $(LDPATHFLAG)$(LIBHOME32)stubs/

----------------------------------------------------------------------------------------------
vi /opt/oracle/11g/rdbms/lib/env_rdbms.mk

REDEFINES32=LIBDIR=lib32 LDFLAGS='-m32 -o $$@ -L/usr/lib32 $$(LDPATHFLAG)$$(PRODLIBHOME) $$(LDPATHFLAG)$$(LIBHOME) $$(LDPATHFLAG)$$(LIBHOME)stubs/'

---

