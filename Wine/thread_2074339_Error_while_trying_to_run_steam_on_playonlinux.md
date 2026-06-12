---
title: "Error while trying to run steam on playonlinux"
date: 2012-10-21
forum: Wine
---

### Post by hfa2010 on 2012-10-21
I'm getting this error while trying to run Steam on Playonlinux:
 - Running wine-1.5.9 Steam.exe (Working directory : /home/henrique/.PlayOnLinux/wineprefix/TF2/drive_c/Program Files (x86)/Steam)
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: Não é possivel abrir arquivo de objetos compartilhado: fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 26/02/2012, dlt (d/m/y): 21/10/2012
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005140, 0x3f036b20, 0x3f036b18
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005140, 0x3f036b58, 0x3f036b50
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005140, 0x3f036ae8, 0x3f036ae0
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005140, 0x3f036b90, 0x3f036b88
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005140, 0x3f036bc8, 0x3f036bc0
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
libGL error: failed to load driver: i965
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  315
  Current serial number in output stream:  319

Anyone got some idea?



Update1= I solved it by running sudo apt-get install libgl1-mesa-dri:i386 but now my games that need 64 bit's libs aren't running! They seem to be faceing the same problem but now with 32 bit's instead of 64 libs... As they're finding the inverse libraries. How to fix this? I already tried reinstalling libgl1-mesa-driver:amd64 to fix but it didn't change nothing.

Update2 = Isn't there someway to force the application to use a certain path to the lib? Looking in the libgl verbose it shows that the application is trying to search on the 64 bits libs, rather than the i386 path. If at last it would search on an alternative way. The problem with this would be changing all the 64 bit's applications.

Update 3 = I just run this(Savage 2 need 64 bit's libs):  LIBGL_DEBUG=verbose ./savage2.bin
And got this
warning: The VAD has been replaced by a hack pending a complete rewrite
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
libGL error: dlopen /usr/lib/x86_64-linux-gnu/dri/i965_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/i965_dri.so: wrong ELF class: ELFCLASS32)
libGL: OpenDriver: trying ${ORIGIN}/dri/tls/i965_dri.so
libGL: OpenDriver: trying ${ORIGIN}/dri/i965_dri.so
libGL error: dlopen ${ORIGIN}/dri/i965_dri.so failed (${ORIGIN}/dri/i965_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/dri/i965_dri.so
libGL error: dlopen /usr/lib/dri/i965_dri.so failed (/usr/lib/dri/i965_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL error: dlopen /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so: wrong ELF class: ELFCLASS32)
libGL: OpenDriver: trying ${ORIGIN}/dri/tls/swrast_dri.so
libGL: OpenDriver: trying ${ORIGIN}/dri/swrast_dri.so
libGL error: dlopen ${ORIGIN}/dri/swrast_dri.so failed (${ORIGIN}/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
libGL error: dlopen /usr/lib/dri/swrast_dri.so failed (/usr/lib/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  24 (X_GLXCreateNewContext)
  Serial number of failed request:  49
  Current serial number in output stream:  66

Update 4 = Succeed in fixing the two libs problem but the game that i've tested(Savage 2) is freezing.

---

### Post by hfa2010 on 2012-10-28
bump

---

### Post by hfa2010 on 2012-10-29
Now aside the Savage 2 bug, now i'm having this two bugs, probably realated to GTK+, as Gimp color selecting display is ruined:
[IMG]http://ubuntuone.com/5eqrxMlO3r9lJAS6sEaIY3[/IMG]
Gimp error:
[IMG]http://ubuntuone.com/6nh7sW4dwWGVfREz8zXNXN[/IMG]

---

