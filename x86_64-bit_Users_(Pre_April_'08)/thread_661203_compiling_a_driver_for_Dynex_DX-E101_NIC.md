---
title: "compiling a driver for Dynex DX-E101 NIC"
date: 2008-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by btthompson on 2008-01-07
I'm having a bit of a problem building a driver for my new NIC. The make utility keeps failing because I don't have all the header files I need. Based on some other posts, I have tried running 'apt-get install build-essential' but that did not help. I was going to install 'linux-headers-386' but I'm running with the AMD64bit kernel. I've made a symbolic link: /usr/src/linux -> linux-headers-2.6.22-14-generic thinking that would help but it didn't.

Any ideas on what to do? I've used Linux for a while but never had to do anything with drivers...

Below is the output of the commands I ran, the ls of the /usr/src/linux/include/linux/ directory and a copy of the makefile for the driver.

-----------build-essential install output----------------

root@Tucker:~/Desktop/5.03# apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed:
build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7416kB of archives.
After unpacking 31.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package linux-libc-dev.
(Reading database ... 88046 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.46_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu9_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_amd64.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-16ubuntu2_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-9ubuntu2_amd64.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch/patch_2.5.9-4_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.5ubuntu16_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_amd64.deb) ...
Setting up linux-libc-dev (2.6.22-14.46) ...
Setting up libc6-dev (2.6.1-1ubuntu9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.5ubuntu16) ...
Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

Setting up build-essential (11.3ubuntu1) ...

----------'make' results-----------------

root@Tucker:~/Desktop/5.03# make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/brian/Desktop/5.03 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
CC [M] /home/brian/Desktop/5.03/rhine_main.o
In file included from /home/brian/Desktop/5.03/rhine_main.c:28:
/home/brian/Desktop/5.03/rhine.h:56:26: error: linux/config.h: No such file or directory
/home/brian/Desktop/5.03/rhine_main.c:59: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:64: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:73: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:85: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:100: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:115: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:122: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:131: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:139: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:148: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:159: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:175: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:182: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:194: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c:200: error: expected â€˜)â€™ before string constant
/home/brian/Desktop/5.03/rhine_main.c: In function â€˜rhine_receive_frameâ€™:
/home/brian/Desktop/5.03/rhine_main.c:1214: error: â€˜struct sk_buffâ€™ has no member named â€˜macâ€™
/home/brian/Desktop/5.03/rhine_main.c:1214: error: â€˜struct sk_buffâ€™ has no member named â€˜macâ€™
/home/brian/Desktop/5.03/rhine_main.c:1214: error: â€˜struct sk_buffâ€™ has no member named â€˜macâ€™
/home/brian/Desktop/5.03/rhine_main.c:1214: error: â€˜struct sk_buffâ€™ has no member named â€˜macâ€™
/home/brian/Desktop/5.03/rhine_main.c: In function â€˜rhine_alloc_rx_bufâ€™:
/home/brian/Desktop/5.03/rhine_main.c:1260: warning: passing argument 2 of â€˜pci_map_singleâ€™ makes pointer from integer without a cast
/home/brian/Desktop/5.03/rhine_main.c: In function â€˜rhine_openâ€™:
/home/brian/Desktop/5.03/rhine_main.c:1572: warning: â€˜deprecated_irq_flagâ€™ is deprecated (declared at include/linux/interrupt.h:66)
/home/brian/Desktop/5.03/rhine_main.c:1572: warning: passing argument 2 of â€˜request_irqâ€™ from incompatible pointer type
/home/brian/Desktop/5.03/rhine_main.c: In function â€˜rhine_xmitâ€™:
/home/brian/Desktop/5.03/rhine_main.c:1716: error: â€˜CHECKSUM_HWâ€™ undeclared (first use in this function)
/home/brian/Desktop/5.03/rhine_main.c:1716: error: (Each undeclared identifier is reported only once
/home/brian/Desktop/5.03/rhine_main.c:1716: error: for each function it appears in.)
/home/brian/Desktop/5.03/rhine_main.c:1717: error: â€˜struct sk_buffâ€™ has no member named â€˜nhâ€™
/home/brian/Desktop/5.03/rhine_main.c: At top level:
/home/brian/Desktop/5.03/rhine_main.c:1926: warning: initialization from incompatible pointer type
/home/brian/Desktop/5.03/rhine_main.c: In function â€˜rhine_init_moduleâ€™:
/home/brian/Desktop/5.03/rhine_main.c:1935: warning: implicit declaration of function â€˜pci_module_initâ€™
/home/brian/Desktop/5.03/rhine_main.c: In function â€˜rhine_ethtool_ioctlâ€™:
/home/brian/Desktop/5.03/rhine_main.c:2086: error: â€˜struct pci_devâ€™ has no member named â€˜slot_nameâ€™
make[2]: *** [/home/brian/Desktop/5.03/rhine_main.o] Error 1
make[1]: *** [_module_/home/brian/Desktop/5.03] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
root@Tucker:~/Desktop/5.03#

