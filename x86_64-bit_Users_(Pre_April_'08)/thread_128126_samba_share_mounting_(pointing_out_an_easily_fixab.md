---
title: "samba share mounting (pointing out an easily fixable issue)"
date: 2006-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonathan_c on 2006-02-10
I installed smb4k to mount samba shares and found that by default that it couldn't mount any share, it kept mumbling about needing suid root on smbmnt. So I set it using sudo chmod +s /usr/bin/smbmnt and it worked great. Then i proceeded to unmount the share and this time it complained about needing suid root on smbumount, so I did the magic step and it worked.

I'm guessing by default the programs smbmnt and smbumount don't have correct permissions when installed from the amd64 packages. Maybe this should be brought to the packagers attention. You folks have done a mighty fine job!

---

### Post by thekat on 2006-02-18
I had tihis problem also..
Thx for posting..

---

