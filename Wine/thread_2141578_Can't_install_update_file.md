---
title: "Can't install update file"
date: 2013-05-03
forum: Wine
---

### Post by skippy3111 on 2013-05-03
I'm running Ubuntu 13.04, and Wine 1.5.29. I'm trying to install Rosetta Stone 4.1.10 and then apply an update file 4.1.15.

The first file installs, but the update file fails. As soon as its launched an error pop up window shows. I'm having trouble attaching a screen shot of it. It's very similar text to what whes up when I tried "wine update_4.1.15.exe" in terminal. This came up:

err:msi:MsiEnableLogW Unable to enable log L"C:\\users\\as\\Temp\\RosettaStoneLtd_TEMP_update\\RS_V4_InstallLog.txt/passive" (3)
fixme:msi:MsiMessageBoxW (nil) L"Windows Installer 4.5.6001.22299\n\nUsage:\nmsiexec command {required parameter} [optional parameter]\n\nInstall a product:\n\t/i {package|product_code} [property]\n\t/package {package|product_code} [property]\n\t/a package [property]\nRepair an installation:\n\t/f[p|o|e|d|c|a|u|m|s|v] {package|produ"... (null) 0 00001009 00000000

This is what the log file contained: 
----------------Install Log-----------------
=onlineSpeechInstallation=

OnlineSpeechInstaller not run as it is not present
TOTALe Installer: aborting installation with error code 1

I'm guessing that the updater can't find the previous installation?

---