-------include/linux dir--------------------

root@Tucker:~/Desktop/5.03# ls /usr/src/linux/include/linux/
8250_pci.h cyclades.h hw_random.h lapb.h percpu_counter.h sonypi.h
ac97_codec.h cyclomx.h hysdn_if.h latency.h percpu.h sort.h
acct.h cycx_cfm.h i2c-algo-bit.h lcd.h personality.h soundcard.h
acpi.h cycx_drv.h i2c-algo-pca.h leds.h pfkeyv2.h sound.h
acpi_pmtmr.h cycx_x25.h i2c-algo-pcf.h libata.h pfn.h spi
adb.h dcache.h i2c-algo-sgi.h libps2.h pg.h spinlock_api_smp.h
adfs_fs.h dccp.h i2c-dev.h license.h phantom.h spinlock_api_up.h
adfs_fs_i.h dcookies.h i2c-gpio.h limits.h phonedev.h spinlock.h
adfs_fs_sb.h debugfs.h i2c.h linkage.h phy.h spinlock_types.h
aer.h debug_locks.h i2c-id.h linux pid.h spinlock_types_up.h
affs_hardblocks.h delayacct.h i2c-isa.h linux_logo.h pid_namespace.h spinlock_up.h
agp_backend.h delay.h i2c-ocores.h list.h pipe_fs_i.h srcu.h
agpgart.h device.h i2c-pnx.h llc.h pktcdvd.h stacktrace.h
aio_abi.h device-mapper.h i2c-pxa.h lm_interface.h pkt_cls.h stallion.h
aio.h devpts_fs.h i2o-dev.h lockd pkt_sched.h start_kernel.h
amba dio.h i2o.h lockdep.h platform_device.h statfs.h
amifd.h dirent.h i8k.h lock_dlm_plock.h plist.h stat.h
amifdreg.h display.h ibmtr.h log2.h pm.h stddef.h
amigaffs.h dlm_device.h icmp.h loop.h pm_legacy.h stop_machine.h
anon_inodes.h dlm.h icmpv6.h lp.h pmu.h string.h
a.out.h dlm_netlink.h ide.h m41t00.h pnpbios.h stringify.h
apm_bios.h dm9000.h idr.h m48t86.h pnp.h sunrpc
apm-emulation.h dmaengine.h ieee80211.h magic.h poison.h superhyway.h
arcdevice.h dma-mapping.h if_addr.h major.h poll.h suspend.h
arcfb.h dmapool.h if_arcnet.h matroxfb.h posix_acl.h svga.h
ata.h dmi.h if_arp.h mbcache.h posix_acl_xattr.h swap.h
atalk.h dm-ioctl.h if_bonding.h mc146818rtc.h posix-timers.h swapops.h
atmapi.h dn.h if_bridge.h mc6821.h posix_types.h synclink.h
atmarp.h dnotify.h if_cablemodem.h mca.h ppdev.h syscalls.h
atmbr2684.h dqblk_v1.h if_ec.h mca-legacy.h ppp_channel.h sysctl.h
atmclip.h dqblk_v2.h if_eql.h memory.h ppp-comp.h sysdev.h
atmdev.h dqblk_xfs.h if_ether.h memory_hotplug.h ppp_defs.h sysfs.h
atmel_pdc.h ds1286.h if_fc.h mempolicy.h prctl.h sys.h
atm_eni.h ds17287rtc.h if_fddi.h mempool.h preempt.h sysrq.h
atm.h ds1wm.h if_frad.h meye.h prefetch.h sysv_fs.h
atm_he.h dtlk.h if.h migrate.h prio_tree.h task_io_accounting.h
atm_idt77105.h dvb if_hippi.h mii.h proc_fs.h task_io_accounting_ops.h
atmioc.h edd.h if_infiniband.h minix_fs.h profile.h taskstats.h
atmlec.h efi.h if_link.h miscdevice.h ps2esdi.h taskstats_kern.h
atmmpc.h efs_dir.h if_ltalk.h mlx4 ptrace.h tc_act
atm_nicstar.h efs_fs.h if_packet.h mman.h qnx4_fs.h tc_ematch
atmppp.h efs_fs_i.h if_plip.h mmc qnxtypes.h tc.h
atmsap.h efs_fs_sb.h if_ppp.h mm.h quicklist.h tcp.h
atm_suni.h efs_vh.h if_pppox.h mm_inline.h quota.h telephony.h
atmsvc.h eisa.h if_shaper.h mmtimer.h quotaio_v1.h termios.h
atm_tcp.h elevator.h if_slip.h mm_types.h quotaio_v2.h textsearch_fsm.h
atm_zatm.h elfcore.h if_strip.h mmzone.h quotaops.h textsearch.h
attribute_container.h elf-em.h if_tr.h mnt_namespace.h radeonfb.h tfrc.h
audit.h elf-fdpic.h if_tun.h mod_devicetable.h radix-tree.h thread_info.h
autoconf.h elf.h if_tunnel.h module.h raid threads.h
auto_fs4.h elfnote.h if_vlan.h moduleloader.h raid_class.h ticable.h
auto_fs.h err.h if_wanpipe.h moduleparam.h ramfs.h tick.h
auxvec.h errno.h igmp.h mount.h random.h tifm.h
ax25.h errqueue.h in6.h mpage.h raw.h time.h
b1lli.h etherdevice.h inetdevice.h mqueue.h rbtree.h timerfd.h
b1pcmcia.h ethtool.h inet_diag.h mroute.h rcupdate.h timer.h
backing-dev.h eventfd.h inet.h msdos_fs.h reboot.h times.h
backlight.h eventpoll.h in.h msg.h reciprocal_div.h timex.h
baycom.h ext2_fs.h init.h msi.h reiserfs_acl.h tiocl.h
bcd.h ext2_fs_sb.h initrd.h mtd reiserfs_fs.h tipc_config.h
bfs_fs.h ext3_fs.h init_task.h mtio.h reiserfs_fs_i.h tipc.h
binfmts.h ext3_fs_i.h inotify.h mutex-debug.h reiserfs_fs_sb.h topology.h
bio.h ext3_fs_sb.h input.h mutex.h reiserfs_xattr.h toshiba.h
bitmap.h ext3_jbd.h input-polldev.h mv643xx.h relay.h transport_class.h
bitops.h ext4_fs_extents.h in_route.h namei.h resource.h trdevice.h
bitrev.h ext4_fs.h interrupt.h nbd.h resume-trace.h tsacct_kern.h
bit_spinlock.h ext4_fs_i.h ioc3.h ncp_fs.h rfkill.h tty_driver.h
blkdev.h ext4_fs_sb.h ioc4.h ncp_fs_i.h rio_drv.h tty_flip.h
blkpg.h ext4_jbd2.h ioctl.h ncp_fs_sb.h rio.h tty.h
blktrace_api.h fadvise.h io.h ncp.h rio_ids.h tty_ldisc.h
blockgroup_lock.h fault-inject.h ioport.h ncp_mount.h rio_regs.h types.h
bootmem.h fb.h ioprio.h ncp_no.h rmap.h uaccess.h
bottom_half.h fcdevice.h ip6_tunnel.h neighbour.h romfs_fs.h udf_fs.h
bpqether.h fcntl.h ipc.h netdevice.h root_dev.h udf_fs_i.h
buffer_head.h fd1772.h ip.h netfilter rose.h udf_fs_sb.h
bug.h fddidevice.h ipmi.h netfilter_arp route.h udp.h
byteorder fd.h ipmi_msgdefs.h netfilter_arp.h rslib.h ufs_fs.h
cache.h fdreg.h ipmi_smi.h netfilter_bridge rtc.h ufs_fs_i.h
calc64.h fib_rules.h ip_mp_alg.h netfilter_bridge.h rtc-v3020.h ufs_fs_sb.h
capability.h file.h ipsec.h netfilter_decnet.h rtmutex.h uinput.h
capi.h filter.h ipv6.h netfilter.h rtnetlink.h uio.h
cciss_ioctl.h firewire-cdev.h ipv6_route.h netfilter_ipv4 rwsem.h ultrasound.h
cd1400.h firewire-constants.h ipx.h netfilter_ipv4.h rwsem-spinlock.h umem.h
cdev.h firmware.h irda.h netfilter_ipv6 rxrpc.h un.h
cdk.h flat.h irq_cpustat.h netfilter_ipv6.h sc26198.h union_fs.h
cdrom.h font.h irqflags.h net.h scatterlist.h unistd.h
cfag12864b.h freezer.h irq.h netlink.h scc.h unwind.h
chio.h fs_enet_pd.h irqreturn.h netpoll.h sched.h usb
circ_buf.h fs.h isa.h netrom.h screen_info.h usbdevice_fs.h
clk.h fsl_devices.h isapnp.h nfs2.h sctp.h usb_gadgetfs.h
clockchips.h fsnotify.h isdn nfs3.h scx200_gpio.h usb_gadget.h
clocksource.h fs_stack.h isdn_divertif.h nfs4_acl.h scx200.h usb.h
cm4000_cs.h fs_struct.h isdn.h nfs4.h sdla.h usb_sl811.h
cn_proc.h fs_uart_pd.h isdnif.h nfs4_mount.h seccomp.h usb_usual.h
cobalt-nvram.h fuse.h isdn_ppp.h nfsacl.h securebits.h user.h
coda_cache.h futex.h isicom.h nfsd security.h utime.h
coda_fs_i.h gameport.h iso_fs.h nfsd_idmap.h selection.h uts.h
coda.h genalloc.h istallion.h nfs_fs.h selinux.h utsname.h
coda_linux.h generic_acl.h ixjuser.h nfs_fs_i.h selinux_netlink.h utsrelease.h
coda_proc.h generic_serial.h jbd2.h nfs_fs_sb.h sem.h vermagic.h
coda_psdev.h genetlink.h jbd.h nfs.h seq_file.h version.h
coff.h genhd.h jffs2.h nfs_idmap.h seqlock.h vfs.h
com20020.h gen_stats.h jhash.h nfs_mount.h serial167.h via.h
compat.h getcpu.h jiffies.h nfs_page.h serial_8250.h video_decoder.h
compiler-gcc3.h gfp.h journal-head.h nfs_xdr.h serial_core.h videodev2.h
compiler-gcc4.h gfs2_ondisk.h joystick.h nl80211.h serial.h videodev.h
compiler-gcc.h gigaset_dev.h kallsyms.h nls.h serialP.h video_encoder.h
compiler.h gpio_keys.h kbd_diacr.h nmi.h serial_pnx8xxx.h video_output.h
compiler-intel.h hardirq.h kbd_kern.h node.h serial_reg.h videotext.h
completion.h harrier_defs.h Kbuild nodemask.h serio.h vmalloc.h
comstats.h hash.h kdebug.h notifier.h shmem_fs.h vmstat.h
concap.h hayesesp.h kdev_t.h n_r3964.h shm.h vt_buffer.h
configfs.h hdlc kd.h nsc_gpio.h signalfd.h vt.h
connector.h hdlcdrv.h kernelcapi.h nsproxy.h signal.h vt_kern.h
console.h hdlc.h kernel.h nubus.h skbuff.h wait.h
consolemap.h hdpu_features.h kernel_stat.h numa.h slab_def.h wanrouter.h
console_struct.h hdreg.h kexec.h nvram.h slab.h watchdog.h
const.h hdsmart.h keyboard.h oom.h slub_def.h wireless.h
cpufreq.h hid-debug.h keyctl.h oprofile.h sm501.h workqueue.h
cpu.h hiddev.h key.h page-flags.h sm501-regs.h writeback.h
cpumask.h hid.h key-ui.h pagemap.h smb_fs.h x25.h
cpuset.h highmem.h kfifo.h pagevec.h smb_fs_i.h xattr.h
cramfs_fs.h highuid.h klist.h param.h smb_fs_sb.h xfrm.h
cramfs_fs_sb.h hil.h kmalloc_sizes.h parport.h smb.h yam.h
crash_dump.h hil_mlc.h kmod.h parport_pc.h smb_mount.h zconf.h
crc16.h hippidevice.h kobject.h parser.h smbno.h zlib.h
crc32c.h hpet.h kobj_map.h pata_platform.h smp.h zorro.h
crc32.h hp_sdc.h kprobes.h patchkey.h smp_lock.h zorro_ids.h
crc-ccitt.h hrtimer.h kref.h pci-acpi.h snmp.h zutil.h
crc-itu-t.h htirq.h ks0108.h pcieport_if.h socket.h
crypto.h hugetlb.h kthread.h pci.h sockios.h
cryptohash.h hwmon.h ktime.h pci_hotplug.h som.h
ctype.h hwmon-sysfs.h kvm.h pci_ids.h sonet.h
cuda.h hwmon-vid.h kvm_para.h pci_regs.h sony-laptop.h
root@Tucker:~/Desktop/5.03#

