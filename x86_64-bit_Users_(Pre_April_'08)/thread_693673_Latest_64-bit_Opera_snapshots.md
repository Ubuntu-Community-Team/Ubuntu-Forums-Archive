---
title: "Latest 64-bit Opera snapshots"
date: 2008-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by inphektion on 2008-02-11
[http://snapshot.opera.com/unix/snapshot-1800/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-1800/x86_64-linux/)

**New known Issues **
[LIST]
[*]Opera will not fetch more than 50 new IMAP messages in one go - you'll need to reset the account to get more. 
[*]Inline find stops working after entering one letter. (using Ctrl+F still works as expected). 
[*]Advanced tab activation currently does not work in the Mac and Linux builds.
[/LIST]

**Changelog** 
[LIST]
[*]Added a new preference in Preferences > Advanced > Tabs which controls which tab to activate when closing a tab. 
[*]Fixed crash when composing mail with empty signature 
[*]Fixed crtash when emptying history and VPS was disabled 
[*]css3 :target now works on targets identified using name attribute 
[*]New spatnav highlighting, similar to the one used in Opera Mini 4 and the Wii browser 
[*]iframes with contenteditable are now in in the tabbing order (Another gmail 2 fix) 
[*]64-bit: Again possible to open (image) attachments in mail 
[*]Some more improvement to fast forward. 
[*]Opera Link now works better when using Work offline 
[*]Again possible to open links from widgets 
[*]UNIX: Drag and drop now works properly in the ION window manager
[/LIST]

---

### Post by prince_niceguy on 2008-02-16
keeps crashing for me everytime i try to access any site with the latest release. will wait for some more time by te time beta comes...

---

### Post by Case_f on 2008-02-16
That's because the known issues posted here are not complete, there's more, including

"Plug-ins crash Opera on UNIX/Linux."

See here: [http://my.opera.com/desktopteam/blog/2008/02/11/introducing-advanced-tab-activation](http://my.opera.com/desktopteam/blog/2008/02/11/introducing-advanced-tab-activation)

---

### Post by inphektion on 2008-02-22
**New Release Today**
Plugins will no longer crash opera.  Get it here: [http://snapshot.opera.com/unix/snapshot-1823/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-1823/x86_64-linux/)
> 
This build demonstrates the plugin work that has been done recently. Most of this work is not visible and is only testable through regression testing: compare with an older build and see if something broke. ;) A lot of this work is cross-platform, so we would appreciate feedback on plugins on all platforms. Note, however, that a lot of the bugs around plugin detection are still unresolved, so this work is only testable on the plugins that you can actually see. :D

On *nix these changes are combined with a bunch of bug fixes and redesigns. First of all, libnpp.so is now built into Opera and all known plugin bugs that result in Opera crashing are resolved (including using 64-bit Opera with 32-bit plugins). We added a work-around for the Flash player crashes with r48 and a lot of other fixes. Please retest any issues you have had with plugins and report back on the relevant bug reports what you find. If you find any new bugs: report, report, report! We really do want to make Kestrel the best release for plugins ever on *nix. :) Note that although most of the work has been focused on Linux, the work so far is *nix platform independent: more work on FreeBSD and Solaris is planned. Please also note that because of the fix for the 64 vs. 32-bit issue, this release is incompatible with previous pluginwrappers. There are also some fixes that will affect Java, so we are interested in feedback on that as well.


**Known issues**
[LIST]
[*]"Save to download folder" is broken
[*]Format selector when saving pages is broken.
[*]Inline find stops working after entering one letter (using Ctrl/Cmd+F still works as expected).
[/LIST]


**Changelog**
[LIST]
[*]Fixed text selection when selecting from bottom left to top right
[*]Crashing plugins should no longer crash Opera on Mac and Windows. Please test.
[*]Fixed crash when opening certain files (especially PDF files)
[*]Fixed crash when changing interface language
[*]Some changes have been made to the tab mode "Activate first tab opened from current tab" (whose name might change in the future): If you open several tabs in the background from one page, Opera will remember that they are related and will switch focus between them when you close one of them. In the previous weekly you had to close the parent tab before this occured.
[*]"Activate tab to the right" preference now works on UNIX and Mac. The mode described above still doesn't work.
[*]Windows: Tray icon is now gone if you don't have mail enabled
[*]UNIX: Made Flash 7 work again
[*]UNIX: When closing a tab, flash animations in other tabs will not be killed anymore
[*]UNIX: And a lot of other plugin fixes
[/LIST]

**Mail**
[LIST]
[*]Really delete associated messages when deleting accounts
[*]Fixed crash when downloading IMAP mail sent from Outlook
[*]Attempt to clean up ghost messages on start-up
[*]Fetch more than 50 messages at a time from IMAP accounts
[*]Fixed unread count inconsistencies
[*]Fixed problem with subscriptions for nested IMAP mailboxes
[*]Fixed problem getting all new messages for IMAP accounts
[*]Fixed problem with stuck IMAP connections when fetching headers/messages
[*]Better synchronization handling after waking computers on Windows and OS X
[*]Decode body parts before indexing them
[*]Fixed overzealous IMAP expunging
[/LIST]

---

### Post by prince_niceguy on 2008-02-22
great improvement over the previous release. quite stable. have not encountered crash still... keeping my fingers crossed... the plugin of flash works.. which is normally which I use.

and it loads way faster then fire the fox... not sure when they will take a leaf out of opera and make their browser load faster and lesser memory hog.

---

### Post by brunoscunha on 2008-02-22
looks quite good and faster than firefox, but some sites are unable to load in opera

---

### Post by C. Wizard on 2008-02-22
I've been running last September's release and have been quite happy with it.

Installed today's release and was that ever a major mistake!

I'm not enough of a geek to say exactly what was wrong, but it certainly was NOT as fast as the Sept. release and the Xine plugin was the only plugin it could handle.  Nothing else worked.  Even tried to use CrossOver to install the 32 bit plugins, but that did not work with the beta, as it did with the Sept. version.
Wasted a good 3 hours trying to get it to work and then flinally flushing it and re-installing the Alpha release.

If anyone is in contact with Opera, please tell them they took a couple of steps backwards, not forward.
:(

---

### Post by elarella on 2008-02-23
Just downloaded the new build (1823).  i must say, it is alot more stable.  Flash doesn't crash as often as it used to on the more flash heavy sites (i.e. Youtube, MySpace ... etc).  Opera is coming close to a more stable browser. :guitar:

---

### Post by inphektion on 2008-02-23
> **C. Wizard said:**
> I've been running last September's release and have been quite happy with it.

Installed today's release and was that ever a major mistake!

I'm not enough of a geek to say exactly what was wrong, but it certainly was NOT as fast as the Sept. release and the Xine plugin was the only plugin it could handle.  Nothing else worked.  Even tried to use CrossOver to install the 32 bit plugins, but that did not work with the beta, as it did with the Sept. version.
Wasted a good 3 hours trying to get it to work and then flinally flushing it and re-installing the Alpha release.

If anyone is in contact with Opera, please tell them they took a couple of steps backwards, not forward.
:(
I think you are doing something wrong.  make sure you uninstall opera AND any old plugin wrappers you used for it in the past as they will no longer work. After removing my old nspluginwrapper and the old opera and simply installing this latest one, for the first time the flash plugin worked for me right out of the box.  Stability is approaching where they are with 9.26 so I think soon this can come out of beta.

---

### Post by John Jason Jordan on 2008-02-23
I am using an old snapshot and don't have time to keep trying new ones. What I have works mostly, including flash, so I prefer to wait until the 64-bit version is final. Has Opera given any indication of when they think that might be?

---

### Post by NullHead on 2008-02-23
I didn't know there was going to be a 64bit verson of opera. This is good news! I'm excited to try this out! :D

---

### Post by C. Wizard on 2008-02-24
> **inphektion said:**
> I think you are doing something wrong.....Stability is approaching where they are with 9.26 so I think soon this can come out of beta.

Nope.

I've been using Opera since the entire program fit on a single 1.44 meg. 3 1/2 inch floppy (paid for it a couple of times too :)  ).

It was a dark rainy day here so I spent most of the day playing with the beta and i would not call it stable.
 
I completely wiped out the previous installation of Opera and all traces thereof.
Un-installed the 64 bt plugins for Firefox and Firefox itself.  Then re-started the Xserver and re-installed Firefox, the Firefox plugins, and, finally, the Opera beta.

Yes, the plug-ins did work out of the box, sometimes. Sometimes they did, sometimes they didn't.  There seem to be some sort of video problem as Opera logo "mouse tracks" were on the screen every now and then.

I would go to save a message on a site and couldn't save the message. I would go to edit a previous message and couldn't get the edit function to work. Fired up Firefox and was able to do what could not be done in the Opera beta.  

Finally, when it froze, I repeated the same sequence as outlined above, but this time installed the Alpha version.  Things are now back were they were before intalling the beta, that is, Opera, the alpha, is now working and working very well.

I actually like the 64 bit alpha better than the 32 bit 9.25 version. The alpha does a much better and faster job of loading and displaying a page.

BTW, does anyone know if there is a 64 bit plugin for midi files? I can't find one.

Thanks.

---

### Post by elarella on 2008-02-24
> **inphektion said:**
> I think you are doing something wrong.  make sure you uninstall opera AND any old plugin wrappers you used for it in the past as they will no longer work. After removing my old nspluginwrapper and the old opera and simply installing this latest one, for the first time the flash plugin worked for me right out of the box.  Stability is approaching where they are with 9.26 so I think soon this can come out of beta.

I was able to install build 1823 over the older build that I had (I think it was 1756 or 1754?)

All the plugins still work, INCLUDING Adobe Flash 9, r115.  :)

The only thing I noticed was that the browser doesn't crash on flash heavy sites and the browser is alot faster at loading webpages.

I forgot to mention that I am running Ubuntu 7.10 64 bit.  :)

---

### Post by C. Wizard on 2008-02-27
OK. I got it to work with the 64 bit plugins for Firefox, BUT now there is another problem.
When on a message board, when I click on the little icon to take me to most recent message posted since my last visit, it no longer works. It takes me to the last page, but not to where I left off.
Ditto, if I click on "last message."  It doesn't take me to the last message posted, but to the top of the last page.
Anyone know a fix for this.
Many Thanks.

---

### Post by igknighted on 2008-02-27
Has anyone gotten java to work natively in opera yet?  I know opera doesn't use the java plugin... so maybe (just maybe?) it can recognize the install in 64bit and use it?

---

### Post by Colonel Kilkenny on 2008-02-28
> **igknighted said:**
> Has anyone gotten java to work natively in opera yet?  I know opera doesn't use the java plugin... so maybe (just maybe?) it can recognize the install in 64bit and use it?

Well, I'm not using 64 bit version so cannot say anything about that for sure but it **should** recognize and use your java installation just fine. 
ctrl+f12 -> Advanced -> Content -> Java options and search your java installation (might be something like /usr/lib/jvm/java-6-sun/jre/lib/amd64).

---

### Post by coolbrook on 2008-02-28
Anyone else having trouble installing the tarball?  It appeared to install ok but the Opera logo isn't showing up under Applications>Internet.  It's just a generic icon and when I click on it, nothing executes.

**edit:**  nevermind.. the .deb file works fine even though my processor is Intel.

---

### Post by prince_niceguy on 2008-02-28
> **coolbrook said:**
> Anyone else having trouble installing the tarball?  It appeared to install ok but the Opera logo isn't showing up under Applications>Internet.  It's just a generic icon and when I click on it, nothing executes.

**edit:**  nevermind.. the .deb file works fine even though my processor is Intel.

even though it is called amd64 it should be working with Intel 64 with 64OS... the reason being called AMD64 is it was AMD which initially started the x86 to x86-64 bit... hence the credit is given to AMD and not intel for the same. Intel was promoting its own itanium and it did not fly...

---

### Post by inphektion on 2008-02-29
New snapshot today:

[http://snapshot.opera.com/unix/snapshot-1834/x86_64-linux/]("http://snapshot.opera.com/unix/snapshot-1834/x86_64-linux/")

**Changelog**
[LIST]
[*]Fixed IMAP and POP synchronization problems
[*]RSS items that are already read are not shown in the notification anymore
[*]It is now possible to set Opera as default mail application from Control Panel
[*]When right-clicking in Speed Dial search field you you can easily reach the "Search options"
[*]Fixed cut-n-pasting bookmark folders
[*]Fixed selecting or creating a new bookmark file with Sync
[*]"Save to download folder" works again
[*]Context menu in transfers panel now work again when no other tabs are open
[*]Content-disposition: attachment filename suggestion now respected when saving files
[*]Fixed saving multiple files from the links panel
[*]Some initial implementation for flipping scrollbars on RTL web sites (to permanently flip, enable opera:config#UserPrefs|Left-handedUI)
[*]Fixed problem finding new POP messages when using the "Leave messages on server" setting
[*]Better search results when using Quick find in Opera Mail
[/LIST]

**UNIX specific:**
[LIST]
[*]Prevent GTK from changing the global locale settings - this would occasionally make text disappear or shrink on web pages after using the GTK filechooser
[*]Autoscroll/pan now appears where clicked, not in middle of page
[*]Fixed plugin detection for .1 and .5 builds
[*]Several more plugin fixes
[/LIST]

---

### Post by C. Wizard on 2008-03-01
OK. Installed the 29 February "snapshot" but still have the same problems.  
When on a message board, if I click on the little icon to take me to most recent message posted since my last visit, it no longer works. It takes me to the last page, but not to where I left off.
Ditto, if I click on "last message." It doesn't take me to the last message posted, but to the top of the last page.
Anyone know a fix for this.
Thanks.

Edit in: The problem appears to be IPB boards, which have always worked in the past. SMF boards seem to work OK.

---

### Post by cbahimsa on 2008-03-05
Am delighted to see 64 bit Opera too. Have been using the 32 bit builds for a long time and have not seen the issue am facing with the Feb 29 64 bit version. It downloaded and still does every email starting from the very first one I got in my gmail accounts, including spam. Also, it seems to like duplicating them.

---

### Post by inphektion on 2008-03-18
**New Snapshot Released**
[Download 64bit .deb here.]("http://snapshot.opera.com/unix/snapshot-1875/x86_64-linux/opera_9.50-20080318.2-shared-qt_amd64.deb")

**Changelog:**
[LIST]
[*]Fixed inline find.
[*]Fixed downloading attachments in the new Yahoo! mail.
[*]Fixed async XMLHttpRequest to never be blocked by a slow script.
[*]Fixed internal plugin methods not accessible from javascript engine when data attribute defined.
[*]Fixed an issue where new mail messages would not be detected.
[*]Opera Mail now handles mailto links with encoded characters correctly.
[*]Improved handling of subscription to temporary subscription to news groups.
[*]Fixed some offline mode issues.
[*]And lots more of stability fixes!
[/LIST]

**Acid3 fixes:**
[LIST]
[*]getSVGDocument is now supported in an iframe.
[*]createDocumentType now throws an exception for malformed qualified name.
[*]Fixed NodeFilter returning true => 1.
[*]Fixed HTMLTableRowElement.rowIndex and .sectionRowIndex returning undefined for table rows created via DOM.
[*]HTMLButtonElement.type now defaults to "submit".
[*]Fixed form control collection not indexed by name when outside the main document tree.
[*]Fixed Range.surroundContents().
[*]Fixed insertNode to not collapse range.
[*]Fixed removeNamedItem() and removeNamedItemNS() to throw a not-found error.
[*]Fixed NodeIterator to function well also under dynamic changes.
[*]Fixed Date.UTC() to do proper 1900 year offsetting.
[/LIST]

**UNIX specific:**
[LIST]
[*]Fixed crash when closing tab with Flash.
[*]Several plugin fixes.
[/LIST]

---

### Post by inphektion on 2008-04-17
**New Snapshot Released**
[Download 64bit .deb here.]("http://snapshot.opera.com/unix/snapshot-1929/x86_64-linux/opera_9.50-20080417.2-shared-qt_amd64.deb")

Beta 2 is close.  View the post [here.]("http://my.opera.com/desktopteam/blog/2008/04/17/beta-2-is-coming")

---

### Post by C. Wizard on 2008-04-20
In this build, 1929, you cannot save an image.  It seems like every time one thing gets fixes something else gets broken in the process.

---

### Post by inphektion on 2008-04-20
Yea but when they already know about it you know it'll be fixed before release.  
Known Issues
[Bug 324643] "Remove from toolbar" doesn't work
[Bug 324645] Right-clicking an IRC channel prevents it from showing new messages
[Bug 322553] The "Execute program" action fails in certain circumstances
[Bug 324678] Mail attachment options don't work on Windows
[Bug 324696] The "Go to Web Address" action fails on Windows
[Bug 324699] Crash when choosing "Open Opera" from the tray icon after hiding Opera on Windows when the mail client is disabled
[Bug 324700] "Save image" context menu item doesn't work

---

