---
title: "Any way to install skype web plugin through wine?"
date: 2015-11-10
forum: Wine
---

### Post by alex469 on 2015-11-10
Hi guys!

I wanna to install skype web plugin through wine but get a stuck with it. I'm sure than not only me want to try online skype instead of awful native linux client.

So here my story: I changed user agent on my browser to windows and downloaded SkypeWebPlugin. Then I run it through wine 

```
wine msiexec /i SkypeWebPlugin.msi
```

But I got this error:

```
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:advapi:EventRegister {5eec90ab-c022-44b2-a5dd-fd716a222a15}, 0x10001123, 0x1001d020, 0x1001d038
err:msi:ITERATE_Actions Execution halted, action L"CA_PreInstallChecks" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister 0: stub

```
If somebody have any suggestions, please, leave your thoughts here. Thanks!

Btw, if you have any tips how to make native linux client more pretty, share it here!

Good luck and have a nice day.

Cheers

---

### Post by alex_32 on 2015-11-12
Hi, 

About the thing to make skype prettier. If you have in mind that the linux skype client is not using your default theme and cursor then install the 32-bit libraries necessary for it to do that.

```
sudo apt-get install gtk2-engines-murrine:i386 gtk2-engines-pixbuf:i386
```

---