--------MAKEFILE-------

DEBUG = 0

KSP := /lib/modules/$(shell uname -r)/build \
/usr/src/linux-$(shell uname -r) \
/usr/src/linux-$(shell uname -r | sed 's/-.*//') \
/usr/src/kernel-headers-$(shell uname -r) \
/usr/src/kernel-source-$(shell uname -r) \
/usr/src/linux-$(shell uname -r | sed 's/\([0-9]*\.[0-9]*\)\..*/\1/') \
/usr/src/linux

test_dir = $(shell [ -e $(dir)/include/linux ] && echo $(dir))
KSP := $(foreach dir, $(KSP), $(test_dir))

KSRC := $(firstword $(KSP))
ifeq (,$(KSRC))
$(error Linux kernel source not found)
endif

# check kernel version
KVER := $(shell uname -r | cut -c1-3 | sed 's/2\.[56]/2\.6/')
KERVER2=$(shell uname -r | cut -d. -f2)

ifeq ($(KVER), 2.6)
# 2.6 kernel
TARGET = rhinefet.ko
BUILTIN = via-rhine.ko
else
TARGET = rhinefet.o
BUILTIN = via-rhine.o
endif

INSTDIR := $(shell find /lib/modules/$(shell uname -r) -name $(TARGET) -printf "%h\n" | sort | head -1)
ifeq (,$(INSTDIR))
ifeq (,$(KERVER2))
ifneq (,$(wildcard /lib/modules/$(shell uname -r)/kernel))
INSTDIR := /lib/modules/$(shell uname -r)/kernel/drivers/net
else
INSTDIR := /lib/modules/$(shell uname -r)/net
endif
else
ifneq ($(KERVER2),2)
INSTDIR := /lib/modules/$(shell uname -r)/kernel/drivers/net
else
INSTDIR := /lib/modules/$(shell uname -r)/net
endif
endif
endif

