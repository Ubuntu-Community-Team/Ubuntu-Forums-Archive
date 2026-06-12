---
title: "Workspace"
date: 2008-06-06
forum: x86 64-bit Users
---

### Post by BertDelRio on 2008-06-06
I noticed that Kubuntu's workspace are independent of each other. This is not the case with Ubuntu. An example is when you drag a window off-page, it appears in the workspace next to the one you are using.

Is there anyway this can be corrected? I would like to keep my workspaces independent of each other, specially when I do sales presentations.

---

### Post by vrangforestillinger on 2008-06-08
You can do this two ways as far as I know:
1.Disable desktop effects. You can do this in the Appereance-menu. The downside of this is that, well you disable the desktop-effects.
2.Install advanced compiz-settings. In a terminal:
```
sudo apt-get install compizconfig-settings-manager
```
Then
```
ccsm
```
Im using Norwegian version, so these might not be exact translations of the options but:
Go to Desktop->Desktop wall->Border switch. There you should be able to disable workspace switching when moving windows.

---

