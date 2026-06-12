---
title: "Fault Packet Error Anytime Wine Closes"
date: 2024-03-25
forum: Wine
---

### Post by pakxos on 2024-03-25
Hello - getting an error any time wine runs:

00a0:err:rpc:I_RpcReceive we got fault packet with status 0x1c010003

Triggers whenever the process using wine terminates, so if I run wine explorer, when I close the window, the above error generates in the terminal.

While it doesn't seem to affect any actual processes so far, I would like to understand what is causing that error to occur in case it does cause a problem down the line.
Happy to provide additional information, but am just starting with linux/ubuntu.

Wine Info:
wine-6.0.3 (Ubuntu 6.0.3~repack-1)

Ubuntu info:

[B]Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy
[/B]
Thanks,

---

### Post by biledk on 2024-03-26
Hi Pakxos
No replies, let me try.
Is wine updated? Or try run older stable version.
Can't you use the winedebug?
As I remember there are winetrick that helps with versions / etc.

---

### Post by pakxos on 2024-03-27
I can try winedebug, but was hoping to get a sense of what usually causes that error. I believe wine-6.0.3 is the latest in the default ubuntu repository.

---