SRC = rhine_main.c rhine_proc.c rhine_wol.c rhine_hw.c

# build rule
ifeq ($(KVER), 2.6)
# 2.6 kernel

obj-m += rhinefet.o
rhinefet-objs := rhine_main.o rhine_proc.o rhine_wol.o rhine_hw.o

default:
make -C $(KSRC) SUBDIRS=$(shell pwd) modules

else
# 2.2/2.4 kernel

OBJS := rhine_main.o rhine_proc.o rhine_wol.o rhine_hw.o

VERSION_FILE := $(KSRC)/include/linux/version.h
CONFIG_FILE := $(KSRC)/include/linux/config.h

ifeq (,$(wildcard $(VERSION_FILE)))
$(error Linux kernel source not configured - missing version.h)
endif

ifeq (,$(wildcard $(CONFIG_FILE)))
$(error Linux kernel source not configured - missing config.h)
endif

ifneq (,$(findstring egcs-2.91.66, $(shell cat /proc/version)))
CC := kgcc gcc cc
else
CC := gcc cc
endif

test_cc = $(shell which $(cc) > /dev/null 2>&1 && echo $(cc))
CC := $(foreach cc, $(CC), $(test_cc))
CC := $(firstword $(CC))

CFLAGS += -Wall -DLINUX -D__KERNEL__ -DMODULE -DEXPORT_SYMTAB -D__NO_VERSION__ -O2 -pipe
CFLAGS += -I$(KSRC)/include -I. -Wstrict-prototypes -fomit-frame-pointer
CFLAGS += $(shell [ -f $(KSRC)/include/linux/modversions.h ] && \
echo "-DMODVERSIONS -include $(KSRC)/include/linux/modversions.h")

