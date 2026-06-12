---
title: "Recent increase in CPU mean Temperature"
date: 2009-06-04
forum: x86 64-bit Users
---

### Post by blissfulpenguin on 2009-06-04
Hello all you really smart people.

Since my last amarok upgrade to 2.1, I have noticed a mild to moderate increase in my CPU temperature.  I don't even think this is related, because after rebooting I haven't started the application, and I see no instances of kde stuff in the process tree that I recognize.
```
root@unknown:/home/joshua# ps -ejH
  PID  PGID   SID TTY          TIME CMD
    2     0     0 ?        00:00:00 kthreadd
    3     0     0 ?        00:00:00   migration/0
    4     0     0 ?        00:00:01   ksoftirqd/0
    5     0     0 ?        00:00:00   watchdog/0
    6     0     0 ?        00:00:00   events/0
    7     0     0 ?        00:00:00   khelper
    8     0     0 ?        00:00:00   kstop/0
    9     0     0 ?        00:00:00   kintegrityd/0
   10     0     0 ?        00:00:00   kblockd/0
   11     0     0 ?        00:00:00   kacpid
   12     0     0 ?        00:00:00   kacpi_notify
   13     0     0 ?        00:00:00   cqueue
   14     0     0 ?        00:00:00   ata/0
   15     0     0 ?        00:00:00   ata_aux
   16     0     0 ?        00:00:00   ksuspend_usbd
   17     0     0 ?        00:00:00   khubd
   18     0     0 ?        00:00:00   kseriod
   19     0     0 ?        00:00:00   kmmcd
   20     0     0 ?        00:00:00   btaddconn
   21     0     0 ?        00:00:00   btdelconn
   22     0     0 ?        00:00:00   pdflush
   23     0     0 ?        00:00:00   pdflush
   24     0     0 ?        00:00:00   kswapd0
   25     0     0 ?        00:00:00   aio/0
   26     0     0 ?        00:00:00   ecryptfs-kthrea
   29     0     0 ?        00:00:00   scsi_eh_0
   30     0     0 ?        00:00:00   scsi_eh_1
   31     0     0 ?        00:00:00   scsi_eh_2
   32     0     0 ?        00:00:00   scsi_eh_3
   33     0     0 ?        00:00:00   kstriped
   34     0     0 ?        00:00:00   kmpathd/0
   35     0     0 ?        00:00:00   kmpath_handlerd
   36     0     0 ?        00:00:00   ksnapd
   37     0     0 ?        00:00:00   kondemand/0
   38     0     0 ?        00:00:00   krfcommd
  676     0     0 ?        00:00:00   scsi_eh_4
  679     0     0 ?        00:00:00   usb-storage
  830     0     0 ?        00:00:00   kjournald
 1726     0     0 ?        00:00:00   kgameportd
 2093     0     0 ?        00:00:00   kjournald
    1     1     1 ?        00:00:00 init
  964   964   964 ?        00:00:00   udevd
 2097  2097  2097 ?        00:00:00   mount.ntfs-3g
 2361  2361  2361 tty4     00:00:00   getty
 2362  2362  2362 tty5     00:00:00   getty
 2369  2369  2369 tty2     00:00:00   getty
 2370  2370  2370 tty3     00:00:00   getty
 2371  2371  2371 tty6     00:00:00   getty
 2441  2441  2441 ?        00:00:00   acpid
 2500  2500  2500 ?        00:00:00   syslogd
 2524  2523  2523 ?        00:00:00   dd
 2526  2526  2526 ?        00:00:00   klogd
 2551  2551  2551 ?        00:00:00   dbus-daemon
 2928  2928  2928 ?        00:00:00   exim4
 3006  3005  3005 ?        00:00:00   hddtemp
 3047  3047  3047 ?        00:00:00   transmission-da
 3069  3069  3069 ?        00:00:00   winbindd
 3077  3069  3069 ?        00:00:00     winbindd
 3109  3109  3109 ?        00:00:00   console-kit-dae
 3313  3313  3313 ?        00:00:00   gdm
 3316  3316  3313 ?        00:00:00     gdm
 3321  3321  3321 tty7     00:01:38       Xorg
 3995  3995  3995 ?        00:00:00       x-session-manag
 4051  4051  4051 ?        00:00:00         ssh-agent
 4063  4063  4063 ?        00:00:00         seahorse-agent
 4092  3995  3995 ?        00:00:11         metacity
 4094  3995  3995 ?        00:00:17         gnome-panel
 4095  3995  3995 ?        00:00:05         nautilus
 4100  3995  3995 ?        00:00:01         update-notifier
 4101  3995  3995 ?        00:00:00         bzr-notify
 4102  3995  3995 ?        00:00:02         pidgin
 4103  3995  3995 ?        00:00:01         twitux
 4110  3995  3995 ?        00:00:14         gnome-terminal
 4146  3995  3995 ?        00:00:00           gnome-pty-helpe
 4148  4148  4148 pts/0    00:00:00           bash
 4328  4328  4148 pts/0    00:00:00             su
 4336  4336  4148 pts/0    00:00:00               bash
19309 19309  4148 pts/0    00:00:00                 ps
 5159  5159  5159 pts/1    00:00:00           bash
 5187  5187  5159 pts/1    00:00:00             su
 5195  5195  5159 pts/1    00:00:00               bash
 4119  3995  3995 ?        00:00:00         bluetooth-apple
 4122  3995  3995 ?        00:00:00         python
 4125  3995  3995 ?        00:00:00         evolution-alarm
 3364  2551  2551 ?        00:00:00   wpa_supplicant
 3367  2551  2551 ?        00:00:00   nm-system-setti
 3372  3372  3372 ?        00:00:00   avahi-daemon
 3373  3373  3373 ?        00:00:00     avahi-daemon
 3400  3400  3400 ?        00:00:00   cupsd
 3424  3424  3424 ?        00:00:00   system-tools-ba
 3519  3519  3519 ?        00:00:00   atd
 3548  3548  3548 ?        00:00:00   dhclient3
 3585  3585  3585 ?        00:00:00   cron
 3780  3780  3780 ?        00:00:00   munin-node
 3926  3926  3926 tty1     00:00:00   getty
 3982  3316  3313 ?        00:00:00   gnome-keyring-d
 4054  3995  3995 ?        00:00:00   dbus-launch
 4055  4055  4055 ?        00:00:00   dbus-daemon
 4066  4055  4055 ?        00:00:00   gvfsd
 4070  4055  4055 ?        00:00:01   gconfd-2
 4074  4074  4074 ?        00:00:00   gvfs-fuse-daemo
 4086  4086  4086 ?        00:00:01   gnome-settings-
 4097  4097  4097 ?        00:00:00   bonobo-activati
 4126  4126  4126 ?        00:00:00   gnome-power-man
 4135  4097  4097 ?        00:00:09   multiload-apple
 4141  4097  4097 ?        00:00:00   trashapplet
 4143  4055  4055 ?        00:00:00   gvfsd-trash
 4188  4097  4097 ?        00:00:00   evolution-excha
 4194  4055  4055 ?        00:00:00   gvfs-hal-volume
 4201  4097  4097 ?        00:00:00   evolution-data-
 4211  4055  4055 ?        00:00:00   gvfs-gphoto2-vo
 4231  4055  4055 ?        00:00:00   gvfsd-burn
 4252  4097  4097 ?        00:00:00   indicator-apple
 4255  4097  4097 ?        00:00:00   fast-user-switc
 4258  4097  4097 ?        00:00:00   mixer_applet2
 4263  4055  4055 ?        00:00:00   notify-osd
 4297  4297  4297 ?        00:00:18   gnome-screensav
 5310  3995  3995 ?        00:00:01   gedit
 6551  6551  6551 ?        00:00:00   hald
 6555  6551  6551 ?        00:00:00     hald-runner
 6645  6551  6551 ?        00:00:00       hald-addon-inpu
 6802  6551  6551 ?        00:00:00       hald-addon-stor
 6805  6551  6551 ?        00:00:00       hald-addon-stor
 6812  6551  6551 ?        00:00:00       hald-addon-acpi
14983  4097  4097 ?        00:00:05   python
14987  4097  4097 ?        00:00:00   cpufreq-applet
18656  3995  3995 ?        00:00:38   firefox-3.5

```
Not sure where I have gone wrong, but I am sure somewhere during the Jaunty upgrade.  I can't seem to find the page that had instructions on post-upgrade maintenance.

