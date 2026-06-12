---
title: "TLS library not found"
date: 2015-05-10
forum: Wine
---

### Post by jefty on 2015-05-10
I've got a new install of Ubuntu - 15.04 and installed the latest version of wine (1:1.6.2-0ubuntu8). I'm getting a constant error of:

err:secur32:SECUR32_initSchannelSP TLS library not found, SSL connections will fail

I've played around with several variations, but haven't been able to make it work. It seems like I have to be missing something simple. 

Any ideas what I should try?

---

### Post by fondfire on 2015-11-11
I'm also having this problem and it keeps Adobe Digital Editions from functioning fully in its wine bottle... Very frustrating! Based on other things I've read, it sounds as though the wine1.6-i386 package was compiled without gnutls support (and perhaps the wine1.6-amd64 package also?); without that support, programs cannot retrieve HTTPS URLs, which makes a great many programs that would otherwise run beautifully under wine just utterly useless. So for instance, I can readily retrieve books into Adobe Digital Editions that only reference HTTP URLs in the ACSM files used to guide that retrieval; if there's an HTTPS URL in the ACSM file, I can't retrieve a damned thing. This is a massive inconvenience when I would think this is basic support that should be baked into the wine1.6-i386 package.

I've been trying to determine if there is an alternative package for Ubuntu that I can retrieve or if I have to go to all the trouble of compiling my own just to get this support. Anybody got any better guidance than I have? I'm still banging on search engines trying to find better guidance...

--Fondfire

---

