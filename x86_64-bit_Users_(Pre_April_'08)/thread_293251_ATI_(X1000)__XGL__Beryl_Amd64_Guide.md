---
title: "ATI (X1000) / XGL / Beryl /Amd64 Guide"
date: 2006-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Syirrus on 2006-11-04
First let me preface this by thanking the linux community for hard work and dedication. If you are like me, I have been trying to get XGL / Beryl to work on my x1900 since before Dapper with no success.  I comb through the threads and found some guides that explained and worked me through the process.  All links will be posted in order.

Step #1
Install AMD64 bit version of Edgy

Step #2
Once manually install your ATI driver (X1000 series & up)
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually")

Step #3
Once you confirm that you have hardware acceleration it is time to install XGL / Beryl (Make sure you use AMD64 repositories)
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL") 

That is it, you are done!!!

Also for all you crossfire users out there, I had to install Edgy with just  one X1900 and then one install with proper drivers I was able to add my second card without a problem.

I hope this helps someone out there
Syirrus

Tip: if XGL / Beryl doesn't seem smooth enough change the following setting in the "Beryl Settings Manager" > Animation Time step to "10"

---

