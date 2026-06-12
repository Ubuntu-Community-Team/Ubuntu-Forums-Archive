---
title: "ddo (pylotro) suddenly not working"
date: 2012-03-23
forum: Wine
---

### Post by buzzmandt on 2012-03-23
running pylotro in terminal gives me this after logging in
```
buzzmandt@buzzmandt-1:~$ pylotro
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/dist-packages/PyLotROLauncher/MainWindow.py", line 295, in txtPasswordEnter
    self.btnLoginClicked()
  File "/usr/local/lib/python2.7/dist-packages/PyLotROLauncher/MainWindow.py", line 289, in btnLoginClicked
    self.AuthAccount();
  File "/usr/local/lib/python2.7/dist-packages/PyLotROLauncher/MainWindow.py", line 306, in AuthAccount
    self.uiMain.txtPassword.text(), self.baseConfig.gameName, self.valHomeDir, self.osType)
  File "/usr/local/lib/python2.7/dist-packages/PyLotROLauncher/PyLotROUtils.py", line 532, in __init__
    if webresp.status == 500:
AttributeError: 'NoneType' object has no attribute 'status'

```

patching still seems to work but it after logging in it just hangs.

---

