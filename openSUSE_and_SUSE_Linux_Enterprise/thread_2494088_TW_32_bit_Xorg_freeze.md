---
title: "TW 32 bit: Xorg freeze"
date: 2024-01-05
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-01-05
Xorg freeze during browsing using Firefox (installed from Tumbleweed repo). Caps Lock and Scroll Lock LEDs started to blink. Power Off button was needed to reboot. IceWM. Any idea pls why this happened ?

```
Jan 05 07:00:14 maketopsite systemd[1]: snapperd.service: Consumed 2.774s CPU time.
Jan 05 07:00:14 maketopsite systemd[1]: snapperd.service: Deactivated successfully.
Jan 05 07:00:10 maketopsite systemd-logind[828]: Removed session c2.
Jan 05 07:00:10 maketopsite systemd[1]: session-c2.scope: Consumed 4.732s CPU time.
Jan 05 07:00:10 maketopsite systemd[1]: session-c2.scope: Deactivated successfully.
Jan 05 07:00:10 maketopsite systemd[1]: systemd-coredump@0-4907-0.service: Deactivated successfully.
Jan 05 07:00:10 maketopsite systemd-coredump[4921]: [&#129109;] Process 4076 (gnome-session-b) of user 461 dumped core.


                                              Stack trace of thread 4076:
                                              #0  0x00000000004869b7 n/a (gnome-session-binary + 0x1b9b7)
                                              #1  0x000000000048717f n/a (gnome-session-binary + 0x1c17f)
                                              #2  0x00000000b7adf3ad g_hash_table_find (libglib-2.0.so.0 + 0x463ad)
                                              #3  0x0000000000489aba n/a (gnome-session-binary + 0x1eaba)
                                              #4  0x000000000048b46d n/a (gnome-session-binary + 0x2046d)
                                              #5  0x00000000004904eb n/a (gnome-session-binary + 0x254eb)
                                              #6  0x00000000b7af10ac n/a (libglib-2.0.so.0 + 0x580ac)
                                              #7  0x00000000b7af2de7 n/a (libglib-2.0.so.0 + 0x59de7)
                                              #8  0x00000000b7af37b9 g_main_loop_run (libglib-2.0.so.0 + 0x5a7b9)
                                              #9  0x0000000000490332 n/a (gnome-session-binary + 0x25332)
                                              #10 0x00000000004742bc n/a (gnome-session-binary + 0x92bc)
                                              #11 0x00000000b7623c75 __libc_start_call_main (libc.so.6 + 0x23c75)
                                              #12 0x00000000b7623d38 __libc_start_main@@GLIBC_2.34 (libc.so.6 + 0x23d38)
                                              #13 0x0000000000474d37 n/a (gnome-session-binary + 0x9d37)
                                              
                                              Stack trace of thread 4095:
                                              #0  0x00000000b7f1c579 __kernel_vsyscall (linux-gate.so.1 + 0x579)
                                              #1  0x00000000b77261f7 syscall (libc.so.6 + 0x1261f7)
                                              #2  0x00000000b7b4ee4a g_cond_wait (libglib-2.0.so.0 + 0xb5e4a)
                                              #3  0x00000000b7abba25 n/a (libglib-2.0.so.0 + 0x22a25)
                                              #4  0x00000000b7abc018 g_async_queue_pop_unlocked (libglib-2.0.so.0 + 0x23018)
                                              #5  0x00000000b7b20fe3 n/a (libglib-2.0.so.0 + 0x87fe3)
                                              #6  0x00000000b7b20867 n/a (libglib-2.0.so.0 + 0x87867)
                                              #7  0x00000000b768b3ed start_thread (libc.so.6 + 0x8b3ed)
                                              #8  0x00000000b7728ba8 __clone3 (libc.so.6 + 0x128ba8)
                                              
                                              Stack trace of thread 4097:
                                              #0  0x00000000b7f1c579 __kernel_vsyscall (linux-gate.so.1 + 0x579)
                                              #1  0x00000000b771ab37 __poll (libc.so.6 + 0x11ab37)
                                              #2  0x00000000b7b04eb0 g_poll (libglib-2.0.so.0 + 0x6beb0)
                                              #3  0x00000000b7af2d87 n/a (libglib-2.0.so.0 + 0x59d87)
                                              #4  0x00000000b7af37b9 g_main_loop_run (libglib-2.0.so.0 + 0x5a7b9)
                                              #5  0x00000000b7d215d5 n/a (libgio-2.0.so.0 + 0x1215d5)
                                              #6  0x00000000b7b20867 n/a (libglib-2.0.so.0 + 0x87867)
                                              #7  0x00000000b768b3ed start_thread (libc.so.6 + 0x8b3ed)
                                              #8  0x00000000b7728ba8 __clone3 (libc.so.6 + 0x128ba8)

                                              Stack trace of thread 4096:
                                              #0  0x00000000b7f1c579 __kernel_vsyscall (linux-gate.so.1 + 0x579)
                                              #1  0x00000000b771ab37 __poll (libc.so.6 + 0x11ab37)
                                              #2  0x00000000b7b04eb0 g_poll (libglib-2.0.so.0 + 0x6beb0)
                                              #3  0x00000000b7af2d87 n/a (libglib-2.0.so.0 + 0x59d87)
                                              #4  0x00000000b7af3554 g_main_context_iteration (libglib-2.0.so.0 + 0x5a554)
                                              #5  0x00000000b7af35b0 n/a (libglib-2.0.so.0 + 0x5a5b0)
                                              #6  0x00000000b7b20867 n/a (libglib-2.0.so.0 + 0x87867)
                                              #7  0x00000000b768b3ed start_thread (libc.so.6 + 0x8b3ed)
                                              #8  0x00000000b7728ba8 __clone3 (libc.so.6 + 0x128ba8)
                                              
                                              Stack trace of thread 4098:
                                              #0  0x00000000b7f1c579 __kernel_vsyscall (linux-gate.so.1 + 0x579)
                                              #1  0x00000000b771ab37 __poll (libc.so.6 + 0x11ab37)
                                              #2  0x00000000b7b04eb0 g_poll (libglib-2.0.so.0 + 0x6beb0)
                                              #3  0x00000000b7af2d87 n/a (libglib-2.0.so.0 + 0x59d87)
                                              #4  0x00000000b7af3554 g_main_context_iteration (libglib-2.0.so.0 + 0x5a554)
                                              #5  0x00000000b4774bab n/a (libdconfsettings.so + 0x5bab)
                                              #6  0x00000000b7b20867 n/a (libglib-2.0.so.0 + 0x87867)
                                              #7  0x00000000b768b3ed start_thread (libc.so.6 + 0x8b3ed)
                                              #8  0x00000000b7728ba8 __clone3 (libc.so.6 + 0x128ba8)
                                              ELF object binary architecture: Intel 80386
Jan 05 07:00:10 maketopsite systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Jan 05 07:00:09 maketopsite su[4897]: pam_unix(su:session): session opened for user root(uid=0) by maketopsite(uid=1000)
Jan 05 07:00:09 maketopsite su[4897]: (to root) maketopsite on pts/0
Jan 05 07:00:09 maketopsite su[4897]: gkr-pam: couldn't unlock the login keyring.
Jan 05 07:00:09 maketopsite su[4897]: The gnome keyring socket is not owned with the same credentials as the user login: /run/user/1000/keyring/cont>
Jan 05 07:00:09 maketopsite systemd[1]: Started Process Core Dump (PID 4907/UID 0).
Jan 05 07:00:09 maketopsite systemd[1]: Created slice Slice /system/systemd-coredump.
Jan 05 07:00:09 maketopsite systemd-logind[828]: Session c2 logged out. Waiting for processes to exit.
Jan 05 07:00:09 maketopsite gdm-launch-environment][3937]: pam_unix(gdm-launch-environment:session): session closed for user gdm
Jan 05 07:00:09 maketopsite gdm-x-session[4063]: GLib: Source ID 2 was not found when attempting to remove it
Jan 05 07:00:09 maketopsite /usr/libexec/gdm/gdm-x-session[4065]: (II) Server terminated successfully (0). Closing log file.
Jan 05 07:00:09 maketopsite /usr/libexec/gdm/gdm-x-session[4065]: (II) systemd-logind: releasing fd for 13:67
Jan 05 07:00:09 maketopsite /usr/libexec/gdm/gdm-x-session[4065]: (II) UnloadModule: "libinput"

Jan 05 07:00:09 maketopsite polkitd[750]: Unregistered Authentication Agent for unix-session:c2 (system bus name :1.75, object path /org/freedesktop>
Jan 05 07:00:09 maketopsite /usr/libexec/gdm/gdm-x-session[4065]: (II) systemd-logind: releasing fd for 13:66
Jan 05 07:00:09 maketopsite /usr/libexec/gdm/gdm-x-session[4065]: (II) UnloadModule: "libinput"
Jan 05 07:00:09 maketopsite systemd[1]: packagekit.service: Deactivated successfully.
Jan 05 07:00:09 maketopsite PackageKit[4161]: daemon quit
Jan 05 07:00:09 maketopsite /usr/libexec/gdm/gdm-x-session[4065]: (II) systemd-logind: releasing fd for 13:65
Jan 05 07:00:09 maketopsite /usr/libexec/gdm/gdm-x-session[4065]: (II) UnloadModule: "libinput"
Jan 05 07:00:09 maketopsite /usr/libexec/gdm/gdm-x-session[4065]: (II) systemd-logind: releasing fd for 13:64
Jan 05 07:00:09 maketopsite /usr/libexec/gdm/gdm-x-session[4065]: (II) UnloadModule: "libinput"
Jan 05 07:00:09 maketopsite gsd-print-notif[4196]: Error releasing name org.gnome.SettingsDaemon.PrintNotifications: The connection is closed
Jan 05 07:00:09 maketopsite kernel: Code: 00 00 00 57 56 e8 e5 61 00 00 81 c6 39 af 02 00 53 89 c3 8b be b0 08 00 00 01 c7 e8 e3 92 ff ff 85 db 74 2>
Jan 05 07:00:09 maketopsite kernel: gnome-session-b[4076]: segfault at aaaaaaaa ip 004869b7 sp bfca6fa0 error 4 in gnome-session-binary[472000+23000>
Jan 05 07:00:09 maketopsite kernel: show_signal_msg: 53 callbacks suppressed
Jan 05 07:00:09 maketopsite gsd-screensaver[4209]: Error releasing name org.gnome.SettingsDaemon.ScreensaverProxy: The connection is closed
Jan 05 07:00:09 maketopsite gsd-housekeepin[4216]: Error releasing name org.gnome.SettingsDaemon.Housekeeping: The connection is closed
Jan 05 07:00:09 maketopsite gsd-sharing[4180]: Error releasing name org.gnome.SettingsDaemon.Sharing: The connection is closed
Jan 05 07:00:09 maketopsite gsd-rfkill[4199]: Error releasing name org.gnome.SettingsDaemon.Rfkill: The connection is closed
Jan 05 07:00:09 maketopsite org.gnome.Shell.desktop[4102]:       after 2290 requests (2290 known processed) with 0 events remaining.
Jan 05 07:00:09 maketopsite org.gnome.Shell.desktop[4102]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
Jan 05 07:00:03 maketopsite at-spi-bus-launcher[4871]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry

```

```
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4250] (prog-if 00 [VGA controller])
    Subsystem: ASRock Incorporation Device 9715
    Flags: bus master, fast devsel, latency 0, IRQ 18, NUMA node 0
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at d000 [size=256]
    Memory at fe8f0000 (32-bit, non-prefetchable) [size=64K]
    Memory at fe700000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: radeon
    Kernel modules: radeon, amdgpu

```

---

