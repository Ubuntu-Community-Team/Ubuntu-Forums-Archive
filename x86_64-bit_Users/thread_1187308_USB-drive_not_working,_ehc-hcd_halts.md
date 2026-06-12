---
title: "USB-drive not working, ehc-hcd halts"
date: 2009-06-14
forum: x86 64-bit Users
---

### Post by ali.b on 2009-06-14
I have a usb-drive that, until recently (when I upgraded from gutsy to jaunty), worked perfectly and it still works under the windows install. However, it no longer works in kubuntu. At first, it wasn't detected at all. Checking dmesg I saw: ```
[  113.647433] ehci_hcd 0000:00:13.5: force halt; handhake ffffc20000064824 00004000 00004000 -> -110
``` This happened if the drive was disconnected as well. Some quick research later and I found someone advicing to add acpi=noirq as boot parameter to the kernel. That seemed to work at first, ehci didn't halt during boot and the usb-drive appeared as /dev/sdb.

Unfortunately, that was not the end of it. When I tried to access the drive (mount it), ehci halted. dmesg had this to say:
```

[  101.240085] usb 1-1: new high speed USB device using ehci_hcd and address 6  
[  101.518824] usb 1-1: configuration #1 chosen from 1 choice                  
[  101.608739] Initializing USB Mass Storage driver...                          
[  101.639660] input: Western Digital My Book as /devices/pci0000:00/0000:00:13.5/usb1/1-1/1-1:1.1/input/input11                                                
[  101.653290] generic-usb 0003:1058:1102.0002: input,hidraw1: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:13.5-1/input1                      
[  101.696204] scsi7 : SCSI emulation for USB Mass Storage devices              
[  101.696482] usbcore: registered new interface driver usb-storage            
[  101.696490] USB Mass Storage support registered.                            
[  101.696824] usb-storage: device found at 6                                  
[  101.696829] usb-storage: waiting for device to settle before scanning
[  106.699929] usb-storage: device scan complete                                
[  106.718323] scsi 7:0:0:0: Direct-Access     WD       My Book          1028 PQ: 0 ANSI: 4                                                                    
[  106.747702] sd 7:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)                                                                        
[  106.760702] sd 7:0:0:0: [sdb] Write Protect is off                          
[  106.760712] sd 7:0:0:0: [sdb] Mode Sense: 10 00 00 00                        
[  106.760718] sd 7:0:0:0: [sdb] Assuming drive cache: write through            
[  106.783366] sd 7:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)                                                                        
[  106.796835] sd 7:0:0:0: [sdb] Write Protect is off                          
[  106.796843] sd 7:0:0:0: [sdb] Mode Sense: 10 00 00 00                        
[  106.796849] sd 7:0:0:0: [sdb] Assuming drive cache: write through            
[  106.796862]  sdb: sdb1                                                      
[  106.814129] sd 7:0:0:0: [sdb] Attached SCSI disk                            
[  106.814306] sd 7:0:0:0: Attached scsi generic sg2 type 0
< The following  happened shortly after the mount attmept was made (I was monitoring dmesg with tail -f) >
[  147.857656] ehci_hcd 0000:00:13.5: force halt; handhake ffffc20000064824 00004000 00000000 -> -110                                                          
[  147.868050] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868054] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868057] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868059] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868062] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868064] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?  
[  147.868067] hub 1-0:1.0: cannot disable port 1 (err = -108)                  
[  147.868070] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868073] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868076] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868078] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868081] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868082] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?  
[  147.868086] hub 1-0:1.0: cannot disable port 1 (err = -108)                  
[  147.868089] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868092] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868095] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868098] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868101] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868103] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?  
[  147.868106] hub 1-0:1.0: cannot disable port 1 (err = -108)                  
[  147.868109] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868112] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868115] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868118] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868120] hub 1-0:1.0: cannot reset port 1 (err = -108)                    
[  147.868123] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?  
[  147.868125] hub 1-0:1.0: cannot disable port 1 (err = -108)                  
[  147.868128] hub 1-0:1.0: cannot disable port 1 (err = -108)                  
[  147.868176] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                    
[  147.868180] end_request: I/O error, dev sdb, sector 240                      
[  147.868184] Buffer I/O error on device sdb, logical block 30                
[  147.868188] Buffer I/O error on device sdb, logical block 31                
[  147.868232] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                    
[  147.868235] end_request: I/O error, dev sdb, sector 0                        
[  147.868238] Buffer I/O error on device sdb, logical block 0                  
[  147.868242] Buffer I/O error on device sdb, logical block 1                  
[  147.868245] Buffer I/O error on device sdb, logical block 2                  
[  147.868247] Buffer I/O error on device sdb, logical block 3                  
[  147.868250] Buffer I/O error on device sdb, logical block 4                  
[  147.868253] Buffer I/O error on device sdb, logical block 5                  
[  147.868255] Buffer I/O error on device sdb, logical block 6                  
[  147.868258] Buffer I/O error on device sdb, logical block 7                  
[  147.868286] hub 1-0:1.0: hub_port_status failed (err = -108)                
[  147.868332] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                    
[  147.868335] end_request: I/O error, dev sdb, sector 0                        
[  147.878608] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                    
[  147.878615] end_request: I/O error, dev sdb, sector 0                        
[  147.878667] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                    
[  147.878670] end_request: I/O error, dev sdb, sector 8                        
[  147.891253] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                    
[  147.891261] end_request: I/O error, dev sdb, sector 63                      
[  147.891395] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                    
[  147.891398] end_request: I/O error, dev sdb, sector 303                      
[  147.891450] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK                                                                    
[  147.891453] end_request: I/O error, dev sdb, sector 63                      
[  147.891500] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  147.891503] end_request: I/O error, dev sdb, sector 65
[  147.891545] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  147.891548] end_request: I/O error, dev sdb, sector 67
[  147.891589] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  147.891592] end_request: I/O error, dev sdb, sector 69
[  147.897097] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  147.897104] end_request: I/O error, dev sdb, sector 0
[  147.902489] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  147.902495] end_request: I/O error, dev sdb, sector 63
[  147.902564] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  147.902567] end_request: I/O error, dev sdb, sector 63
[  147.902605] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  147.902608] end_request: I/O error, dev sdb, sector 65

