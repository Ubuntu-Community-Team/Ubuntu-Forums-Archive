---
title: "Evolution segfaults (again) after latest update"
date: 2008-12-01
forum: x86 64-bit Users
---

### Post by Lerxst on 2008-12-01
It seems like updating Evolution or not when update-manager tells you an update is available, is a risky process depending on if you want a working email client/suite afterwards. Updating Evolution has more or less constantly brought one of the following problems:

1) Filters that's not working
2) Evolution segfaults
3) Evolution floods you with it losing contact with the Exchange-backend messages and must be restarted

After updating Evolution this morning, a combination of 2 & 3 is happening. I updated it to 2.24.2 after the blurb said it fixes a memory leak ("hey, that's useful!" I thought), and afterwards Evolution, on one particular folder when it refreshes it, generates the following error in /var/log/messages: "Dec  1 13:33:22 server kernel: [15471.973693] evolution-excha[17808]: segfault at 0 ip 00007fe507136360 sp 00007fff17c7e168 error 4 in libglib-2.0.so.0.1800.2[7fe5070da000+c3000]"

And then abruptly tells me it has lost contact with the Exchange-backend.
This happens when the refresh reaches 100%, and starting Evolution from the CLI reveals " Error syncing up the counts
(evolution:17949): evolution-mail-WARNING **: Failed to refresh folders: Lost connection to Evolution Exchange backend process"

I didn't notice if glib was updated too - I guess it is since it seems to be the culprit, but does anyone else experience this problem?

I've tried deleting the summary and summary-meta files for that particular folder, even the cache. Also disabled all plugins, but it still crashes. Not a particularily large folder either.
If I untick check for new messages in all folder, I can get Evolution to work, even though I manually have to click on each folder to get them updated.

Very annoying, sometimes I have the impression they don't test Evolution **at all** before they release a new update. Especially considering all those countless times filters don't work and have to be applied manually.

Ubuntu Intrepid 8.10, x64 dual-core e2200 with 2GB RAM.

---

### Post by rimbaud on 2009-01-05
Updating Evolution is indeed a lottery, especially where connecting to Exchange is concerned.  I just don't understand how they so often release code that crashes or doesn't work properly.  There should be a serious feature freeze until they fix their years old bugs.

I had the nightmare "syncing up the counts" problem: I finally fixed it by creating a new Exchange email account.  This kept most of my settings but the filters now don't work properly.  A misleading message like "no email provider" actually means it is confused because folders are given a specific id on each account and it can't find the old filters.  Try as I might, I can't make this go away.

Anyone who says Evolution is a viable option for the Enterprise in conjunction with Exchange hasn't endured it for the last few years.

---

### Post by cepal on 2009-02-06
I have same problem as Lexrst with Evolution 2.24.1... Any idea? I was switching /home from XFS to EXT3 so I backed it up (by rsync over net) and then resotred and then, I have also chmoded my ~ (recursively) to "o-rwx", but that shouldn't mind as all is running under my credentials, rite?

CePal

---

### Post by lesser on 2009-11-03
Pfffffff, this is exactly my problem too. After the last update (a year after the start of this thread) I get the same sync error and a loss with backend. Evolution just manages to tell me there are 155 million messages in my inbox (which of course is a rediculous number, despite my huge popularity *cough-cough*).

I'll second the request for a feature freeze. Evolution is the one and only reason why I cannot recommend my colleagues to switch to Ubuntu.

I know beggars can't choose, but I'm begging for a decent mail client.

---

### Post by dcstar on 2009-11-06
> **lesser said:**
> Pfffffff, this is exactly my problem too. After the last update (a year after the start of this thread) I get the same sync error and a loss with backend. Evolution just manages to tell me there are 155 million messages in my inbox (which of course is a rediculous number, despite my huge popularity *cough-cough*).

I'll second the request for a feature freeze. Evolution is the one and only reason why I cannot recommend my colleagues to switch to Ubuntu.

I know beggars can't choose, but I'm begging for a decent mail client.

Many thousands of us use Evolution with no problem at all, the main problems I see reported are with Microsoft Exchange use where Evolution has to try and work with an essentially "moving target" by a vendor notorious for constantly changing things with little concern for "foreign" access to their systems.

If Evolution just gave up on trying to access Microsoft Exchange systems 95% of the complaints about it would probably disappear overnight as it became like most other non-Microsoft e-mail clients.

I have great sympathy for the Evolution developers trying to work with the Microsoft Exchange Webmail interface.

---

