---
title: "Updating Blizzard Update Agent [stuck]"
date: 2013-04-11
forum: Wine
---

### Post by michaeljwjr on 2013-04-11
Been scouring forums looking for this solution, and not finding it. I followed the wiki, all the right ports are open, downloaded the installer, run the installer, and it hangs at **Updating Blizzard Update Agent** and if I start it back up without deleting the Battle.net folder, I get **Checking for updates** stuck. 

Running Ubuntu 13.04, latest Wine, kernel 3.8.6

---

### Post by Tweak42 on 2013-04-11
If you haven't started from a clean prefix, I have in the past deleted the Agent in the /home/<username>/.wine/drive_c/users/Public/Application Data directory, then started the Updater again.  Also have you tried launching it from a terminal and see if there are any telling error messages?

---

### Post by michaeljwjr on 2013-04-11
```
fixme:iphlpapi:GetExtendedTcpTable ulAf = 2, TableClass = 5 not supporttedfixme:process:GetLogicalProcessorInformation (0xfee348,0xfee948): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x1b9e314,0x1b9e914): stub
fixme:process:GetLogicalProcessorInformation (0x1b9e2e4,0x1b9e8e4): stub
fixme:iphlpapi:GetExtendedTcpTable ulAf = 2, TableClass = 5 not supportted
fixme:process:GetLogicalProcessorInformation (0xfee348,0xfee948): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x1b9e314,0x1b9e914): stub
fixme:process:GetLogicalProcessorInformation (0x1b9e2e4,0x1b9e8e4): stub



```

---

### Post by michaeljwjr on 2013-04-11
Now this problem has been happening in windows, and the fix for the windows guys is for them to update to internet explorer 10, is that even an option for us?

---

### Post by michaeljwjr on 2013-04-12
I installed Crossover, and it installed WoW perfectly first time. Don't know what the difference is.

---

### Post by slipup on 2013-05-09
> **michaeljwjr said:**
> I installed Crossover, and it installed WoW perfectly first time. Don't know what the difference is.

Thanks that worked for me.

---

