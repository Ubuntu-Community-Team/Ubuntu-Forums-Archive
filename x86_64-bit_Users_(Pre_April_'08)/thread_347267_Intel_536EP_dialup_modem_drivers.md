---
title: "Intel 536EP dialup modem drivers?"
date: 2007-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by teamr on 2007-01-27
Hi Guy's, asking for any help avail for my dialup problem. I am onto my second modem, first was a Smartlink machine and this is a new Intel 536EP.

System is a amd64 Sempron running dual boot with my old Win 98se.

Have followed the thread by chuckman 78 but can't get the driver to compile.

Following is the text. Sorry if it is a bit long.

root@bigtoot:/home/garry/Desktop/Intel-536# make clean
cd coredrv; make clean
make[1]: Entering directory `/home/garry/Desktop/Intel-536/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/garry/Desktop/Intel-536/coredrv'
rm -f *.o *.ko
root@bigtoot:/home/garry/Desktop/Intel-536# make 536
   Module precompile check
   Current running kernel is: 2.6.15-23-amd64-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
        cd coredrv && make 536core_26 && \
        cp Intel536.ko .. && cd .. && \
        strip --strip-debug Intel536.ko && \
        exit; \
        ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed  to build driver" && exit; \
        if [  ]; then \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTAR GET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        else \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname  -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
        cp Intel536.o .. ; \
        if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/v ersion.h;\
        fi
2.6.15-23-amd64-generic
make[1]: Entering directory `/home/garry/Desktop/Intel-536/coredrv'
make -C /lib/modules/2.6.15-23-amd64-generic/build SUBDIRS=/home/garry/Desktop/I ntel-536/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-23-amd64-generic'
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/coredrv.o
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:73: warning: type defaults to â€˜i ntâ€™ in declaration of â€˜EXPORT_SYMBOL_NOVERSâ€™
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:73: warning: parameter names (wi thout types) in function declaration
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:73: warning: data definition has  no type or storage class
/home/garry/Desktop/Intel-536/coredrv/coredrv.c: In function â€˜closeâ€™:
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:439: warning: implicit declarati on of function â€˜pm_unregisterâ€™
/home/garry/Desktop/Intel-536/coredrv/coredrv.c: At top level:
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:880: warning: initialization mak es integer from pointer without a cast
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:289: warning: â€˜power_callbackâ€™ d efined but not used
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/clmmain.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/rts.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/task.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/uart.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/wwh_dflt.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/locks.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/softserial_io.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/softserial_ioctl.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/softserial.o
  LD [M]  /home/garry/Desktop/Intel-536/coredrv/Intel536.o
ld: Relocatable linking with relocations from format elf32-i386 (/home/garry/Des ktop/Intel-536/coredrv/536core.lib) to format elf64-x86-64 (/home/garry/Desktop/ Intel-536/coredrv/Intel536.o) is not supported
make[3]: *** [/home/garry/Desktop/Intel-536/coredrv/Intel536.o] Error 1
make[2]: *** [_module_/home/garry/Desktop/Intel-536/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-23-amd64-generic'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/garry/Desktop/Intel-536/coredrv'
2.6.15-23-amd64-generic
Failed to build driver
root@bigtoot:/home/garry/Desktop/Intel-536# make clean

I replace the i386 with amd64 and the 537 with 536 as you can see.

If I can get this going I will be able to finaly dump win98.

Thanks in advance.

teamr.

---

### Post by scunc_dvl on 2007-02-17
It won't compile in 64-bit mode, it will always yield linker errors. There is no 64-bit drivers, and sadly Intel probably won't make more.

I'd like to see someone make this modem work in 64-bit somehow, either using existing Alsa stuff, *( [https://help.ubuntu.com/community/DialupModemHowto/Smartlink](https://help.ubuntu.com/community/DialupModemHowto/Smartlink) , it's unclear whether this can actually work or not because it's supposed to work for the Intel 537)* 

Another way more in the direction you were going would be to try and force the 64-bit kernel to use the 32-bit driver, something I would like to see because Windows can't do it ;)

---

### Post by Matchless on 2007-02-17
Hi,
   This works on Edgy, but I have never tried it on 64-bit.
                                           ** [B]_[COLOR=#000000][SIZE=3]Mode[/SIZE][SIZE=2][FONT=Arial, sans-serif]ms supported by the Intel536EP driver for Ubuntu Edgy Eft[/FONT][/SIZE][/COLOR]_**[/B]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]This page describes how to install the driver for the Intel 536EP internal modem on Ubuntu Edgy for i386 systems. Some of these are sold as Cnet modems and have Ambient chips on board. The process below is quick easy and works quite well. For other older ubuntu versions before Dapper you will additionally require gcc 3.4 to also be installed. [/SIZE][/FONT][/COLOR] 
 [B] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][B]
Install required Ubuntu packages[/B][/SIZE][/FONT][/COLOR][/B]
[SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]In a terminal type [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]uname -r[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000], which should give you your kernel version ARCH[/COLOR][/FONT][/SIZE]
 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]You will need to install the [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]build-essential[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000] and [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]linux-headers-ARCH[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000] packages. They are normally on the install CD and can most easily be installed with Synaptic or downloaded if your PC is on a connected lan.[/COLOR][/FONT][/SIZE]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Download the latest drivers for the modem here: [/SIZE][/FONT][/COLOR] 
 [COLOR=#000080]_[[SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-536EP-2.56.76.0_21_09_2006.tgz[/COLOR][/FONT][/SIZE]]("http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-536EP-2.56.76.0_21_09_2006.tgz")_[/COLOR] 
 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Save the file, which is named i[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]ntel-536EP-2.56.76.0_21_09_2006.tgz[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000] on your Desktop. [/COLOR][/FONT][/SIZE] 
 ** [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][B]Compiling the driver**[/SIZE][/FONT][/COLOR][/B]

 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Right click on the file and select &#8220;Extract to here&#8221; 
This will create directory [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]intel-536EP-2.56.76.0[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]  on your Desktop. 
Open a terminal window and type: [/COLOR][/FONT][/SIZE] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]cd Desktop/intel-536EP-2.56.76.0[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]make clean[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
This should produce output looking like this: [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]make[1]: Entering directory `/home/<usename>/Desktop/intel-536EP-2.56.76.0/coredrv'[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]rm -f *.ko .*.o.cmd *.mod.c .*.ko.cmd *.o *~ core Modules.symvers[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]rm -rf .tmp_versions[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
make[1]: Leaving directory `/home/<username>/Desktop/intel-536EP-2.56.76.0/coredrv'[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]rm -f *.o *.ko[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]make 536[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
This will result in many lines of output, the final lines should look like this: [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000]   [SIZE=2][FONT=Arial, sans-serif]CC      /home/<username>/Desktop/intel-536EP-2.56.76.0/coredrv/Intel536.mod.o[/FONT][/SIZE][/COLOR] [COLOR=#000000]  [SIZE=2][FONT=Arial, sans-serif]LD [M]  /home/<username>/Desktop/intel-536EP-2.56.76.0/coredrv/Intel536.ko[/FONT][/SIZE][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]make[1]: Leaving directory `/home/<username>/Desktop/intel-536EP-2.56.76.0/coredrv'[/SIZE][/FONT][/COLOR]  [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]
There should be an [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Intel536.ko[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000] file in the directory now; test this by typing[/COLOR][/FONT][/SIZE]
 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]ls -l Intel536.ko [/COLOR][/FONT][/SIZE] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]The output should look like:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000] [SIZE=2][FONT=Arial, sans-serif]--rw-r--r-- 1 <username> <username> 1099788 2006-11-13 19:50 Intel536.ko[/FONT][/SIZE][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][B]
Installing the driver[/B][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]There are two steps to installing the driver. The first is to copy the Intel536.ko file created above to an appropriate directory, and the second is to cause the driver to be loaded at boot time. [/SIZE][/FONT][/COLOR] 
 *[SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]To install the Intel536.ko file, c[/COLOR][/FONT][/SIZE]*[SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]opy the file to the modules directory with this command: [/COLOR][/FONT][/SIZE] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo cp Intel536.ko /lib/modules/$(uname -r)/kernel/drivers/char[/SIZE][/FONT][/COLOR] 
[SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Make your system aware of this module with [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]depmod[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]: [/COLOR][/FONT][/SIZE] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo depmod -a[/SIZE][/FONT][/COLOR] [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]
Finally, load the driver with the [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]modprobe[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000] command: [/COLOR][/FONT][/SIZE] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo modprobe Intel536[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
This command should not print a response; if it prints something like this: [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000] [SIZE=2][FONT=Arial, sans-serif]FATAL: Module Intel536 not found.[/FONT][/SIZE][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You have made an error; most likely you have copied the file to the wrong place. If you see a different error message, there may be an error in the module, or your modem, or you may not have a Intel 536-based modem. [/SIZE][/FONT][/COLOR] 
 *[SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Loading the driver at boot time[/COLOR][/FONT][/SIZE]* 
 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]To load the module at boot time, we need to add a line "[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]Intel536[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]" to the file /etc/modules. Right click on the file, actions, Edit as Root and enter a line at the end:[/COLOR][/FONT][/SIZE]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Intel536[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**Using the modem**[/SIZE][/FONT][/COLOR]
 [SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]The name of your modem device is [/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]/dev/536ep0[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial, sans-serif][COLOR=#000000]. To use Kppp you will need to create a symlink be able to link the /dev/536ep0 to /dev/modem. Udev rewrites the /dev on each reboot and you thus have to create a new line with kwrite, kate or gedit in /etc/udev/rules.d/60-symlink.rules and find the following lines and put the last line in it: [/COLOR][/FONT][/SIZE] 
 [COLOR=#000000] [SIZE=2][FONT=Arial, sans-serif]    # Create /dev/modem symlink[/FONT][/SIZE][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]KERNEL=="ttyLTM[0-9]*",            SYMLINK+="modem"[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
KERNEL=="536ep0",                SYMLINK+="modem"[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
Now reboot and you can use Kppp to query the modem as this is a quick check if all is well before dialling out. Configure Kppp or Gnome-ppp for your ISP connection. These Intel modems are found to be quite stable.[/SIZE][/FONT][/COLOR]

---

