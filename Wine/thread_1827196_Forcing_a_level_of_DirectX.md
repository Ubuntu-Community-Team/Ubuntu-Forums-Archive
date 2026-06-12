---
title: "Forcing a level of DirectX"
date: 2011-08-17
forum: Wine
---

### Post by s3a on 2011-08-17
Is there a way to force any game to use a certain version of DirectX (as long as the game supports the particular version of DirectX)? I don't mean a game specific way to force DirectX. I mean a way which works with any software running through Wine.

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by wineman on 2011-08-29
hi there!

so to answer your questions, they are possible, but i'll explain each now:
> **s3a said:**
> Is there a way to force any game to use a certain version of DirectX (as long as the game supports the particular version of DirectX)?

Yes. You can install the DX version that (either) came with the game or came from MS into your winecache (either by using wine, winetricks, or playonlinux) and then you can set (using winecfg) the app to run off the DX alongside the openGL.

> **s3a said:**
> 
I don't mean a game specific way to force DirectX. I mean a way which works with any software running through Wine.

This is a little more tricky. On a per-winecache basis its easy to do, just do the above method, but if you were to reconfigure your **system** to use DX as the primary wine graphical software engine, that would take some creative programming and a lot of elbow grease to get right. plus i dont think MS would like it very much - their SDK doesnt really extend into wine (if my memory serves me correctly). 

Look, im not saying its impossible, i have done it before, but its flipping difficult. i'll have to do some digging on my pc to look for how i did it (it was at least a year or 3 ago) and then i'll try and post it here. Basically to do it you'd need to rebuild the file structure of the wine equivalent of /etc/skel using your /etc/sysctl.d/wine.conf files and one or 2 .conf files in /usr/share/wine or /usr/lib/wine/fakedlls. This takes some programmatic work, but its worth it when all your games run in native DX and tessalations are native to Wine. Ah, the joys of WINE!! 
Also, please note that too many wine dlls that are replaced with windows DLLs cause something called the "Windows Experience", which is copyright protected by MS and they get very iffy if you make a non-windows system have a windows experience.

HTH - will post the howto of redoing the DLLs by the 5th/9/2011.

HTH

---

