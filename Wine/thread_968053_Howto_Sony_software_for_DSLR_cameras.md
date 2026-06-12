---
title: "Howto: Sony software for DSLR cameras"
date: 2008-11-02
forum: Wine
---

### Post by Oldster on 2008-11-02
Copied verbatim from the Sony forum at dpreview.com. I have successfully installed the software using these instructions and thought I would pass this info along. Link back to dpreview at the bottom. I see no reason why this shouldn't work with the previous version as well. I quote:

Image Data Converter 3 and Lightbox both seem to work correctly when installed in the latest version of wine (I'm running Ubuntu 8.10). There are a couple of things to do first to get the install to run.
Here are the install instructions:

1. Make sure that you have the latest wine installed.
2. Get copies of the following files

msvcp71.dll and mfc71.dll

I got them from [http://www.dll-files.com]("http://www.dll-files.com"). Put them in your .wine/windows/system folder. Note .wine is a hidden folder, so use the show hidden files option in nautilus.

3. It should then just be a matter of running the downloaded IDS3 installer file.

[*Link back to the forums.dpreview.com post*]("http://forums.dpreview.com/forums/readflat.asp?forum=1037&message=29888736&refresh=1112")

---

### Post by Malcy on 2008-11-02
Just a small alteration to the above instructions. The DLL's should be placed in the .wine/drive_c/windows/system folder.

p.s. Version 2 of Sony IDS installs straight away and doesn't need the DLL's.

---

