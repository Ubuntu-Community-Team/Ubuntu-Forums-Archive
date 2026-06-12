---
title: "winetricks will not install anything"
date: 2018-09-28
forum: Wine
---

### Post by estatistics on 2018-09-28
Dear Ubuntuers, 

I am running Lubuntu, and the latest versions of wine and winetricks. 

I have a very frustrating problem.
Winetricks will not download anything at all! 
When wget is used by winetricks, it says failed to fetch the file in demand from microsoft download page (mainly). It fails to communicate with download.microsoft.com

I used that terminal command: ```
 WINEPREFIX="$HOME/.wine32" WINEARCH=win32  winetricks 
```
I can access internet or to download things outside wine environment. 

Gpower that I want to run, it throws the pasted code.
Therefore, I cannot apply the tip of that page.[https://ubuntuforums.org/archive/index.php/t-1342734.html]("https://ubuntuforums.org/archive/index.php/t-1342734.html")

```
elias@eliasc:/usr$ WINEPREFIX="$HOME/.wine32" WINEARCH=win32  wine "/home/elias/.wine32/dosdevices/c:/Program Files/GPower 3.1/GPowerNT.exe "
0009:fixme:font:get_outline_text_metrics failed to read full_nameW for font L"Ani"!
0009:fixme:nls:GetThreadPreferredUILanguages 00000034, 0x32f710, 0x32f780 0x32f718
0009:fixme:nls:get_dummy_preferred_ui_language (0x34 0x32f710 0x32f780 0x32f718) returning a dummy value (current locale)
0009:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0009:fixme:nls:GetThreadPreferredUILanguages 00000034, 0x32fa54, 0x32fac4 0x32fa5c
0009:fixme:nls:get_dummy_preferred_ui_language (0x34 0x32fa54 0x32fac4 0x32fa5c) returning a dummy value (current locale)
0009:fixme:shell:InitNetworkAddressControl stub
0009:fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x32f8f8 1 C) semi-stub
0009:fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x32f6e8 1 C) semi-stub
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f644): -- Empty Stub !
0009:fixme:font:freetype_SelectFont Untranslated charset 123
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f644): -- Empty Stub !
0009:fixme:font:freetype_SelectFont Untranslated charset 123
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f63c): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f63c): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f644): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f644): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f644): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f644): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f644): -- Empty Stub !
0009:fixme:font:freetype_SelectFont Untranslated charset 123
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f644): -- Empty Stub !
0009:fixme:font:freetype_SelectFont Untranslated charset 123
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f63c): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f63c): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f644): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f644): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f654): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f654): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f65c): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x5011b, 0x32f65c): -- Empty Stub !
0009:fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x32f208 1 C) semi-stub
0009:fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x32efd8 1 C) semi-stub
0009:fixme:font:GetAspectRatioFilterEx (0x500d3, 0x32f040): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x500d3, 0x32f040): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x500d3, 0x32f040): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x500d3, 0x32f040): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x500d3, 0x32f194): -- Empty Stub !
0009:fixme:font:freetype_SelectFont Untranslated charset 126
0009:fixme:font:GetAspectRatioFilterEx (0x500d3, 0x32f040): -- Empty Stub !
0009:fixme:font:freetype_SelectFont Untranslated charset 123
0009:fixme:font:GetAspectRatioFilterEx (0x500d3, 0x32f040): -- Empty Stub !
0009:fixme:font:freetype_SelectFont Untranslated charset 123
0009:fixme:font:GetAspectRatioFilterEx (0x500d3, 0x32f040): -- Empty Stub !
0009:fixme:font:GetAspectRatioFilterEx (0x500d3, 0x32f040): -- Empty Stub !

```

What I can do? 

Thank you.

Sincerely,
Elias Tsolis

---

### Post by jacko777 on 2018-11-03
Hello Elias,
I probably can't help because I,m asking for help on this forum too.
Try this URL and see if it is of any help to you.
<code>
[https://www.wikihow.com/Install-Wine-on-Ubuntu](https://www.wikihow.com/Install-Wine-on-Ubuntu)
</code>
I truly hope you get somewhere with this.
Rod

---

### Post by Holger_Gehrke on 2018-11-03
I can't say what's wrong with your installation, but if you're talking about the statistics program from the University of Düsseldorf ([http://www.gpower.hhu.de/](http://www.gpower.hhu.de/)) I can tell you it seems to run without a problem on my system (XUbuntu 18.04, wine 3.0) without any need to use winetricks. The installation package contains the Visual C Runtime and installs it if necessary.

I just unpacked the downloaded zip into a temporary directory, ran 'wine ./setup.exe' and that was that.

Holger

---