```Not sure if it's relevant, but it seems I can't start the ehci-hcd module manually. I just get "FATAL: Module ehci_hcd not found.".

Aside from that first boot with acpi=noirq, ehci keeps halting during boot just as before adding the kernel parameter. I've also tried irqpoll as kernel parameter, because that used to be required when I ran gutsy (or else the system wouldn't boot at all), but it doesn't make any difference.

Where I am atm I don't really have any other usb devices to try, except a mouse (which works).

Misc other info that might or might not help:
```

alib@laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914                                          
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)        
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)        
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)        
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA                          
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)                                
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)                                
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)                                
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)                                
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)                                
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)                      
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)                          
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE                                        
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)                          
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge                              
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge                              
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration                                                                                                      
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map                        
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller                    
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control              
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]              
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]                  
05:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)          
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)                                                                                                      
08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)                            
08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)                
08:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)                      
08:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)                                
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

alib@laptop:~$ lsmod
Module                  Size  Used by
radeon                357792  2      
drm                   123232  3 radeon
ppdev                  16904  0       
bridge                 63904  0       
stp                    11140  1 bridge
bnep                   22912  2       
input_polldev          12688  0       
joydev                 20864  0       
lp                     19588  0       
parport                49584  2 ppdev,lp
tuner_xc2028           30000  1         
snd_hda_intel         557364  5         
snd_pcm_oss            52352  0         
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0                          
snd_seq_oss            41984  0                          
arc4                   10240  2                          
snd_seq_midi           15744  0                          
ecb                    11392  2                          
snd_rawmidi            33920  1 snd_seq_midi             
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi 
dvb_usb_dib0700        54536  0                          
dib7000p               27400  2 dvb_usb_dib0700          
dib7000m               24964  1 dvb_usb_dib0700          
dvb_usb                27148  1 dvb_usb_dib0700          
ath5k                 116224  0                          
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dvb_core              106924  1 dvb_usb                                                  
psmouse                64028  0                                                          
mac80211              251144  1 ath5k                                                    
snd_timer              34064  2 snd_pcm,snd_seq                                          
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dib3000mc              22280  1 dvb_usb_dib0700                                           
dibx000_common         12292  3 dib7000p,dib7000m,dib3000mc                               
dib0070                16772  1 dvb_usb_dib0700                                           
i2c_piix4              20112  0                                                           
sdhci_pci              16896  0
sdhci                  27396  1 sdhci_pci
btusb                  21784  2
serio_raw              14468  0
pcspkr                 11136  0
k8temp                 13440  0
video                  29204  0
stkwebcam              33156  0
compat_ioctl32         18304  1 stkwebcam
videodev               45184  2 stkwebcam,compat_ioctl32
v4l1_compat            23940  1 videodev
snd                    78792  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211               43168  2 ath5k,mac80211
asus_laptop            27740  0
output                 11648  1 video
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
led_class              13064  2 ath5k,asus_laptop
r8169                  46596  0
mii                    14464  1 r8169
ohci1394               42036  0
ieee1394              108288  1 ohci1394
usbhid                 47040  0
fbcon                  49792  0
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

