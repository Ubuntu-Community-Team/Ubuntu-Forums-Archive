---
title: "configure: error: --enable-application=APP is required (compiling firefox 1.5 64bit)"
date: 2006-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by 5ketcher on 2006-01-31
Hi Guys,

Am I the first guy that tries to run firefox 1.5 on an amd64? I'm surprised that I couldn't find any 64bit binary.

I tried to compile it from source, but I got this error:
*configure: error: --enable-application=APP is required*
Does anybody know how to fix this?

thx, Jan

---

### Post by slavik on 2006-02-01
can you do a ./configure --help and copy/paste the section that has that option (we're looking for the description of it)

---

### Post by Jason_25 on 2006-02-01
Read [this]("http://developer.mozilla.org/en/docs/Configuring_Build_Options") link.  You'll need to add a .mozconfig file with 
--enable-application=APP
in it.

---

### Post by 5ketcher on 2006-02-01
thx Jason, it worked :) 
now I do have an other porblem. make doesen't work. I get this message:

*/usr/bin/ld: deflate.o: relocation R_X86_64_PC32 against `memcpy@@GLIBC_2.2.5' can not be used when making a shared object; recompile with -fPIC*

how can I recompile with -fPIC? do you know the syntax?

thx, Jan

---

### Post by hasek on 2006-02-06
it is a well known bug on Gcc 4.XX on 64 bit machines,

please type this in the mozilla directory

root@satan:~/mozilla# ac_cv_visibility_pragma=no ./configure --enable-application=browser

it should compile any versions of firefox:KS

---

### Post by hasek on 2006-02-09
for any persons still having problems for compiling firefox 1.5.0.1 on amd64 ubuntu, i have provided a ubuntu debian amd64 package for easy installation

you can download it at

[http://s1m0ne.free.fr/firefox_1.5.0.1-1_amd64.deb](http://s1m0ne.free.fr/firefox_1.5.0.1-1_amd64.deb)

to install it do

sudo dpkg -i firefox_1.5.0.1-1_amd64.deb

---

### Post by trigg on 2006-02-09
[QUOTE=hasek]it is a well known bug on Gcc 4.XX on 64 bit machines,

please type this in the mozilla directory

root@satan:~/mozilla# ac_cv_visibility_pragma=no ./configure --enable-application=browser

it should compile any versions of firefox:KS[/QUOTE]


You can also just add the ac_cv_visibility_pragma=no to your ~/.mozconfig file and then compile the package according to the [instructions on the mozilla.org website.]("http://developer.mozilla.org/en/docs/Build_and_Install") 



```

$ make -f client.mk build
$ sudo checkinstall make install

``` 

and you have a debian package you can install and un-install via dpkg and apt-get!

---

### Post by hasek on 2006-02-10
then after installing my deb package upper in this forum, you may want a full working amd64 java runtime environment (jre) plugin for firefox 1.5.0.1. 

it is still not exists yet but Blackdown Java-Linux Team has created a 100% working 64 bit jre for firefox 1.5+ Java Runtime Version 1.4.2-rc1

download it at [http://s1m0ne.free.fr/j2re-1.4.2-rc1-linux-amd64.bin](http://s1m0ne.free.fr/j2re-1.4.2-rc1-linux-amd64.bin)

easy installation amd64 firefox plugin 5 minutes

create a java directory in /usr/ by doing "mkdir java" if not existing
put the jre file in this /usr/java directory
execute it by ./j2re-1.4.2-rc1-linux-amd64.bin (if not executable do "chmod 755  j2re-1.4.2-rc1-linux-amd64.bin" and then execute it again)

you see know the program installing bla bla lbla.....

you should see now unpacked jre directory in /usr/java

after we should locate the firefox mozilla plugin in this package


root@satan:/usr/java# ls
j2re1.4.2  j2re-1.4.2-rc1-linux-amd64.bin

root@satan:/usr/java# locate libjavaplugin
/usr/java/j2re1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so

the firefox 64 bit plugin is here

/usr/java/j2re1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so

then we go in the firefox-1.5.0.1 plugin directory

root@satan:/usr/java# cd /usr/local/lib/firefox-1.5.0.1/plugins

root@satan:/usr/local/lib/firefox-1.5.0.1/plugins# ls
libnullplugin.so  libunixprintplugin.so

we create a link to the plugin we installed in /usr/java by doing this

root@satan:/usr/local/lib/firefox-1.5.0.1/plugins# ln -s /usr/java/j2re1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so ./

root@satan:/usr/local/lib/firefox-1.5.0.1/plugins# ls
libjavaplugin_oji.so  libnullplugin.so  libunixprintplugin.so

restart Firefox , you have now a full 64 bit (non-sucking 32 bit jre in emulation mode) java plugin for your 64 bit firefox

to check if plugin is correctly installed type in the url firefox bar, about:plugins

---

### Post by hasek on 2006-02-10
[QUOTE=hasek]for any persons still having problems for compiling firefox 1.5.0.1 on amd64 ubuntu, i have provided a ubuntu debian amd64 package for easy installation

you can download it at

[http://s1m0ne.free.fr/firefox_1.5.0.1-1_amd64.deb](http://s1m0ne.free.fr/firefox_1.5.0.1-1_amd64.deb)

to install it do

sudo dpkg -i firefox_1.5.0.1-1_amd64.deb[/QUOTE]
then after installing my deb package upper in this forum, you may want a full working amd64 java runtime environment (jre) plugin for firefox 1.5.0.1. 

it is still not exists yet but Blackdown Java-Linux Team has created a 100% working 64 bit jre for firefox 1.5+ Java Runtime Version 1.4.2-rc1

download it at [http://s1m0ne.free.fr/j2re-1.4.2-rc1-linux-amd64.bin](http://s1m0ne.free.fr/j2re-1.4.2-rc1-linux-amd64.bin)

easy installation amd64 firefox plugin 5 minutes

create a java directory in /usr/ by doing "mkdir java" if not existing
put the jre file in this /usr/java directory
execute it by ./j2re-1.4.2-rc1-linux-amd64.bin (if not executable do "chmod 755  j2re-1.4.2-rc1-linux-amd64.bin" and then execute it again)

you see know the program installing bla bla lbla.....

you should see now unpacked jre directory in /usr/java

after we should locate the firefox mozilla plugin in this package


root@satan:/usr/java# ls
j2re1.4.2  j2re-1.4.2-rc1-linux-amd64.bin

root@satan:/usr/java# locate libjavaplugin
/usr/java/j2re1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so

the firefox 64 bit plugin is here

/usr/java/j2re1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so

then we go in the firefox-1.5.0.1 plugin directory

root@satan:/usr/java# cd /usr/local/lib/firefox-1.5.0.1/plugins

root@satan:/usr/local/lib/firefox-1.5.0.1/plugins# ls
libnullplugin.so  libunixprintplugin.so

we create a link to the plugin we installed in /usr/java by doing this

root@satan:/usr/local/lib/firefox-1.5.0.1/plugins# ln -s /usr/java/j2re1.4.2/plugin/amd64/mozilla/libjavaplugin_oji.so ./

root@satan:/usr/local/lib/firefox-1.5.0.1/plugins# ls
libjavaplugin_oji.so  libnullplugin.so  libunixprintplugin.so

restart Firefox , you have now a full 64 bit (non-sucking 32 bit jre in emulation mode) java plugin for your 64 bit firefox

to check if plugin is correctly installed type in the url firefox bar, about:plugins

---

