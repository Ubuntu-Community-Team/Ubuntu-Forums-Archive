---
title: "How to get IBM Softcopy Reader running on AMD64 8.04 HARDY"
date: 2008-10-08
forum: x86 64-bit Users
---

### Post by jym on 2008-10-08
[FONT="Courier New"]
[SIZE="2"]
# "IBM Softcopy Reader for Linux V3.7" is used to search and view IBM mainframes documentations
#  stored in "*.boo" files. Books are on shelves described by "*.bkd" files
# [http://www-01.ibm.com/support/docview.wss?doc=4000251&org=SW&rs=4](http://www-01.ibm.com/support/docview.wss?doc=4000251&org=SW&rs=4)

# steps to fix encountered problems:
# 1 - libc6-i586 must be installed. ( 32bit shared libraries for AMD64: sounds like MVS 24/31/64 ! ) 
# 2 - java for i586 must be installed from java sun site
# 3 - in "hlcs.sh" and "hlcb.sh" from Softcopy Reader, "java" calls must be modified to "$JAVA_HOME/bin/java" if i586 JRE is not the default 
# 4 - must start with "MALLOC_CHECK_=0" to bypass :? "munmap_chunk(): invalid pointer" 

# this text is in "sh" format
# following paths can be "customized"
# /home/zdata/programs/IBMreaderV3.7
# /home/zdata/programs/jdk-6u7-linux-x64
# /home/zdata/programs/jdk-6u7-linux-i586

# uncomment following mount to activate the "no noise option"
# iso image of zSeries documentation DVD
# sudo mount -v -o loop,ro -t iso9660 /home/zdata/iso/zseries/UAF013.iso /home/zdata/mnt/zOS1.9_doc

# establish Softcopy Reader current path
cd /home/zdata/programs/IBMreaderV3.7/sys/

# according to "slinread.txt" of the "ilrjaval.tgz" from Softcopy Reader  
export LD_LIBRARY_PATH=/home/zdata/programs/IBMreaderV3.7/sys/
echo LD_LIBRARY_PATH=$LD_LIBRARY_PATH

# "[COLOR="Red"]libhlcwam.so: wrong ELF class: ELFCLASS32[/COLOR]" error occurs with this JRE   
export JAVA_HOME=/home/zdata/programs/jdk-6u7-linux-x64
echo 
echo JAVA_HOME=$JAVA_HOME
$JAVA_HOME/bin/java -version
echo

# [COLOR="Green"]ELFCLASS32 error doesn't occur with this one[/COLOR]
export JAVA_HOME=/home/zdata/programs/jdk-6u7-linux-i586
echo 
echo JAVA_HOME=$JAVA_HOME
$JAVA_HOME/bin/java -version
echo

# "[COLOR="Green"]MALLOC_CHECK_=0[/COLOR]" to bypass "[COLOR="Red"]munmap_chunk(): invalid pointer[/COLOR]" when searching shelves or books
MALLOC_CHECK_=0 ./hlcs.sh  -s -u /home/zdata/mnt/zOS1.9_doc/shelves -b -u /home/zdata/mnt/zOS1.9_doc/books


echo leaving IBM Softcopy Reader
# 
# sudo umount -v /home/zdata/mnt/zOS1.9_doc/

[/SIZE]
[/FONT]

---

