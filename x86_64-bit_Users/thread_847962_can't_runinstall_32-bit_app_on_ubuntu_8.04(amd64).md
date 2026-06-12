---
title: "can't run/install 32-bit app on ubuntu 8.04(amd64)"
date: 2008-07-03
forum: x86 64-bit Users
---

### Post by fasahat on 2008-07-03
Hi,

I moved from an older 32-bit fc5 by installing the 64-bit 8.04 ubuntu. 
Machine is AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
Release is Ubuntu 8.04 (hardy)
Kernel release is Ubuntu 8.04 (hardy)

I then installed the equivalent 64-bit applications. However, because of open motif library issue (only available in 32-bit), I was not able to run the old running app in 64-bit. I thus tried to run the 32-bit app in the new ubuntu OS, but I am getting this error.

root@fasahat:/tools/Xilinx/10.1/ISE/bin/lin# ./ise
bash: ./ise: No such file or directory
root@fasahat:/tools/Xilinx/10.1/ISE/bin/lin# ls -l ./ise
-rwxr-xr-x 1 root root 16068 2008-02-11 04:19 ./ise
root@fasahat:/tools/Xilinx/10.1/ISE/bin/lin# uname -a
Linux fasahat 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

As you may see from above, the file is there, but shell comes back with message "No such file or directory". Please note by default, the application setup installed both 64-bit and 32-bit executables

The same app runs ok on an old installed 64-bit fc5, both in 64-bit as well as 32-bit mode.

What do I add to make ubuntu run the 32-bit app on 64-bit?

Thanks for the reply in advance.

Fasahat

---

### Post by Kilz on 2008-07-03
> **fasahat said:**
> Hi,

I moved from an older 32-bit fc5 by installing the 64-bit 8.04 ubuntu. 
Machine is AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
Release is Ubuntu 8.04 (hardy)
Kernel release is Ubuntu 8.04 (hardy)

I then installed the equivalent 64-bit applications. However, because of open motif library issue (only available in 32-bit), I was not able to run the old running app in 64-bit. I thus tried to run the 32-bit app in the new ubuntu OS, but I am getting this error.

root@fasahat:/tools/Xilinx/10.1/ISE/bin/lin# ./ise
**bash: ./ise: No such file or directory**
root@fasahat:/tools/Xilinx/10.1/ISE/bin/lin# ls -l ./ise
-rwxr-xr-x 1 root root 16068 2008-02-11 04:19 ./ise
root@fasahat:/tools/Xilinx/10.1/ISE/bin/lin# uname -a
Linux fasahat 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

As you may see from above, the file is there, but shell comes back with message "No such file or directory". Please note by default, the application setup installed both 64-bit and 32-bit executables

The same app runs ok on an old installed 64-bit fc5, both in 64-bit as well as 32-bit mode.

What do I add to make ubuntu run the 32-bit app on 64-bit?

Thanks for the reply in advance.

Fasahat

My bold, it doesnt see the file, are you sure you are in the correct directory? If you are, is the permission set on the file to make it executable? Lastly, Why are you running as root?

---

### Post by Cappy on 2008-07-03
This kind of error occurs if you don't have ia32-libs installed so try
```
sudo apt-get install ia32-libs lib32nss-mdns
```

---

