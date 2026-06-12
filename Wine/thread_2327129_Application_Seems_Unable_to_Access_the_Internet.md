---
title: "Application Seems Unable to Access the Internet"
date: 2016-06-07
forum: Wine
---

### Post by Voc on 2016-06-07
Hey all,

I've been trying to install a game using wine, which claims to be easily installed on Ubuntu 16.04 according to WineHQ.  However, every time I try to run the installer the log gets stuck in the following loop:

```
20:40:13.629 [41]: [ERROR] [ArcInstall_STO_20151009a.exe](0) Download failed, need retry, waiting 5000 ms...20:40:48.815 [41]: [WARN] [CHTTPResponseHeader] [GetModifyTime] query ContentMD5 fail, [ERROR CODE] 12150
20:40:48.908 [60]: [ERROR] [CHTTPBlockDownload] [DownloadBlock] download file result = -1 
20:40:48.908 [60]: [WARN] [ArcInstall_STO_20151009a.exe](2) DownloadBlock (offset:524288, datalen:524288) failed, ret=12, RetryTime=1
20:40:49.47 [61]: [ERROR] [CHTTPBlockDownload] [DownloadBlock] download file result = -1 
20:40:49.47 [61]: [WARN] [ArcInstall_STO_20151009a.exe](1) DownloadBlock (offset:0, datalen:524288) failed, ret=12, RetryTime=1
20:40:49.47 [57]: [ERROR] [CHTTPBlockDownload] [DownloadBlock] download file result = -1 
20:40:49.47 [57]: [WARN] [ArcInstall_STO_20151009a.exe](5) DownloadBlock (offset:2097152, datalen:524288) failed, ret=12, RetryTime=1
20:40:49.168 [59]: [ERROR] [CHTTPBlockDownload] [DownloadBlock] download file result = -1 
20:40:49.168 [59]: [WARN] [ArcInstall_STO_20151009a.exe](3) DownloadBlock (offset:1048576, datalen:524288) failed, ret=12, RetryTime=1
20:40:49.170 [58]: [ERROR] [CHTTPBlockDownload] [DownloadBlock] download file result = -1 
20:40:49.170 [58]: [WARN] [ArcInstall_STO_20151009a.exe](4) DownloadBlock (offset:1572864, datalen:524288) failed, ret=12, RetryTime=1
20:40:49.218 [41]: [ERROR] [ArcInstall_STO_20151009a.exe](0) Download failed, Stopping Download threads(count:5)
20:40:49.248 [61]: [WARN] [ArcInstall_STO_20151009a.exe](1) DownloadBlock (offset:0, datalen:524288) failed, Stop by main thread, call ReturnSection
20:40:49.248 [57]: [WARN] [ArcInstall_STO_20151009a.exe](5) DownloadBlock (offset:2097152, datalen:524288) failed, Stop by main thread, call ReturnSection
20:40:49.269 [59]: [WARN] [ArcInstall_STO_20151009a.exe](3) DownloadBlock (offset:1048576, datalen:524288) failed, Stop by main thread, call ReturnSection
20:40:49.270 [58]: [WARN] [ArcInstall_STO_20151009a.exe](4) DownloadBlock (offset:1572864, datalen:524288) failed, Stop by main thread, call ReturnSection
20:40:49.309 [60]: [WARN] [ArcInstall_STO_20151009a.exe](2) DownloadBlock (offset:524288, datalen:524288) failed, Stop by main thread, call ReturnSection
20:40:49.311 [41]: [ERROR] [ArcInstall_STO_20151009a.exe](0) Download failed, need retry, waiting 5000 ms...
```

I'm not sure what it's telling me, or how I should go about correcting the problem.

Thanks,
Luke

---

### Post by Mark Phelps on 2016-06-12
My suggestion is to go to the WineHQ website, enter the game name and see what is displayed:  [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

If there are no ratings, or if the ratings are lower than Gold, you're wasting your time.

Good Luck

---