alib@laptop:~$ lsusb
Bus 001 Device 004: ID 174f:a311 Syntek 1.3MPixel Web Cam - Asus A3A, A6J, A6K, A6M, A6R, A6T, A6V, A7T, A7sv, A7U
Bus 001 Device 005: ID 1164:1f08 YUAN High-Tech Development Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse

```I'd be very grateful for any help

---

### Post by ali.b on 2009-06-15
I tired of trying to fix the problem "properly" and simply installed the 32-bit version of kubuntu instead, which works fine. Just thought I'd mention that in case someone else suffers the same problem.

---

### Post by agorka on 2009-08-29
I have the same problem in 32bit ubuntu 9.10 on my netbook MSI Wind U90. Everything works except webcam. When I turn on webcam by Fn-F6, I get this:

```
[  357.424174] usb 1-5: new high speed USB device using ehci_hcd and address 4                                                  
[  357.756722] usb 1-5: configuration #1 chosen from 1 choice                                                                   
[  357.873908] Linux video capture interface: v2.00                                                                             
[  357.902444] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0141)                                                     
[  357.906707] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input9                        
[  357.907007] usbcore: registered new interface driver uvcvideo                                                                
[  357.907606] USB Video Class driver (v0.1.0)                                                                                  
[  357.957018] ehci_hcd 0000:00:1d.7: force halt; handhake f8042024 00004000 00000000 -> -110                                   
[  358.318679] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318695] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318705] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318715] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318726] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318734] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?                                                  
[  358.318744] hub 1-0:1.0: cannot disable port 1 (err = -108)                                                                  
[  358.318754] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318762] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318773] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318783] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318794] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318802] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?                                                  
[  358.318814] hub 1-0:1.0: cannot disable port 1 (err = -108)                                                                  
[  358.318827] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318838] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318848] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318859] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318869] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318877] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?                                                  
[  358.318888] hub 1-0:1.0: cannot disable port 1 (err = -108)                                                                  
[  358.318900] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318911] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318922] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318932] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318942] hub 1-0:1.0: cannot reset port 1 (err = -108)                                                                    
[  358.318950] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?                                                  
[  358.318964] hub 1-0:1.0: cannot disable port 1 (err = -108)                                                                  
[  358.318976] hub 1-0:1.0: cannot disable port 1 (err = -108)                                                                  
[  358.319012] hub 1-0:1.0: hub_port_status failed (err = -108)  
```

Then, no usb flash drives or cardreaders are seen in lsusb. Webcam still doesn't work. Only rebooting with webcam off helps.

---

