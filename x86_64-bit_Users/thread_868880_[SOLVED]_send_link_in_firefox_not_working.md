---
title: "[SOLVED] send link in firefox not working"
date: 2008-07-24
forum: x86 64-bit Users
---

### Post by skrap on 2008-07-24
Ok I have been trying for quite some time to get this fixed.  First of all I am running an AMD 64 processor with 2 gig ram and 320 gig HD.  Gutsy 7.1 64 bit version.  I have read the Thunderbird manual and Firefox manual and I have made the changes accordingly.  What is happening is when I click an email link in FF nothing happens.  With the settings I have TB should open with a write mail window to compose message to said email link.  Nothing is happening.  

This is what is set in FF about:congfig network.protocol-handler.app.mailto /usr/bin/home/skrap/.mozilla-thunderbird %s Which is the path to TB

Tb Settings = network.protocol-handler.app.mailto /usr/bin/home/skrap/.mozilla-thunderbird

If anyone could shed some light that would be great.

---

### Post by philinux on 2008-07-24
Check in system>prefs>preferred apps.

This is working fine for me.

---

### Post by warp99 on 2008-07-24
Which versions of Firefox are you using?

---

### Post by skrap on 2008-07-24
Using Firefox 2. something and I have the preferences set correctly as I said I have read the documentation at Firefox and Thunderbird nothing seems to work for me.

---

### Post by warp99 on 2008-07-25
> **skrap said:**
> Using Firefox 2. something and I have the preferences set correctly as I said I have read the documentation at Firefox and Thunderbird nothing seems to work for me.

You have the wrong path set for each binary. Your path leads to your hidden ~/.mozilla-thunderbird directory which have no binary files. If you've installed Firefox and Thunderbird from the Ubuntu repositories the path for each binary should be '/usr/bin/thunderbird' and '/usr/bin/firefox'.

The best thing is to follow these directions here at the Gentoo wiki:

[http://gentoo-wiki.com/Mozilla_Firefox/Settings#Open_mailto:_urls_in_Mozilla_Thunderbird](http://gentoo-wiki.com/Mozilla_Firefox/Settings#Open_mailto:_urls_in_Mozilla_Thunderbird)

and here

[http://gentoo-wiki.com/Mozilla_Thunderbird#Open_URLs_in_Mozilla_Firefox](http://gentoo-wiki.com/Mozilla_Thunderbird#Open_URLs_in_Mozilla_Firefox)

I have personally used these guides on numerous installs without any problems.

---

### Post by skrap on 2008-07-26
This is what I get when I try to go to [http://gentoo.wiki.com/](http://gentoo.wiki.com/)
willing to try if I can get there.



ERROR
The requested URL could not be retrieved

While trying to retrieve the URL: [http://gentoo-wiki.com/](http://gentoo-wiki.com/)

The following error was encountered:

    * Unable to forward this request at this time. 

This request could not be forwarded to the origin server or to any parent caches. The most likely cause for this error is that:

    * The cache administrator does not allow this cache to make direct connections to origin servers, and
    * All configured parent caches are currently unreachable. 

Your cache administrator is root.
Generated Sat, 26 Jul 2008 15:55:23 GMT by none (squid/3.0.STABLE1)

---

### Post by warp99 on 2008-07-26
The site must be down because here is the Google cache:

[http://209.85.141.104/search?hl=en&gl=us&q=gentoo-wiki.com%2FTIP_Firefox_Settings+gentoo+firefox+settings&btnG=Search](http://209.85.141.104/search?hl=en&gl=us&q=gentoo-wiki.com%2FTIP_Firefox_Settings+gentoo+firefox+settings&btnG=Search)

and here:

[http://209.85.141.104/search?q=cache:wEv3c2RosOMJ:gentoo-wiki.com/Thunderbird_attachments_window_too_large+gentoo+thunderbird+settings&hl=en&ct=clnk&cd=2&gl=us](http://209.85.141.104/search?q=cache:wEv3c2RosOMJ:gentoo-wiki.com/Thunderbird_attachments_window_too_large+gentoo+thunderbird+settings&hl=en&ct=clnk&cd=2&gl=us)

Remember that Google is your friend.

---

### Post by skrap on 2008-07-26
Thanks Warp looks like the site is still down.  I'll try later and let you know.

---

### Post by skrap on 2008-07-28
Hey Warp 99.  It worked! Thank you so much. I believe I have everything working now and I am very Happy with linux and all my new FREE SOFTWARE.

---

