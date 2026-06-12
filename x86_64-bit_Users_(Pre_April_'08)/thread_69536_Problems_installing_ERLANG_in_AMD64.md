---
title: "Problems installing ERLANG in AMD64"
date: 2005-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by tudense on 2005-09-27
Hello. I'm newbie in Linux and I'm having some problems.

I've been trying to install the  otp_src_R10B-7 but when I write "make" happens this:

carlos@Fenix:~/Desktop/APPS/otp_src_R10B-7$ make
cd erts/emulator && ERL_TOP=/home/carlos/Desktop/APPS/otp_src_R10B-7 make generate depend
make[1]: Entering directory `/home/carlos/Desktop/APPS/otp_src_R10B-7/erts/emulator'
make -f x86_64-unknown-linux-gnu/Makefile generate
make[2]: Entering directory `/home/carlos/Desktop/APPS/otp_src_R10B-7/erts/emulator'
make[2]: x86_64-unknown-linux-gnu/Makefile: No existe el fichero o el directorio
make[2]: *** No hay ninguna regla para construir el objetivo `x86_64-unknown-linux-gnu/Makefile'.  Alto.
make[2]: Leaving directory `/home/carlos/Desktop/APPS/otp_src_R10B-7/erts/emulator'
make[1]: *** [generate] Error 2
make[1]: Leaving directory `/home/carlos/Desktop/APPS/otp_src_R10B-7/erts/emulator'
make: *** [depend] Error 2
carlos@Fenix:~/Desktop/APPS/otp_src_R10B-7$


"No existe el fichero o el directorio" means that there is no file or folder
"No hay ninguna regla para construir el objetivo" means that there is no rule to build the target

I don't know what I do wrong. Thank you.

Best regards

---

