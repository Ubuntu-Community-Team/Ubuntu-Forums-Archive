---
title: "I/O error on serial port"
date: 2006-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by costinc on 2006-11-20
Hello 


When I try to get informations about serial port I got following I/O errors :
[INDENT]
sudo setserial -v  /dev/ttyS0
Cannot get serial info: Input/output error

[FONT="Lucida Console"]
strace output 
[...............]
open("/dev/ttyS0", O_RDWR|O_NONBLOCK)   = 3
ioctl(3, TIOCGSERIAL, 0x7fff32109880)   = -1 EIO (Input/output error)
dup(2)                                  = 4
fcntl(4, F_GETFL)                       = 0x8002 (flags O_RDWR|O_LARGEFILE)
brk(0)                                  = 0x506000
brk(0x527000)                           = 0x527000
fstat(4, {st_dev=makedev(0, 11), st_ino=2, st_mode=S_IFCHR|0620, st_nlink=1, st_uid=1000, st_gid=5, st_blksize=1024, st_blocks=0, st_rdev=makedev(136, 0), st_atime=2006/11/20-18:49:20, st_mtime=2006/11/20-18:49:20, st_ctime=2006/11/20-16:25:33}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2b8f789bc000
lseek(4, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
write(4, "Cannot get serial info: Input/ou"..., 43Cannot get serial info: Input/output error
) = 43
close(4)                                = 0
munmap(0x2b8f789bc000, 4096)            = 0
close(3)                                = 0
exit_group(0)                           = ?

[/FONT]
[/INDENT]

dmesg | grep -i tty
```

[   27.875721] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.876255] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

```

lspci

```


00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


```

Mainboard Gigabyte GA-M55plus-S3g
Kernel :
```

Linux ubuntu64-610 2.6.18 #1 SMP PREEMPT Sun Nov 19 21:44:11 EET 2006 x86_64 GNU/Linux

```

---

