---
title: "Partial Upgrade today?"
date: 2008-05-29
forum: x86 64-bit Users
---

### Post by s_spiff on 2008-05-29
Hi, 
I'm on a AMD64 Hardy Heron setup. Somehow I'm having and issue with the updates today. Its asking me to do a Partial Upgrade. I checked out the packages, and the ones that remain unselected are all Open Office Packages, and one python-uno package. 
The only non-official repo program I had installed was pidgin ( from get deb, version 2.4.1) and Wine from the repo provided on their site. That's about it. 
I've now reverted back to the old default sources.list and yet, I'm having the same issue. 
Can someone please tell me what to do in this situation?

Thanks,
Alok

---

### Post by Moop on 2008-05-29
I have the same situation. I don't have any non-official software installed but I do have backports enabled. I was able to install all the updates except the Open Office (7 or 8 of those) and the python-uno updates. Usually if you just wait a day or so these things get sorted out.

---

### Post by philinux on 2008-05-29
Just do this in a an hour. The updates are circulating the servers.
sudo apt-get update && sudo apt-get upgrade

---

### Post by Joeb454 on 2008-05-29
Do you have the "hardy-proposed" repo enabled? I got asked to do a partial upgrade earlier with that repo enabled :)

---

### Post by s_spiff on 2008-05-30
no hardy proposed repos enabled, medibuntu repos enabled. Well, the partial upgrade issue is still not resolved on my side. I did a sudo update re-enabled all the repos available from Sytem > Admin > Software Sources and still no respite from the issue! anyone?
[edit] 
When I did run the "upgrade" this is what i got :
> 
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.

This is really perplexing!

---

### Post by gracin on 2008-05-30
Same thing here.  Reporting "Partial Upgrade" in the last 24 hours.

---

### Post by IanW on 2008-05-30
Looks like the OpenOffice 2.4.1 packages are being held back until the existing OpenOffice 2.4.0 is uninstalled.

Synaptic's "Mark all upgrades" shows this much better.

So I'd suggest either updating via Synaptic, or running Update Manager again once it's done the partial upgrade.

---

### Post by s_spiff on 2008-05-30
Worked just fine. Presently downloading the updates. Thanks for the idea.

---

