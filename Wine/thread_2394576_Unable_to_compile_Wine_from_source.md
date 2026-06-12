---
title: "Unable to compile Wine from source"
date: 2018-06-18
forum: Wine
---

### Post by skade88 on 2018-06-18
Howdy All!

I am having issues compiling wine from source on Ubuntu 18.04. I have tried 'sudo apt-get build-dep wine', this does not resolve the issue. I am using this guide to build wine with. ([https://wiki.winehq.org/Building_Wine](https://wiki.winehq.org/Building_Wine)). I am guessing I am missing libs for openGL but I am not sure which one(s) I need to install. Any pro tips would be helpful.

```
./configure --enable-win64
[INDENT]configure: libhal 64-bit development files not found, no legacy dynamic device support.[/INDENT]
[INDENT]configure: vkd3d 64-bit development files not found, Direct3D 12 won't be supported.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]configure: WARNING: No OpenGL library found on this system.[/INDENT]
[INDENT]OpenGL and Direct3D won't be supported.
[/INDENT]

```
Full output
======================
```
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for cpp... cpp
checking for ld... ld
checking whether gcc supports __builtin_ms_va_list... yes
checking for the directory containing the Wine tools... $(top_builddir)
checking for flex... flex
checking whether flex is recent enough... yes
checking for bison... bison
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking whether ln -s works... yes
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ldconfig... /sbin/ldconfig
checking for msgfmt... msgfmt
checking for pkg-config... pkg-config
checking whether msgfmt supports contexts... yes
checking for i386_set_ldt in -li386... no
checking for _oss_ioctl in -lossaudio... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking how to run the C preprocessor... gcc -m64 -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking AL/al.h usability... yes
checking AL/al.h presence... yes
checking for AL/al.h... yes
checking ApplicationServices/ApplicationServices.h usability... no
checking ApplicationServices/ApplicationServices.h presence... no
checking for ApplicationServices/ApplicationServices.h... no
checking AudioToolbox/AudioConverter.h usability... no
checking AudioToolbox/AudioConverter.h presence... no
checking for AudioToolbox/AudioConverter.h... no
checking AudioUnit/AudioUnit.h usability... no
checking AudioUnit/AudioUnit.h presence... no
checking for AudioUnit/AudioUnit.h... no
checking AudioUnit/AudioComponent.h usability... no
checking AudioUnit/AudioComponent.h presence... no
checking for AudioUnit/AudioComponent.h... no
checking CL/cl.h usability... yes
checking CL/cl.h presence... yes
checking for CL/cl.h... yes
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CommonCrypto/CommonCryptor.h usability... no
checking CommonCrypto/CommonCryptor.h presence... no
checking for CommonCrypto/CommonCryptor.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking CoreServices/CoreServices.h usability... no
checking CoreServices/CoreServices.h presence... no
checking for CoreServices/CoreServices.h... no
checking DiskArbitration/DiskArbitration.h usability... no
checking DiskArbitration/DiskArbitration.h presence... no
checking for DiskArbitration/DiskArbitration.h... no
checking EGL/egl.h usability... yes
checking EGL/egl.h presence... yes
checking for EGL/egl.h... yes
checking IOKit/IOKitLib.h usability... no
checking IOKit/IOKitLib.h presence... no
checking for IOKit/IOKitLib.h... no
checking IOKit/hid/IOHIDLib.h usability... no
checking IOKit/hid/IOHIDLib.h presence... no
checking for IOKit/hid/IOHIDLib.h... no
checking OpenAL/al.h usability... no
checking OpenAL/al.h presence... no
checking for OpenAL/al.h... no
checking OpenCL/opencl.h usability... no
checking OpenCL/opencl.h presence... no
checking for OpenCL/opencl.h... no
checking QuickTime/ImageCompression.h usability... no
checking QuickTime/ImageCompression.h presence... no
checking for QuickTime/ImageCompression.h... no
checking Security/Security.h usability... no
checking Security/Security.h presence... no
checking for Security/Security.h... no
checking alias.h usability... no
checking alias.h presence... no
checking for alias.h... no
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking arpa/nameser.h usability... yes
checking arpa/nameser.h presence... yes
checking for arpa/nameser.h... yes
checking asm/types.h usability... yes
checking asm/types.h presence... yes
checking for asm/types.h... yes
checking asm/user.h usability... no
checking asm/user.h presence... no
checking for asm/user.h... no
checking curses.h usability... yes
checking curses.h presence... yes
checking for curses.h... yes
checking direct.h usability... no
checking direct.h presence... no
checking for direct.h... no
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking elf.h usability... yes
checking elf.h presence... yes
checking for elf.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking fnmatch.h usability... yes
checking fnmatch.h presence... yes
checking for fnmatch.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking gettext-po.h usability... yes
checking gettext-po.h presence... yes
checking for gettext-po.h... yes
checking grp.h usability... yes
checking grp.h presence... yes
checking for grp.h... yes
checking gsm.h usability... yes
checking gsm.h presence... yes
checking for gsm.h... yes
checking gsm/gsm.h usability... yes
checking gsm/gsm.h presence... yes
checking for gsm/gsm.h... yes
checking ieeefp.h usability... no
checking ieeefp.h presence... no
checking for ieeefp.h... no
checking inet/mib2.h usability... no
checking inet/mib2.h presence... no
checking for inet/mib2.h... no
checking io.h usability... no
checking io.h presence... no
checking for io.h... no
checking kstat.h usability... no
checking kstat.h presence... no
checking for kstat.h... no
checking libproc.h usability... no
checking libproc.h presence... no
checking for libproc.h... no
checking link.h usability... yes
checking link.h presence... yes
checking for link.h... yes
checking linux/cdrom.h usability... yes
checking linux/cdrom.h presence... yes
checking for linux/cdrom.h... yes
checking linux/compiler.h usability... no
checking linux/compiler.h presence... no
checking for linux/compiler.h... no
checking linux/filter.h usability... yes
checking linux/filter.h presence... yes
checking for linux/filter.h... yes
checking linux/hdreg.h usability... yes
checking linux/hdreg.h presence... yes
checking for linux/hdreg.h... yes
checking linux/hidraw.h usability... yes
checking linux/hidraw.h presence... yes
checking for linux/hidraw.h... yes
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking linux/ioctl.h usability... yes
checking linux/ioctl.h presence... yes
checking for linux/ioctl.h... yes
checking linux/joystick.h usability... yes
checking linux/joystick.h presence... yes
checking for linux/joystick.h... yes
checking linux/major.h usability... yes
checking linux/major.h presence... yes
checking for linux/major.h... yes
checking linux/param.h usability... yes
checking linux/param.h presence... yes
checking for linux/param.h... yes
checking linux/serial.h usability... yes
checking linux/serial.h presence... yes
checking for linux/serial.h... yes
checking linux/types.h usability... yes
checking linux/types.h presence... yes
checking for linux/types.h... yes
checking linux/ucdrom.h usability... no
checking linux/ucdrom.h presence... no
checking for linux/ucdrom.h... no
checking lwp.h usability... no
checking lwp.h presence... no
checking for lwp.h... no
checking mach-o/nlist.h usability... no
checking mach-o/nlist.h presence... no
checking for mach-o/nlist.h... no
checking mach-o/loader.h usability... no
checking mach-o/loader.h presence... no
checking for mach-o/loader.h... no
checking mach/mach.h usability... no
checking mach/mach.h presence... no
checking for mach/mach.h... no
checking mach/machine.h usability... no
checking mach/machine.h presence... no
checking for mach/machine.h... no
checking machine/cpu.h usability... no
checking machine/cpu.h presence... no
checking for machine/cpu.h... no
checking machine/limits.h usability... no
checking machine/limits.h presence... no
checking for machine/limits.h... no
checking machine/sysarch.h usability... no
checking machine/sysarch.h presence... no
checking for machine/sysarch.h... no
checking mntent.h usability... yes
checking mntent.h presence... yes
checking for mntent.h... yes
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/in_systm.h usability... yes
checking netinet/in_systm.h presence... yes
checking for netinet/in_systm.h... yes
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking netinet/tcp_fsm.h usability... no
checking netinet/tcp_fsm.h presence... no
checking for netinet/tcp_fsm.h... no
checking pcap/pcap.h usability... yes
checking pcap/pcap.h presence... yes
checking for pcap/pcap.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking port.h usability... no
checking port.h presence... no
checking for port.h... no
checking process.h usability... no
checking process.h presence... no
checking for process.h... no
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking sched.h usability... yes
checking sched.h presence... yes
checking for sched.h... yes
checking scsi/scsi.h usability... yes
checking scsi/scsi.h presence... yes
checking for scsi/scsi.h... yes
checking scsi/scsi_ioctl.h usability... yes
checking scsi/scsi_ioctl.h presence... yes
checking for scsi/scsi_ioctl.h... yes
checking scsi/sg.h usability... yes
checking scsi/sg.h presence... yes
checking for scsi/sg.h... yes
checking stdbool.h usability... yes
checking stdbool.h presence... yes
checking for stdbool.h... yes
checking for stdint.h... (cached) yes
checking stropts.h usability... yes
checking stropts.h presence... yes
checking for stropts.h... yes
checking sys/asoundlib.h usability... yes
checking sys/asoundlib.h presence... yes
checking for sys/asoundlib.h... yes
checking sys/attr.h usability... no
checking sys/attr.h presence... no
checking for sys/attr.h... no
checking sys/auxv.h usability... yes
checking sys/auxv.h presence... yes
checking for sys/auxv.h... yes
checking sys/cdio.h usability... no
checking sys/cdio.h presence... no
checking for sys/cdio.h... no
checking sys/elf32.h usability... no
checking sys/elf32.h presence... no
checking for sys/elf32.h... no
checking sys/epoll.h usability... yes
checking sys/epoll.h presence... yes
checking for sys/epoll.h... yes
checking sys/event.h usability... no
checking sys/event.h presence... no
checking for sys/event.h... no
checking sys/exec_elf.h usability... no
checking sys/exec_elf.h presence... no
checking for sys/exec_elf.h... no
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/inotify.h usability... yes
checking sys/inotify.h presence... yes
checking for sys/inotify.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/ipc.h usability... yes
checking sys/ipc.h presence... yes
checking for sys/ipc.h... yes
checking sys/limits.h usability... no
checking sys/limits.h presence... no
checking for sys/limits.h... no
checking sys/link.h usability... no
checking sys/link.h presence... no
checking for sys/link.h... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/modem.h usability... no
checking sys/modem.h presence... no
checking for sys/modem.h... no
checking sys/msg.h usability... yes
checking sys/msg.h presence... yes
checking for sys/msg.h... yes
checking sys/mtio.h usability... yes
checking sys/mtio.h presence... yes
checking for sys/mtio.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking sys/prctl.h usability... yes
checking sys/prctl.h presence... yes
checking for sys/prctl.h... yes
checking sys/protosw.h usability... no
checking sys/protosw.h presence... no
checking for sys/protosw.h... no
checking sys/ptrace.h usability... yes
checking sys/ptrace.h presence... yes
checking for sys/ptrace.h... yes
checking sys/queue.h usability... yes
checking sys/queue.h presence... yes
checking for sys/queue.h... yes
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking sys/scsiio.h usability... no
checking sys/scsiio.h presence... no
checking for sys/scsiio.h... no
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking sys/signal.h usability... yes
checking sys/signal.h presence... yes
checking for sys/signal.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/socketvar.h usability... yes
checking sys/socketvar.h presence... yes
checking for sys/socketvar.h... yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking sys/strtio.h usability... no
checking sys/strtio.h presence... no
checking for sys/strtio.h... no
checking sys/syscall.h usability... yes
checking sys/syscall.h presence... yes
checking for sys/syscall.h... yes
checking sys/sysinfo.h usability... yes
checking sys/sysinfo.h presence... yes
checking for sys/sysinfo.h... yes
checking sys/tihdr.h usability... no
checking sys/tihdr.h presence... no
checking for sys/tihdr.h... no
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/timeout.h usability... no
checking sys/timeout.h presence... no
checking for sys/timeout.h... no
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking sys/user.h usability... yes
checking sys/user.h presence... yes
checking for sys/user.h... yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking sys/vnode.h usability... no
checking sys/vnode.h presence... no
checking for sys/vnode.h... no
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking syscall.h usability... yes
checking syscall.h presence... yes
checking for syscall.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking valgrind/memcheck.h usability... no
checking valgrind/memcheck.h presence... no
checking for valgrind/memcheck.h... no
checking valgrind/valgrind.h usability... no
checking valgrind/valgrind.h presence... no
checking for valgrind/valgrind.h... no
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking sys/mkdev.h usability... no
checking sys/mkdev.h presence... no
checking for sys/mkdev.h... no
checking sys/sysmacros.h usability... yes
checking sys/sysmacros.h presence... yes
checking for sys/sysmacros.h... yes
checking whether stat file-mode macros are broken... no
checking for sys/mount.h... yes
checking for sys/statfs.h... yes
checking for sys/sysctl.h... yes
checking for sys/user.h... (cached) yes
checking for sys/vfs.h... yes
checking for netinet/ip.h... yes
checking for net/if.h... yes
checking for net/if_arp.h... yes
checking for net/if_dl.h... no
checking for net/if_types.h... no
checking for net/route.h... yes
checking for netinet/if_ether.h... yes
checking for netinet/if_inarp.h... no
checking for netinet/in_pcb.h... no
checking for netinet/ip_icmp.h... yes
checking for netinet/ip_var.h... no
checking for netinet/udp.h... yes
checking for netipx/ipx.h... yes
checking for sys/un.h... yes
checking for netinet/tcp_timer.h... no
checking for netinet/udp_var.h... no
checking for netinet/icmp_var.h... no
checking for netinet/tcp_var.h... no
checking for linux/ipx.h... yes
checking for linux/irda.h... yes
checking for linux/rtnetlink.h... yes
checking for mach-o/dyld_images.h... no
checking for resolv.h... yes
checking for ifaddrs.h... yes
checking for sys/ucontext.h... yes
checking for sys/thr.h... no
checking for pthread_np.h... no
checking for linux/videodev.h... no
checking for linux/videodev2.h... yes
checking for libv4l1.h... yes
checking for libprocstat.h... no
checking attr/xattr.h usability... no
checking attr/xattr.h presence... no
checking for attr/xattr.h... no
checking sys/extattr.h usability... no
checking sys/extattr.h presence... no
checking for sys/extattr.h... no
checking sys/xattr.h usability... yes
checking sys/xattr.h presence... yes
checking for sys/xattr.h... yes
checking for ldd... /usr/bin/ldd
checking for otool... no
checking for readelf... readelf
checking whether we can build a GNU style ELF dll... yes
checking whether the compiler supports -fPIC -shared -Wl,-soname,confest.so.1... yes
checking whether the compiler supports -fPIC -shared -Wl,--version-script=conftest.map... yes
checking whether the compiler supports -fPIC -Wl,--export-dynamic... yes
checking whether the compiler supports -fPIC -Wl,--rpath,$ORIGIN/../lib... yes
checking whether the compiler supports -Wl,--enable-new-dtags... yes
checking whether the compiler supports -Wl,-Ttext-segment=0x7bc00000... yes
checking whether the compiler supports -Wl,-z,max-page-size=0x1000... yes
checking for x86_64-pc-mingw32-gcc... no
checking for amd64-pc-mingw32-gcc... no
checking for x86_64-w64-mingw32-gcc... no
checking for amd64-w64-mingw32-gcc... no
checking for x86_64-mingw32msvc-gcc... no
checking for amd64-mingw32msvc-gcc... no
checking for x86_64-w64-mingw32-clang... no
checking for amd64-w64-mingw32-clang... no
checking for pthread_create... no
checking for pthread_create in -lpthread... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for -lX11... libX11.so.6
checking for -lXext... libXext.so.6
checking for X11/Xlib.h... yes
checking for X11/XKBlib.h... yes
checking for X11/Xutil.h... yes
checking for X11/Xcursor/Xcursor.h... yes
checking for X11/extensions/shape.h... yes
checking for X11/extensions/XInput.h... yes
checking for X11/extensions/XInput2.h... yes
checking for X11/extensions/XShm.h... yes
checking for X11/extensions/Xcomposite.h... yes
checking for X11/extensions/Xfixes.h... yes
checking for X11/extensions/Xinerama.h... yes
checking for X11/extensions/Xrandr.h... yes
checking for X11/extensions/Xrender.h... yes
checking for X11/extensions/xf86vmode.h... yes
checking for X11/extensions/xf86vmproto.h... yes
checking for XkbQueryExtension in -lX11... yes
checking for -lXcursor... libXcursor.so.1
checking for -lXi... libXi.so.6
checking for XShmQueryExtension in -lXext... yes
checking for XShapeQueryExtension in -lXext... yes
checking for -lXxf86vm... libXxf86vm.so.1
checking for -lXrender... libXrender.so.1
checking for XRenderSetPictureTransform in -lXrender... yes
checking for XRenderCreateLinearGradient in -lXrender... yes
checking for -lXrandr... libXrandr.so.2
checking for -lXfixes... libXfixes.so.3
checking for -lXinerama... libXinerama.so.1
checking for -lXcomposite... libXcomposite.so.1
checking for XICCallback.callback... yes
checking for XEvent.xcookie... yes
checking for -lGL... not found
checking for -lGL... not found
checking for -lGLU... libGLU.so.1
checking for -lOSMesa... libOSMesa.so.8
checking va/va_x11.h usability... yes
checking va/va_x11.h presence... yes
checking for va/va_x11.h... yes
checking va/va_drm.h usability... yes
checking va/va_drm.h presence... yes
checking for va/va_drm.h... yes
checking for -lva... libva.so.2
checking for -lva-x11... libva-x11.so.2
checking for -lva-drm... libva-drm.so.2
checking for clGetPlatformInfo in -lOpenCL... yes
checking for -lpcap... libpcap.so.0.8
checking libxml/parser.h usability... yes
checking libxml/parser.h presence... yes
checking for libxml/parser.h... yes
checking libxml/xmlsave.h usability... yes
checking libxml/xmlsave.h presence... yes
checking for libxml/xmlsave.h... yes
checking libxml/SAX2.h usability... yes
checking libxml/SAX2.h presence... yes
checking for libxml/SAX2.h... yes
checking for xmlParseMemory in -lxml2... yes
checking for xmlReadMemory in -lxml2... yes
checking for xmlNewDocPI in -lxml2... yes
checking for xmlSchemaSetParserStructuredErrors in -lxml2... yes
checking for xmlSchemaSetValidStructuredErrors in -lxml2... yes
checking for xmlFirstElementChild in -lxml2... yes
checking for xmlDocProperties... yes
checking for libxslt/pattern.h... yes
checking for libxslt/transform.h... yes
checking for -lxslt... libxslt.so.1
checking dbus/dbus.h usability... yes
checking dbus/dbus.h presence... yes
checking for dbus/dbus.h... yes
checking for -ldbus-1... libdbus-1.so.3
checking hal/libhal.h usability... no
checking hal/libhal.h presence... no
checking for hal/libhal.h... no
checking gnutls/gnutls.h usability... yes
checking gnutls/gnutls.h presence... yes
checking for gnutls/gnutls.h... yes
checking for -lgnutls... libgnutls.so.30
checking for gnutls_cipher_init... yes
checking for -lncurses... libncurses.so.5
checking for mousemask... yes
checking sane/sane.h usability... yes
checking sane/sane.h presence... yes
checking for sane/sane.h... yes
checking for -lsane... libsane.so.1
checking for -lv4l1... libv4l1.so.0
checking gphoto2-camera.h usability... yes
checking gphoto2-camera.h presence... yes
checking for gphoto2-camera.h... yes
checking for gp_camera_new in -lgphoto2... yes
checking gphoto2-port.h usability... yes
checking gphoto2-port.h presence... yes
checking for gphoto2-port.h... yes
checking for gp_port_info_list_new in -lgphoto2_port... yes
checking for resolver library... -lresolv
checking lcms2.h usability... yes
checking lcms2.h presence... yes
checking for lcms2.h... yes
checking for cmsOpenProfileFromFile in -llcms2... yes
checking gtk/gtk.h usability... yes
checking gtk/gtk.h presence... yes
checking for gtk/gtk.h... yes
checking for -lgobject-2.0... libgobject-2.0.so.0
checking for -lcairo... libcairo.so.2
checking for -lgtk-3... libgtk-3.so.0
checking ft2build.h usability... yes
checking ft2build.h presence... yes
checking for ft2build.h... yes
checking for -lfreetype... libfreetype.so.6
checking for FT_TrueTypeEngineType... yes
checking for parport header/ppdev.h... yes
checking for pthread_attr_get_np... no
checking for pthread_getattr_np... yes
checking for pthread_getthreadid_np... no
checking for pthread_get_stackaddr_np... no
checking for pthread_get_stacksize_np... no
checking for inflate in -lz... yes
checking pulse/pulseaudio.h usability... yes
checking pulse/pulseaudio.h presence... yes
checking for pulse/pulseaudio.h... yes
checking for pa_stream_is_corked in -lpulse... yes
checking gst/gst.h usability... yes
checking gst/gst.h presence... yes
checking for gst/gst.h... yes
checking whether gint64 defined by gst/gst.h is indeed 64-bit... yes
checking for gst_pad_new in -lgstreamer-1.0... yes
checking for snd_pcm_hw_params_get_access_mask in -lasound... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking for oss_sysinfo.numaudioengines... yes
checking libudev.h usability... yes
checking libudev.h presence... yes
checking for libudev.h... yes
checking for udev_new in -ludev... yes
checking SDL2/SDL.h usability... yes
checking SDL2/SDL.h presence... yes
checking for SDL2/SDL.h... yes
checking for -lSDL2... libSDL2-2.0.so.0
checking for capi20.h... yes
checking for linux/capi.h... yes
checking for -lcapi20... libcapi20.so.3
checking cups/cups.h usability... yes
checking cups/cups.h presence... yes
checking for cups/cups.h... yes
checking cups/ppd.h usability... yes
checking cups/ppd.h presence... yes
checking for cups/ppd.h... yes
checking for -lcups... libcups.so.2
checking fontconfig/fontconfig.h usability... yes
checking fontconfig/fontconfig.h presence... yes
checking for fontconfig/fontconfig.h... yes
checking for -lfontconfig... libfontconfig.so.1
checking for -lgsm... libgsm.so.1
checking krb5/krb5.h usability... yes
checking krb5/krb5.h presence... yes
checking for krb5/krb5.h... yes
checking for -lkrb5... libkrb5.so.3
checking gssapi/gssapi.h usability... yes
checking gssapi/gssapi.h presence... yes
checking for gssapi/gssapi.h... yes
checking gssapi/gssapi_ext.h usability... yes
checking gssapi/gssapi_ext.h presence... yes
checking for gssapi/gssapi_ext.h... yes
checking for -lgssapi_krb5... libgssapi_krb5.so.2
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for -ljpeg... libjpeg.so.8
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for -lpng... libpng16.so.16
checking tiffio.h usability... yes
checking tiffio.h presence... yes
checking for tiffio.h... yes
checking for -ltiff... libtiff.so.5
checking for -ltxc_dxtn... not found
checking mpg123.h usability... yes
checking mpg123.h presence... yes
checking for mpg123.h... yes
checking for mpg123_feed in -lmpg123... yes
checking for -lopenal... libopenal.so.1
checking for openal-soft... yes
checking for -lodbc... libodbc.so.2
checking for -lnetapi... not found
checking for -lvulkan... libvulkan.so.1
checking for -lvkd3d... not found
checking for gcc strength-reduce bug... no
checking whether the compiler supports -fno-builtin... yes
checking whether the compiler supports -fno-strict-aliasing... yes
checking whether the compiler supports -fexcess-precision=standard... yes
checking whether the compiler supports -Werror=unknown-warning-option... no
checking whether the compiler supports -Wdeclaration-after-statement... yes
checking whether the compiler supports -Wempty-body... yes
checking whether the compiler supports -Wignored-qualifiers... yes
checking whether the compiler supports -Wpacked-not-aligned... no
checking whether the compiler supports -Wpragma-pack... no
checking whether the compiler supports -Wshift-overflow=2... yes
checking whether the compiler supports -Wstrict-prototypes... yes
checking whether the compiler supports -Wtype-limits... yes
checking whether the compiler supports -Wunused-but-set-parameter... yes
checking whether the compiler supports -Wvla... yes
checking whether the compiler supports -Wwrite-strings... yes
checking whether the compiler supports -Wpointer-arith... yes
checking for broken string.h that generates warnings with -Wpointer-arith... no
checking whether the compiler supports -Wlogical-op... yes
checking for broken string.h that generates warnings with -Wlogical-op... no
checking whether the compiler supports -gdwarf-2... yes
checking whether the compiler supports -gstrict-dwarf... yes
checking for ms_hook_prologue attribute... yes
checking for the need to disable Fortify... yes
checking whether external symbols need an underscore prefix... no
checking how to define a function in assembly code... .type @function
checking whether asm() works outside of functions... yes
checking whether .previous is supported in assembly code... yes
checking whether CFI directives are supported in assembly code... yes
checking for __res_get_state... no
checking for __res_getservers... no
checking for _finite... no
checking for _isnan... no
checking for _pclose... no
checking for _popen... no
checking for _snprintf... no
checking for _spawnvp... no
checking for _strdup... no
checking for _stricmp... no
checking for _strnicmp... no
checking for _strtoi64... no
checking for _strtoui64... no
checking for _vsnprintf... no
checking for asctime_r... yes
checking for chsize... no
checking for dlopen... no
checking for epoll_create... yes
checking for ffs... yes
checking for finitef... yes
checking for fnmatch... yes
checking for fork... yes
checking for fpclass... no
checking for fstatfs... yes
checking for fstatvfs... yes
checking for ftruncate... yes
checking for futimens... yes
checking for futimes... yes
checking for futimesat... yes
checking for getattrlist... no
checking for getauxval... yes
checking for getifaddrs... yes
checking for getopt_long_only... yes
checking for getpwuid... yes
checking for gettimeofday... yes
checking for getuid... yes
checking for isnanf... yes
checking for kqueue... no
checking for lstat... yes
checking for memmove... yes
checking for mmap... yes
checking for pclose... yes
checking for pipe2... yes
checking for poll... yes
checking for popen... yes
checking for port_create... no
checking for prctl... yes
checking for pread... yes
checking for proc_pidinfo... no
checking for pwrite... yes
checking for readdir... yes
checking for readlink... yes
checking for sched_yield... yes
checking for select... yes
checking for setproctitle... no
checking for setprogname... no
checking for setrlimit... yes
checking for settimeofday... yes
checking for sigaltstack... yes
checking for sigprocmask... yes
checking for snprintf... yes
checking for statfs... yes
checking for statvfs... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for strnlen... yes
checking for strtold... yes
checking for strtoll... yes
checking for strtoull... yes
checking for symlink... yes
checking for sysinfo... yes
checking for tcdrain... yes
checking for thr_kill2... no
checking for timegm... yes
checking for usleep... yes
checking for vsnprintf... yes
checking for dlopen in -ldl... yes
checking for dladdr... yes
checking for library containing gethostbyname... none required
checking for library containing connect... none required
checking for library containing inet_aton... none required
checking for getaddrinfo... yes
checking for getnameinfo... yes
checking for getnetbyname... yes
checking for getprotobyname... yes
checking for getprotobynumber... yes
checking for getservbyport... yes
checking for inet_addr... yes
checking for inet_network... yes
checking for inet_ntop... yes
checking for inet_pton... yes
checking for sendmsg... yes
checking for socketpair... yes
checking for library containing clock_gettime... none required
checking ldap.h usability... yes
checking ldap.h presence... yes
checking for ldap.h... yes
checking lber.h usability... yes
checking lber.h presence... yes
checking for lber.h... yes
checking for LDAPSortKey... yes
checking for ldap_initialize in -lldap_r... yes
checking for ber_init in -llber... yes
checking for ldap_count_references... yes
checking for ldap_first_reference... yes
checking for ldap_next_reference... yes
checking for ldap_parse_reference... yes
checking for ldap_parse_sort_control... no
checking for ldap_parse_sortresponse_control... yes
checking for ldap_parse_vlv_control... no
checking for ldap_parse_vlvresponse_control... yes
checking whether mkdir takes only one argument... no
checking for sched_setaffinity... yes
checking for fallocate... yes
checking for inline... inline
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for ssize_t... yes
checking for long long... yes
checking for fsblkcnt_t... yes
checking for fsfilcnt_t... yes
checking for sigset_t... yes
checking for request_sense... no
checking for struct xinpgen... no
checking for struct r_debug... yes
checking for struct link_map... yes
checking for struct ff_effect.direction... yes
checking for if_nameindex... yes
checking for sigaddset... yes
checking whether we can use re-entrant gethostbyname_r Linux style... yes
checking whether linux/joystick.h uses the Linux 2.2+ API... yes
checking for struct statfs.f_bfree... yes
checking for struct statfs.f_bavail... yes
checking for struct statfs.f_frsize... yes
checking for struct statfs.f_ffree... yes
checking for struct statfs.f_favail... no
checking for struct statfs.f_namelen... yes
checking for struct statvfs.f_blocks... yes
checking for struct dirent.d_reclen... yes
checking for struct msghdr.msg_accrights... no
checking for struct sockaddr.sa_len... no
checking for struct sockaddr_un.sun_len... no
checking for scsireq_t.cmd... no
checking for sg_io_hdr_t.interface_id... yes
checking for siginfo_t.si_fd... yes
checking for struct mtget.mt_blksiz... no
checking for struct mtget.mt_gstat... yes
checking for struct mtget.mt_blkno... yes
checking for struct option.name... yes
checking for struct stat.st_blocks... yes
checking for struct stat.st_mtim... yes
checking for struct stat.st_mtimespec... no
checking for struct stat.st_ctim... yes
checking for struct stat.st_ctimespec... no
checking for struct stat.st_atim... yes
checking for struct stat.st_atimespec... no
checking for struct stat.st_birthtime... no
checking for struct stat.st_birthtim... no
checking for struct stat.st_birthtimespec... no
checking for struct stat.__st_birthtime... no
checking for struct stat.__st_birthtim... no
checking for struct sockaddr_in6.sin6_scope_id... yes
checking for struct __res_state... yes
checking for struct __res_state._u._ext.nscount6... yes
checking for ns_msg._msg_ptr... yes
checking for struct icmpstat.icps_inhist... no
checking for struct icmpstat.icps_outhist... no
checking for struct ipstat.ips_total... no
checking for struct ip_stats.ips_total... no
checking for struct tcpstat.tcps_connattempt... no
checking for struct tcp_stats.tcps_connattempt... no
checking for struct udpstat.udps_ipackets... no
checking for struct ifreq.ifr_hwaddr... yes
checking for timezone variable... yes
checking for daylight variable... yes
checking for isfinite... yes
checking for isinf... yes
checking for isnan... yes
checking for acosh... yes
checking for acoshf... yes
checking for asinh... yes
checking for asinhf... yes
checking for atanh... yes
checking for atanhf... yes
checking for cbrt... yes
checking for cbrtf... yes
checking for erf... yes
checking for erfc... yes
checking for erfcf... yes
checking for erff... yes
checking for exp2... yes
checking for exp2f... yes
checking for expm1... yes
checking for expm1f... yes
checking for j0... yes
checking for j1... yes
checking for jn... yes
checking for lgamma... yes
checking for lgammaf... yes
checking for llrint... yes
checking for llrintf... yes
checking for llround... yes
checking for llroundf... yes
checking for log1p... yes
checking for log1pf... yes
checking for log2... yes
checking for log2f... yes
checking for lrint... yes
checking for lrintf... yes
checking for lround... yes
checking for lroundf... yes
checking for nearbyint... yes
checking for nearbyintf... yes
checking for powl... yes
checking for remainder... yes
checking for remainderf... yes
checking for rint... yes
checking for rintf... yes
checking for round... yes
checking for roundf... yes
checking for trunc... yes
checking for truncf... yes
checking for y0... yes
checking for y1... yes
checking for yn... yes
checking for __builtin_clz... yes
checking for __builtin_ctzl... yes
checking for __builtin_popcount... yes
checking for __clear_cache... yes
checking whether we need to define __x86_64__... no
creating Makefile rules... done
configure: creating ./config.status
config.status: creating Make.tmp
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: linking tools/winewrapper to wine
config.status: linking tools/winewrapper to wine64
config.status: executing include/stamp-h commands
config.status: executing tools/makedep commands
config.status: executing Makefile commands


configure: libhal 64-bit development files not found, no legacy dynamic device support.
configure: vkd3d 64-bit development files not found, Direct3D 12 won't be supported.


configure: WARNING: No OpenGL library found on this system.
OpenGL and Direct3D won't be supported.

```


Best,
David Brooks

---