But, here's an lsmod:
```
root@unknown:/home/joshua# lsmod
Module                  Size  Used by
isofs                  43688  1 
udf                    92584  0 
crc_itu_t              10496  1 udf
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  0 
input_polldev          12688  0 
video                  29204  0 
output                 11648  1 video
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_via82xx            36648  1 
gameport               21520  1 snd_via82xx
snd_ac97_codec        133848  1 snd_via82xx
snd_usb_audio         108832  0 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
ac97_bus               10368  1 snd_ac97_codec
snd_mpu401_uart        16640  1 snd_via82xx
snd_pcm                99592  4 snd_via82xx,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_page_alloc         18704  2 snd_via82xx,snd_pcm
snd_seq_dummy          11524  0 
snd_usb_lib            27392  1 snd_usb_audio
snd_seq_oss            41984  0 
wlan_scan_sta          21888  1 
snd_seq_midi           15744  0 
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_rawmidi            33920  3 snd_mpu401_uart,snd_usb_lib,snd_seq_midi
snd_hwdep              16776  1 snd_usb_audio
ath_rate_sample        21120  1 
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               8123768  26 
pcspkr                 11136  0 
ath_pci               108400  0 
i2c_viapro             17304  0 
k8temp                 13440  0 
shpchp                 44572  0 
wlan                  232736  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               225904  3 ath_rate_sample,ath_pci
snd                    78792  15 snd_via82xx,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_mpu401_uart,snd_pcm,snd_seq_oss,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
usblp                  22656  0 
usbhid                 47040  0 
usb_storage           115392  0 
via_rhine              34568  0 
mii                    14464  1 via_rhine
floppy                 75816  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```
Oddly, I just remembered also having plugged in a thumb drive around the time of amarok to test it as swap.  Never figured out how to do it, but do you think hal might be munching away?

