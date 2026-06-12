---
title: "Wine with real Windows DLLs?"
date: 2013-08-10
forum: Wine
---

### Post by arlesschill on 2013-08-10
Since Wine uses open source windows files could a user with windows import the DLLs and such to wine and replace the open source ones?

---

### Post by 1clue on 2013-08-10
This is called Crossover Office.  Or you can do it yourself, if you understand the licensing issues.

---

### Post by MikeCyber on 2013-08-11
winetricks will install all you need. No need to mess around...or simply use the windows installers.

---

### Post by Mark Phelps on 2013-08-12
> **arlesschill said:**
> Since Wine uses open source windows files could a user with windows import the DLLs and such to wine and replace the open source ones?

Wine uses DLLs that were rewritten by CodeWeavers to replace MS Windows OS calls with Linux OS calls.  Don't know that I would call these "open-source".

If you replace these with native MS Windows DLLs, Wine will no longer work.

Whether or not you can use other DLLs can only be determined by trial-and-error.

As mentioned, some Wine add-ons will download additional DLLs for you.

---

### Post by 1clue on 2013-08-12
Clarification:

Wine uses DLLs that were rewritten by people looking only at the API, which are open-source.  Mostly these are good enough to get some less complicated software to run.

CodeWeavers produces Crossover Office, which is Wine but uses genuine Windows DLLs to get some of the software that people really want working.  These are fully licensed (you pay a fee, some of which pays for your license to use the DLLs) and legal.

If you want something like Microsoft Office to work, then you will find that it's a lot easier to buy the Crossover Office product.

---

