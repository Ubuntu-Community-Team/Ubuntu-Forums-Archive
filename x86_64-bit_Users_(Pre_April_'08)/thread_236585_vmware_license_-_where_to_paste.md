---
title: "vmware license - where to paste?"
date: 2006-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by xwing on 2006-08-15
I recently downloaded and installed vmware server (free edition) on my Ubuntu Dapper system. During the command-line install, it asked me for a license, which I didn't have at that point, so I skipped the step. After the installation, I generated the license from the vmware website and launched the vmware console and tried to paste my license into the 'Enter serial...' menu option. But it gave me a dialog box saying that I didn't have permissions to install a license and that I should contact an administrator.
 
Next I tried launching the vmware console as root, but that menu option was disabled when running as root. Could someone guide me as to where I can paste my vmware linux license key? I can't initialize any virtual machines as a result of this.

---

### Post by Stephen Robertson on 2006-08-15
Re-run vmware-config.pl.  Type sudo /usr/bin/vmware-config.pl and when the script asks if you want to enter a serial number, type yes.  The script will then prompt you for the serial number.

;)

---

### Post by xwing on 2006-08-15
Thanks Stephen. That did it.

---

