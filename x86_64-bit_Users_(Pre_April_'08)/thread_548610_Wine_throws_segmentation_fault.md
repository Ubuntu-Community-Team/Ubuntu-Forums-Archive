---
title: "Wine throws segmentation fault"
date: 2007-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by lv1001 on 2007-09-11
I really need help,

I installed Wine on a _nearly_ clean 64bit Kubuntu Feisty system on a Macbook Pro from the wine repositories (following [this]("http://www.winehq.org/site/download-deb") guide) 
wineconfig throws the following:

```

lewin@mecki:~$ wineconfig
Segmentation fault (core dumped)
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\Software\Wine\Drives' does not exist!
Success

Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3547, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 118, in __init__
    self.CreateWindowsInstall()
  File "/usr/bin/wineconfig", line 318, in CreateWindowsInstall
    winewrite.SetDriveMappings(drives)
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/lewin/.wine/dosdevices/c:/windows/profiles/lewin'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3547, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 118, in __init__
    self.CreateWindowsInstall()
  File "/usr/bin/wineconfig", line 318, in CreateWindowsInstall
    winewrite.SetDriveMappings(drives)
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/usr/share/python-support/kde-guidance/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/lewin/.wine/dosdevices/c:/windows/profiles/lewin'

```
When I manually ad the directories
```
lewin@mecki:~$ mkdir /home/lewin/.wine/dosdevices/c\:/windows/profiles
lewin@mecki:~$ mkdir /home/lewin/.wine/dosdevices/c\:/windows/profiles/lewin

```
I go some further:
```

lewin@mecki:~$ wineconfig
Segmentation fault (core dumped)
regedit: Can't export. Registry key 'HKEY_USERS\.Default\Software\Microsoft\Windows\CurrentVersion\Explorer\Shell Folders' does not exist!
Success

regedit: Can't export. Registry key 'HKEY_USERS\.Default\Software\Microsoft\Windows\CurrentVersion\Explorer\Shell Folders' does not exist!
Success

regedit: Can't export. Registry key 'HKEY_USERS\.Default\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders' does not exist!
Success

regedit: Can't export. Registry key 'HKEY_CURRENT_USER\Control Panel\Desktop' does not exist!
Success

regedit: Can't export. Registry key 'HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\ThemeManager' does not exist!
Success

regedit: Can't export. Registry key 'HKEY_CURRENT_USER\Control Panel\Desktop\WindowMetrics' does not exist!
Success

Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3547, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 120, in __init__
    self._buildGUI()
  File "/usr/bin/wineconfig", line 213, in _buildGUI
    self.appearancepage = AppearancePage(appearance1page)
  File "/usr/bin/wineconfig", line 1812, in __init__
    self.reset()
  File "/usr/bin/wineconfig", line 1926, in reset
    self.__selectColorScheme(i)
  File "/usr/bin/wineconfig", line 2237, in __selectColorScheme
    self.__selectItem(unicode(i18n("Desktop")))
  File "/usr/bin/wineconfig", line 2417, in __selectItem
    self.customizableitems[item][0][key][0])
KeyError: u'Arbeitsfl\xe4che'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 3547, in <module>
    wineconfigapp = WineConfigApp()
  File "/usr/bin/wineconfig", line 120, in __init__
    self._buildGUI()
  File "/usr/bin/wineconfig", line 213, in _buildGUI
    self.appearancepage = AppearancePage(appearance1page)
  File "/usr/bin/wineconfig", line 1812, in __init__
    self.reset()
  File "/usr/bin/wineconfig", line 1926, in reset
    self.__selectColorScheme(i)
  File "/usr/bin/wineconfig", line 2237, in __selectColorScheme
    self.__selectItem(unicode(i18n("Desktop")))
  File "/usr/bin/wineconfig", line 2417, in __selectItem
    self.customizableitems[item][0][key][0])
KeyError: u'Arbeitsfl\xe4che'

```

Is wine really a 64 bit program or does it use some kind of 32 bit environment?
Google Earth gives a segmentation fault as well. Could it be some 32 bit libraries are not properly installed on my system?

Thanks in advance
  LV1001

---

### Post by kansei on 2007-09-13
I'm on Gutsy x64 and it seems as though there are no Wine packages still, so I'll have to assume it's because Wine isn't easily compatible.

restarting into windows to run minitab = :(

---

