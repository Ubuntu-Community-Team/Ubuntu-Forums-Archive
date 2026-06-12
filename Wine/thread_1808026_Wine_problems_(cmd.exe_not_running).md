---
title: "Wine problems (cmd.exe not running)"
date: 2011-07-19
forum: Wine
---

### Post by alexwi on 2011-07-19
Hi, 

I installed wine 1.2 and then went ahead and installed quickbooks 6 (yes umpteen years old version).

Then I installed a quickbooks update, which I need and at that point I got winevdm.exe errors. The update would not install.

I must have screwed up something royally, because cmd.exe, which worked before I did all this, stopped working and now, regardless of having uninstalled, purged, and manually deleted any remnants of wine and reinstalling (both from the repository and via terminal), cmd.exe doesn't work.

Also, now I don't have any wine shortcuts in the applications menu (I can add those manually, but strange things have definitely happened here).

This is with ubuntu 11.04 classic (I don't use Unity, if that's of any help).

Can someone please help?

Thanks!

Alex 520261

---

### Post by Unterseeboot_234 on 2012-12-09
I found your post searching for things quickbooks. I have successfully installed QB2006-Pro on 64-bit Ubuntu with wine and wine tricks. I then used wine uninstall to take off QB and installed the same setup on another AMD64 ubuntu. The person at the other workstation didn't want to do bookkeeping, so I came back to my personal ubuntu to re-install. 

I had to find the ./wine/drive_c/programs/quicken and any other quicken file and delete those (excepting my financial data files). Only after I did that could I re-run the cmd.exe.

A couple of notes: It is my opinion that vers. 2006 would be the last MFC based code instead of the silly dot-net way of making software. eHow.com also suggested vers. 2006 as the best choice to try in Ubuntu.

In QB2006-pro most things work. Pie charts have the center origin over on the left margin so the colored wedges don't fit into the pie slices. If a financial portfolio is set up, the dial-up will fetch the latest value of mutual funds, stocks, bonds AFTER I defeated online registration. I did have to defeat the registration --> online registration will kill the wine-wineTricks-QB2006 installation because Quicken wants you to upgrade.

My bank wants a recent QB to gain online banking within Quickbooks, so the wine-QB2006 cannot automatically track credit cards, checking, or bill-pay. I have to do those features manually and then use the bank's website which is not so bad, never more than 30 transactions a month.

You won't have any Help files because you cannot register an online version of QB2006.

All of the print reports work in QB2006 and the bank's loan officers were very pleased with our professional and believable financial statements.

So, I hope that helps you. I found it is a combination of experimentation.

---

