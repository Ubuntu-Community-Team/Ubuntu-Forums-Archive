---
title: "Apple Shake 4.1"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by kyo007 on 2008-08-04
hi all, i am new in linux and i can't install shake. 

I have found some working information about shake :

1 - Install Ubuntu 8.04 (hardy) and GNOME 2.22.2
2 - Create folder /home/user/apple/ and /home/user/apple/shake/
3 - Copy content of "shake-v4.10.0606" to /home/user/apple/shake/
4 - Run: sudo apt-get install csh
5 - Download: libX11-1.0.3-8.fc7.i386.rpm
6 - Run: rpm2cpio libX11-1.0.3-8.fc7.i386.rpm | cpio -idmv ./usr/lib/libX11.so.6.2.0
7 - Run: mv ./usr/lib/libX11.so.6.2.0 /home/user/apple/shake/lib/libX11.so.6
8 - Start app: in bin folder type ./shake "   
 and other one 

   1. download the file libX11-1.0.3-8.fc7.i386.rpm
   2. install the 'alien' rpm conversion utility
   3. extract the rpm file
   4. locate libX11.so.6.2.0 and copy to the lib directory used by shake
   5. rename your moved copy of 'libX11.so.6.2.0' to 'libX11.so.6'
          * if you are running shake from the original directory that was created from the software's extraction, then the lib directory is found in the shake directory
          * (~./shake*/lib/)
   6. if you are using shake 4.1, then you should be able to run shake
   7. otherwise, enter shake's 'bin' directory
   8. open up shake's startup script './shake' with a text editor

now i have few question :

1. I installed x64 ubuntu and i read, i need to create 32lib for shake.
2. what does mean "hardy" ? 
3. Can you write me installation with step by step ?


Thanks.

---