.SILENT: $(TARGET) clean

# look for SMP in config.h
SMP := $(shell $(CC) $(CFLAGS) -E -dM $(CONFIG_FILE) | \
grep CONFIG_SMP | awk '{ print $$3 }')

ifneq ($(SMP),1)
SMP := 0
endif

ifeq ($(DEBUG),1)
CFLAGS += -DRHINE_DBG
endif

ifeq ($(SMP), 1)
CFLAGS += -D__SMP__
endif

# check x86_64
SUBARCH := $(shell uname -m)
ifeq ($(SUBARCH),x86_64)
CFLAGS += -mcmodel=kernel -mno-red-zone
endif

$(TARGET): $(filter-out $(TARGET), $(SRC:.c=.o))
$(LD) -r $^ -o $@
echo; echo
echo "************************************************* *"
echo "Build options:"
echo " VERSION $(shell uname -r)"
echo -n " SMP "
if [ "$(SMP)" = "1" ]; \
then echo "Enabled"; else echo "Disabled"; fi
echo "************************************************* *"

endif # ifeq ($(KVER),2.6)

ifeq ($(KVER), 2.6)
install: default
else
install: clean $(TARGET)
endif
mkdir -p $(MOD_ROOT)$(INSTDIR)
install -m 644 -o root $(TARGET) $(MOD_ROOT)$(INSTDIR)
@if [ -f $(MOD_ROOT)$(INSTDIR)/$(BUILTIN) ] ; then \
echo "***** Move official driver $(BUILTIN) to $(BUILTIN).backup file" ; \
echo "mv $(MOD_ROOT)$(INSTDIR)/$(BUILTIN) $(MOD_ROOT)$(INSTDIR)/$(BUILTIN).backup";\
mv $(MOD_ROOT)$(INSTDIR)/$(BUILTIN) $(MOD_ROOT)$(INSTDIR)/$(BUILTIN).backup ; \
echo ;\
fi ;
@if [ -f $(MOD_ROOT)$(INSTDIR)/linuxfet.o ] ; then \
echo "***** Move previous driver linuxfet.o to linuxfet.o.backup" ; \
echo "mv $(MOD_ROOT)$(INSTDIR)/linuxfet.o $(MOD_ROOT)$(INSTDIR)/linuxfet.o.backup";\
mv $(MOD_ROOT)$(INSTDIR)/linuxfet.o $(MOD_ROOT)$(INSTDIR)/linuxfet.o.backup ; \
echo ;\
fi ;

ifeq (,$(MOD_ROOT))
/sbin/depmod -a || true
else
/sbin/depmod -b $(MOD_ROOT) -a || true
endif

uninstall:
rm -f $(INSTDIR)/$(TARGET)
@if [ -f $(MOD_ROOT)$(INSTDIR)/$(BUILTIN).backup ] ; then \
echo "***** Restore official driver $(BUILTIN) from $(MOD_ROOT)$(INSTDIR)".; \
echo "mv $(MOD_ROOT)$(INSTDIR)/$(BUILTIN).backup $(MOD_ROOT)$(INSTDIR)/$(BUILTIN)";\
mv $(MOD_ROOT)$(INSTDIR)/$(BUILTIN).backup $(MOD_ROOT)$(INSTDIR)/$(BUILTIN) ;\
fi
/sbin/depmod -a

clean:
rm -f $(SRC:.c=.o) rhinefet.o rhinefet.ko rhinefet.mod.c rhinefet.mod.o *~
__________________

---

### Post by Kilz on 2008-01-07
Try ```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by btthompson on 2008-01-08
I get:

linux-headers-2.6.22-14-generic is already the newest version

---