```
hald --version
HAL package version: 0.5.12
```

Since I grabbed the thumbdrive there has been a near 20°Centigrade drop.  Here's some output from a log:
```
04Jun2009 16:28:57	Kernel i2c sensors (hwmon)	hwmon0 (1)	63
04Jun2009 16:29:02	Kernel i2c sensors (hwmon)	hwmon0 (1)	65
04Jun2009 16:29:07	Kernel i2c sensors (hwmon)	hwmon0 (1)	63
04Jun2009 16:29:12	Kernel i2c sensors (hwmon)	hwmon0 (1)	64
04Jun2009 16:29:17	Kernel i2c sensors (hwmon)	hwmon0 (1)	63
04Jun2009 16:29:22	Kernel i2c sensors (hwmon)	hwmon0 (1)	65
04Jun2009 16:29:27	Kernel i2c sensors (hwmon)	hwmon0 (1)	64
04Jun2009 16:29:32	Kernel i2c sensors (hwmon)	hwmon0 (1)	63
04Jun2009 16:29:37	Kernel i2c sensors (hwmon)	hwmon0 (1)	63
04Jun2009 16:29:42	Kernel i2c sensors (hwmon)	hwmon0 (1)	62
04Jun2009 16:29:47	Kernel i2c sensors (hwmon)	hwmon0 (1)	63
04Jun2009 16:29:52	Kernel i2c sensors (hwmon)	hwmon0 (1)	63
04Jun2009 16:29:57	Kernel i2c sensors (hwmon)	hwmon0 (1)	58
04Jun2009 16:30:02	Kernel i2c sensors (hwmon)	hwmon0 (1)	56
04Jun2009 16:30:07	Kernel i2c sensors (hwmon)	hwmon0 (1)	66 --> Here is where I pulled the thumbdrive.
04Jun2009 16:30:12	Kernel i2c sensors (hwmon)	hwmon0 (1)	55
04Jun2009 16:30:17	Kernel i2c sensors (hwmon)	hwmon0 (1)	55
04Jun2009 16:30:22	Kernel i2c sensors (hwmon)	hwmon0 (1)	53
04Jun2009 16:30:27	Kernel i2c sensors (hwmon)	hwmon0 (1)	53
04Jun2009 16:30:32	Kernel i2c sensors (hwmon)	hwmon0 (1)	51
04Jun2009 16:30:37	Kernel i2c sensors (hwmon)	hwmon0 (1)	53
04Jun2009 16:30:42	Kernel i2c sensors (hwmon)	hwmon0 (1)	53
04Jun2009 16:30:47	Kernel i2c sensors (hwmon)	hwmon0 (1)	52
04Jun2009 16:30:52	Kernel i2c sensors (hwmon)	hwmon0 (1)	52
04Jun2009 16:30:57	Kernel i2c sensors (hwmon)	hwmon0 (1)	52
04Jun2009 16:31:02	Kernel i2c sensors (hwmon)	hwmon0 (1)	51
04Jun2009 16:31:07	Kernel i2c sensors (hwmon)	hwmon0 (1)	50
04Jun2009 16:31:12	Kernel i2c sensors (hwmon)	hwmon0 (1)	50
04Jun2009 16:31:17	Kernel i2c sensors (hwmon)	hwmon0 (1)	50
04Jun2009 16:31:22	Kernel i2c sensors (hwmon)	hwmon0 (1)	50
04Jun2009 16:31:27	Kernel i2c sensors (hwmon)	hwmon0 (1)	51
04Jun2009 16:31:32	Kernel i2c sensors (hwmon)	hwmon0 (1)	50
04Jun2009 16:31:37	Kernel i2c sensors (hwmon)	hwmon0 (1)	49
04Jun2009 16:31:42	Kernel i2c sensors (hwmon)	hwmon0 (1)	50
04Jun2009 16:31:47	Kernel i2c sensors (hwmon)	hwmon0 (1)	49
04Jun2009 16:31:52	Kernel i2c sensors (hwmon)	hwmon0 (1)	50
04Jun2009 16:31:57	Kernel i2c sensors (hwmon)	hwmon0 (1)	51
04Jun2009 16:32:02	Kernel i2c sensors (hwmon)	hwmon0 (1)	49
04Jun2009 16:32:07	Kernel i2c sensors (hwmon)	hwmon0 (1)	48
04Jun2009 16:32:12	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:32:17	Kernel i2c sensors (hwmon)	hwmon0 (1)	48
04Jun2009 16:32:22	Kernel i2c sensors (hwmon)	hwmon0 (1)	46
04Jun2009 16:32:27	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:32:32	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:32:37	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:32:42	Kernel i2c sensors (hwmon)	hwmon0 (1)	46
04Jun2009 16:32:47	Kernel i2c sensors (hwmon)	hwmon0 (1)	45
04Jun2009 16:32:52	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:32:57	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:33:02	Kernel i2c sensors (hwmon)	hwmon0 (1)	46
04Jun2009 16:33:07	Kernel i2c sensors (hwmon)	hwmon0 (1)	48
04Jun2009 16:33:12	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:33:17	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:33:22	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:33:28	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:33:33	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:33:38	Kernel i2c sensors (hwmon)	hwmon0 (1)	45
04Jun2009 16:33:43	Kernel i2c sensors (hwmon)	hwmon0 (1)	46
04Jun2009 16:33:48	Kernel i2c sensors (hwmon)	hwmon0 (1)	46
04Jun2009 16:33:53	Kernel i2c sensors (hwmon)	hwmon0 (1)	45
04Jun2009 16:33:58	Kernel i2c sensors (hwmon)	hwmon0 (1)	46
04Jun2009 16:34:03	Kernel i2c sensors (hwmon)	hwmon0 (1)	46
04Jun2009 16:34:08	Kernel i2c sensors (hwmon)	hwmon0 (1)	45
04Jun2009 16:34:13	Kernel i2c sensors (hwmon)	hwmon0 (1)	46
04Jun2009 16:34:18	Kernel i2c sensors (hwmon)	hwmon0 (1)	50
04Jun2009 16:34:23	Kernel i2c sensors (hwmon)	hwmon0 (1)	46
04Jun2009 16:34:28	Kernel i2c sensors (hwmon)	hwmon0 (1)	50
04Jun2009 16:34:33	Kernel i2c sensors (hwmon)	hwmon0 (1)	47
04Jun2009 16:34:38	Kernel i2c sensors (hwmon)	hwmon0 (1)	46
04Jun2009 16:34:43	Kernel i2c sensors (hwmon)	hwmon0 (1)	45
04Jun2009 16:34:48	Kernel i2c sensors (hwmon)	hwmon0 (1)	46
04Jun2009 16:34:53	Kernel i2c sensors (hwmon)	hwmon0 (1)	45 -->here is where I am about to make the post.
```

