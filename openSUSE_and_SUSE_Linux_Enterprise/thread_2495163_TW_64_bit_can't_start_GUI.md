---
title: "TW 64 bit can't start GUI"
date: 2024-02-09
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-02-09
```
Starting X Display manager
[...] [T...] bridge: filtering via arp/ip/ip6tables is no longer available...
[...] [T...] Bridge firewalling registered
```

After Ctrl-Alt-F2: only cursor visible
After Ctrl-Alt-F7: black screen

Any idea pls ?

---

### Post by maketopsite on 2024-02-11
> **mrmazda said:**
> Others reported problems several days ago too. Among reports were that a subsequent dup resolved reported issues. Last reported release was 20240208. Many packages were rebuilt this past week, making dups bigger and more complex than average. Try another dup by booting a prior kernel and/or booting to multi-user.target or after a Snapper rollback.

booting with 
```
systemd.unit=multi-user.target
```

kernel parameter and

```
zypper dup
``` has solved the problem.

---

