---
title: "FireFox 3.5.2 does not work"
date: 2009-08-05
forum: x86 64-bit Users
---

### Post by mopuf on 2009-08-05
Hi

I have a 64 bit system and I want to update the fire fox. 
For this I use the ubuntuzilla ([http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)). 
The ubuntuzilla script was working, the fire fox was updated and the firefox(3.5.2) is also starting, the only problem is that I can not contact any other server out side my network
(by example the [www.google.com]("http://www.google.com")). I can see my dsl model and the router, but I that it, I can not see other servers.
More frustrating, I download the 3.5.2 from the mozilla.org and I relink the /usr/bin/firefox to this version and the same effect.
More,More frustrating the old version(3.5.1) is working.
 
My question I make something wrong here ? Requires mozilla/firefox a specific configuration ?

Regards,
M

---

### Post by nanotube on 2009-08-05
Hi

in firefox, go to "about:config", and set network.dns.disableIPv6 setting to true.

this issue is mentioned in the ubuntuzilla faq:
[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_I_installed_the_latest_Firefox.2C_but_cannot_connect_to_any_websites._Any_suggestions.3F](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_I_installed_the_latest_Firefox.2C_but_cannot_connect_to_any_websites._Any_suggestions.3F)

---