Maybe all that code will help?  I certainly appreciate any insight, and if I need to post this as bug, let me know.

---

### Post by loomsen on 2009-06-04
You should provide some more informative code, for example from your dmesg.

But the kernel shipped with jaunty caused severe problems for me as well.

Trace:
look into your logfiles (either gui'd or under /var/log/)
dmesg will tell you whats going on too ( pipe it through | less as it's a lot of output... but it provides a lot of information as well)



66° has been pretty much my average since jauntys alpha was released, another issue caused by ipv6, and, pretty much untracable high temperature. There obv is some regression, anyway, as 2.6.29 is stable in version 4 in the meanwhile, I can't understand ubuntus thoughts there at all anyway.

I'm running a fedora system with a btrfs more stable than ext4 could even think of, plymouth enabled, my hardware detected perfectly, a reasonable temp of 40°-50° and so many more advantages I cant tell. Give it a try, gnome is gnome, theres an apt frontend to redhats rpm, and its community driven (There are a LOT! of builds)

In doubt, boot from a live cd, shrink your partition, install fedora onto another (if you have a separate home partition you can simply mount it during install...) Even if it's just to trace the bug. (But I think you'll like it ;) ) If you grab the netinstall you'll be able to configure the package installation with anaconda, which is very nice as well.

Enjoy

---

