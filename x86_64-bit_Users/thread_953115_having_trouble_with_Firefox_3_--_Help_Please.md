---
title: "having trouble with Firefox 3 -- Help Please"
date: 2008-10-19
forum: x86 64-bit Users
---

### Post by goldstar1 on 2008-10-19
I don't know what happened

When I open Firefox 3.0 up...

no home page unless I click on the house on the tool bar.

I cannot use the back or forward arrow, I'm stuck with typing into the URL box.

The bookmarks tool bar doesn't have any bookmarks -- They used to be there and work, but not anymore.

I'm running an x86_64 processor with 3 gig of memory, Ubuntu 8.04

**in the browser menu**

**>>Tools>>Error Console has this output...**

Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.3/components/libpyloader.so

Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.3/components/pyabout.py

Failed to load XPCOM component: /home/george/.mozilla/firefox/efiuvu8m.default/extensions/{2fa4ed95-0317-4c6a-a74c-5f3e3912c1f9}/components/build.sh

Error: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib/firefox-3.0.3/components/nsBrowserGlue.js :: bg__initPlaces :: line 389"  data: no]
Source File: file:///usr/lib/firefox-3.0.3/components/nsBrowserGlue.js
Line: 389

Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 763"  data: no]

---

### Post by Thelasko on 2008-10-20
Sounds like one of your extensions is the problem. (foxyproxy?)  Go through and remove them one by one and see if that fixes the problem.

If all else fails go to "/home/george/.mozilla" and delete the "firefox" folder.  Restart Firefox and see what happens. (hint: to view folders that start with "." you need to press ctrl+h.)

---

### Post by goldstar1 on 2008-10-20
It was on of the extensions in /home/geore/.mozilla...only I don't know which one. I removed everything that had the name 'Firefox' the reinstalled and now its working fine.

Thank you soo much for a quick reply

---

### Post by Thelasko on 2008-10-21
Glad I could help!  By the way, you can say thanks by simply clicking the gold medal icon in the lower right corner of the helpful post.

Please go to "thread tools" at the top of the page and mark this thread solved.  Thanks.

---

### Post by Vishal Agarwal on 2008-10-21
in terminal issue the command
 > firefox3 --profile-manager

it will start the profile manager, try creating new profile for you. If it works.

---

