---
title: "Leap 15.5: File conflicts happen when two packages attempt to install files with the"
date: 2023-10-02
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2023-10-02
```
# zypper up
Loading repository data...
Reading installed packages...


The following 55 package updates will NOT be installed:
  Mesa Mesa-KHR-devel Mesa-dri Mesa-dri-nouveau Mesa-gallium Mesa-libEGL-devel Mesa-libEGL1 Mesa-libGL-devel Mesa-libGL1
  Mesa-libGLESv2-devel Mesa-libglapi0 Mesa-libva Mesa-vulkan-device-select conky dnsmasq gstreamer-plugin-pipewire iscsiuio krb5
  krb5-server libOSMesa8 libgbm-devel libgbm1 libmbim libmbim-glib4 libndp0 libpipewire-0_3-0 libqmi-glib5 libqmi-tools
  libquicktime0 libteamdctl0 libvdpau_nouveau libverto-libev1 libverto1 libvulkan_intel mbimcli-bash-completion open-iscsi
  openconnect openconnect-lang openssh openssh-askpass-gnome openssh-clients openssh-common openssh-helpers openssh-server pipewire
  pipewire-lang pipewire-modules-0_3 pipewire-spa-plugins-0_2 pipewire-spa-tools pipewire-tools rp-pppoe rpcbind rsync tnftp w3m


The following 20 packages are going to be upgraded:
  ffmpeg-3 ffmpeg-4 libavcodec57 libavcodec58_134 libavdevice57 libavdevice58_13 libavfilter6 libavfilter7_110 libavformat57
  libavformat58_76 libavresample3 libavresample4_0 libavutil55 libavutil56_70 libpostproc54 libpostproc55_9 libswresample2
  libswresample3_9 libswscale4 libswscale5_9


20 packages to upgrade.
Overall download size: 0 B. Already cached: 17.1 MiB. After the operation, 16.0 KiB will be freed.
Continue? [y/n/v/...? shows all options] (y): 
In cache libavutil56_70-4.4.4-150500.5.pm.1.x86_64.rpm                                                        (1/20), 278.3 KiB    
In cache libavutil55-3.4.12-150500.2.pm.1.x86_64.rpm                                                          (2/20), 257.6 KiB    
In cache libpostproc55_9-4.4.4-150500.5.pm.1.x86_64.rpm                                                       (3/20), 103.6 KiB    
In cache libavresample4_0-4.4.4-150500.5.pm.1.x86_64.rpm                                                      (4/20), 108.8 KiB    
In cache libswscale5_9-4.4.4-150500.5.pm.1.x86_64.rpm                                                         (5/20), 206.3 KiB    
In cache libswresample3_9-4.4.4-150500.5.pm.1.x86_64.rpm                                                      (6/20), 109.6 KiB    
In cache libswscale4-3.4.12-150500.2.pm.1.x86_64.rpm                                                          (7/20), 180.9 KiB    
In cache libavresample3-3.4.12-150500.2.pm.1.x86_64.rpm                                                       (8/20),  92.4 KiB    
In cache libswresample2-3.4.12-150500.2.pm.1.x86_64.rpm                                                       (9/20),  93.2 KiB    
In cache libpostproc54-3.4.12-150500.2.pm.1.x86_64.rpm                                                       (10/20),  87.3 KiB    
In cache libavcodec58_134-4.4.4-150500.5.pm.1.x86_64.rpm                                                     (11/20),   4.4 MiB    
In cache libavcodec57-3.4.12-150500.2.pm.1.x86_64.rpm                                                        (12/20),   4.0 MiB    
In cache libavformat58_76-4.4.4-150500.5.pm.1.x86_64.rpm                                                     (13/20), 981.4 KiB    
In cache libavformat57-3.4.12-150500.2.pm.1.x86_64.rpm                                                       (14/20), 874.4 KiB    
In cache libavfilter7_110-4.4.4-150500.5.pm.1.x86_64.rpm                                                     (15/20),   1.2 MiB    
In cache libavfilter6-3.4.12-150500.2.pm.1.x86_64.rpm                                                        (16/20), 823.2 KiB    
In cache libavdevice58_13-4.4.4-150500.5.pm.1.x86_64.rpm                                                     (17/20), 118.6 KiB    
In cache libavdevice57-3.4.12-150500.2.pm.1.x86_64.rpm                                                       (18/20),  98.4 KiB    
In cache ffmpeg-4-4.4.4-150500.5.pm.1.x86_64.rpm                                                             (19/20),   1.7 MiB    
In cache ffmpeg-3-3.4.12-150500.2.pm.1.x86_64.rpm                                                            (20/20),   1.6 MiB    


Checking for file conflicts: ...............................................................................................[error]
Detected 33 file conflicts:


File /usr/bin/aviocat
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/cws2fws
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/ffescape
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/ffeval
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/ffhash
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/ffmpeg
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/ffplay
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/ffprobe
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/fourcc2pixfmt
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/graph2dot
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/ismindex
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/pktdumper
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/probetest
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/qt-faststart
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/seek_print
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/sidxindex
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/bin/trasher
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/ffmpeg/ffprobe.xsd
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffmpeg-all.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffmpeg-bitstream-filters.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffmpeg-codecs.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffmpeg-devices.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffmpeg-filters.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffmpeg-formats.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffmpeg-protocols.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffmpeg-resampler.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffmpeg-scaler.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffmpeg-utils.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffmpeg.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffplay-all.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffplay.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffprobe-all.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File /usr/share/man/man1/ffprobe.1.gz
  from install of
     ffmpeg-4-4.4.4-150500.5.pm.1.x86_64 (packman_new)
  conflicts with file from install of
     ffmpeg-3-3.4.12-150500.2.pm.1.x86_64 (packman_new)


File conflicts happen when two packages attempt to install files with the same name but different contents. If you continue, conflicting files will be replaced losing the previous content.
Continue? [yes/no] (no): 



```


Is it please safe to overwrite all ?

---

### Post by Xian on 2023-10-02
Try first to remove ffmpeg-3 and then install the updated ffmpeg-4

zypper rm ffmpeg-3
zypper in -f ffmpeg-4

---

### Post by maketopsite on 2023-10-06
> **Xian said:**
> Try first to remove ffmpeg-3 and then install the updated ffmpeg-4

zypper rm ffmpeg-3
zypper in -f ffmpeg-4

Thank you this has solved the problem.

---

