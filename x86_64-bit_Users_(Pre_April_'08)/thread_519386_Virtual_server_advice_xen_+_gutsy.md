---
title: "Virtual server advice: xen + gutsy?"
date: 2007-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by PurpleFool on 2007-08-07
My "problem" is how to use a 4 proc opteron with plenty of memory.  It was in service previously as a SuSE(SLES10) box.  I had peripheral issues and ended up doing a CD less install and have a shiny Gutsy install.

I'd like to provide the SLES environment, just to show it's there,   and I went to add a couple of xen packages.  This failed as synaptic tells me that xen-hypervisor is not installable.

Yeah yeah, so NOW I'm asking for advice.  There's nothing in Gutsy, that I know of, that I'll need.  I set up the AFS and Kerberos packages necessary and  I'd like to throw around some builds, but it's not, quite, a personal workstation. :)

Would it "better" to move back to Feisty and use that?  And if so, will it be easier to re-install?  Or is the opteron/xen combination useful enough to Gutsy late testing to warrant a xen newb sticking with the current install.  In which case, what are my chances of making headway by simply pulling the source and trying to make packages in situ?

Thanks for your time and any help you can give.

---

### Post by Kilz on 2007-08-07
> **PurpleFool said:**
> My "problem" is how to use a 4 proc opteron with plenty of memory.  It was in service previously as a SuSE(SLES10) box.  I had peripheral issues and ended up doing a CD less install and have a shiny Gutsy install.

I'd like to provide the SLES environment, just to show it's there,   and I went to add a couple of xen packages.  This failed as synaptic tells me that xen-hypervisor is not installable.

Yeah yeah, so NOW I'm asking for advice.  There's nothing in Gutsy, that I know of, that I'll need.  I set up the AFS and Kerberos packages necessary and  I'd like to throw around some builds, but it's not, quite, a personal workstation. :)

Would it "better" to move back to Feisty and use that?  And if so, will it be easier to re-install?  Or is the opteron/xen combination useful enough to Gutsy late testing to warrant a xen newb sticking with the current install.  In which case, what are my chances of making headway by simply pulling the source and trying to make packages in situ?

Thanks for your time and any help you can give.

Gutsy is in Alpha testing right now. I don't recommend running it unless you are good at troubleshooting broken Ubuntu systems.. Things will break as development is done. Unless you are real comfortable with Ubuntu its just not a good idea. The purpose of the Alpha Gutsy releases is for testing to find bugs. Not to be depended upon not to break.
I would do a Feisty install. You will be able to easily upgrade to Gutsy when its released. But I would even put that off for a week or 2 to make sure no major bugs slip by. While it hasn't happened yet, we are all human.

---

### Post by PurpleFool on 2007-08-07
Thanks for the quick reply.  I realised, after installing, that I'd picked up a pre-release installer.  I was wondering whether someone actually trying to use xen was useful.  Sounds like you think it's all covered so I'm happy to back off to Feisty.

Is there a sanctioned way to downrev an installation of Ubuntu?  Or is a fresh install the only safe method?

Thanks again for the guidance.

---

