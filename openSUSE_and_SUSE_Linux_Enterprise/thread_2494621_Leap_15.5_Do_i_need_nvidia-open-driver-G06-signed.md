---
title: "Leap 15.5: Do i need nvidia-open-driver-G06-signed ?"
date: 2024-01-22
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-01-22
```
maketopsite:/home/maketopsite # LANG=C zypper lp
Loading repository data...
Reading installed packages...

Repository                                                   | Name                       | Category    | Severity | Interactive | Status | Since | Summary
-------------------------------------------------------------+----------------------------+-------------+----------+-------------+--------+-------+-----------------------------------------------------
Update repository with updates from SUSE Linux Enterprise 15 | openSUSE-SLE-15.5-2024-143 | recommended | moderate | ---         | needed | -     | Recommended update for nvidia-open-driver-G06-signed
Update repository with updates from SUSE Linux Enterprise 15 | openSUSE-SLE-15.5-2024-145 | recommended | moderate | ---         | needed | -     | Recommended update for btrfsprogs
Update repository with updates from SUSE Linux Enterprise 15 | openSUSE-SLE-15.5-2024-161 | recommended | moderate | ---         | needed | -     | Recommended update for dpdk22

Found 3 applicable patches:
3 patches needed (0 security patches)
```

```
maketopsite@maketopsite:~> LANG=C zypper se -i nvidia
Loading repository data...
Reading installed packages...

S  | Name                            | Summary                                                               | Type
---+---------------------------------+-----------------------------------------------------------------------+--------
i  | kernel-firmware-nvidia          | Kernel firmware files for Nvidia Tegra and graphics drivers           | package
i  | kernel-firmware-nvidia-gsp-G06  | Kernel firmware file for open NVIDIA kernel module driver G06         | package
i  | kernel-firmware-nvidia-gspx-G06 | Kernel firmware file for open NVIDIA kernel module driver G06         | package
i  | nvidia-computeG05               | NVIDIA driver for computing with GPGPU                                | package
i  | nvidia-computeG05-32bit         | 32bit NVIDIA driver for computing with GPGPU                          | package
i  | nvidia-gfxG05-kmp-default       | NVIDIA graphics driver kernel module for GeForce 600 series and newer | package
i  | nvidia-glG05                    | NVIDIA OpenGL libraries for OpenGL acceleration                       | package
i  | nvidia-glG05-32bit              | 32bit NVIDIA OpenGL libraries for OpenGL acceleration                 | package
i+ | x11-video-nvidiaG05             | NVIDIA graphics driver for GeForce 600 series and newer               | package
i  | x11-video-nvidiaG05-32bit       | 32bit NVIDIA graphics driver for GeForce 600 series and newer         | package
```

Do i need other *G06* packages ? I did not install them.

NVIDIA Corporation GK107M [GeForce GTX 660M]

---

### Post by maketopsite on 2024-01-25
removing G06 firmware solved the problem.

---

