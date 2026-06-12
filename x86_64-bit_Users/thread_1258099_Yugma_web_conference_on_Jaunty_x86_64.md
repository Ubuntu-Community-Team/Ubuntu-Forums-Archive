---
title: "Yugma web conference on Jaunty x86_64"
date: 2009-09-04
forum: x86 64-bit Users
---

### Post by chet_fred on 2009-09-04
Hi I recently moved changed from SLED11 to Ubuntu Jaunty.  I installed the 64 bit version because I need access to lots of RAM for FPGA development tools that I use.  I had Yugma running on 64 bit SLED 11.  On SLED 11 I had to get rid of 64 bit firefox and install 32 bit firefox.  On Ubuntu Jaunty I have java plugins etc. working great with firefox 64 bit.  But Yugma refuses to connect to server.  I was thinking of trying to get rid of 64 bit firefox and install 32 bit firefox like I did on SLED 11.  I love Ubuntu and I refuse to go back to Suse.  Any one had success with Yugma on 64 bit Jaunty?  Thanks.

---

### Post by chet_fred on 2009-09-05
Well I have things fixed now so I thought I would share the solution.  I installed 32 bit firefox on Jaunty 64-bit by following the directions at:

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

Then I reinstalled Yugma and things are working great now.  As a bonus when I installed firefox I upgraded to version 3.5.2.  I have no problem running a 32 bit browser.  I really need the 64 bit horse power for running Xilinx FPGA tools that can blow right out of 4G of RAM when you are doing a place and route on a large part.

---

