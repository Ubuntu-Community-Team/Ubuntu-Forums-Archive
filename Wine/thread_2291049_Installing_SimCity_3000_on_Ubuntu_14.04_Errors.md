---
title: "Installing SimCity 3000 on Ubuntu 14.04 Errors"
date: 2015-08-17
forum: Wine
---

### Post by ryan174 on 2015-08-17
Hello everyone,

I am trying to install SimCity 3000 on Ubuntu 14.04 and I either get a POL error saying "Error in main. Sim City 3000 crashed. Click on debug link to get more details." or a POL_wine error saying that wine crashed. when I run the PlayOnLinux debugger, here is the script I get:

[08/16/15 18:06:23] - Running wine-1.3.1 --version (Working directory : /home/ryan/.PlayOnLinux/shortcuts)
wine-1.3.1

PlayOnLinux logfile
  
> wine --version
  wine-1.3.1
> POL_WINEVERSION
  1.3.1
> WINEPREFIX
  /home/ryan/.PlayOnLinux//wineprefix/SimCity3000
> Distribution
  Ubuntu 14.04.2 LTS
> glxinfo \| grep rendering
  
> glxinfo \| grep renderer
  
> OpenGL libs (Direct rendering testing)
  32bits direct rendering is enabled
  64bits direct rendering is enabled

[08/16/15 18:06:32] - Running wine-1.3.1 cmd /c echo %ProgramFiles% (Working directory : /home/ryan/.PlayOnLinux/shortcuts)
C:\Program Files 
[08/16/15 18:06:36] - Running wine-1.3.1 cmd /c echo %ProgramFiles% (Working directory : /home/ryan/.PlayOnLinux/shortcuts)
C:\Program Files 
[08/16/15 20:54:21] - Running wine-1.3.1  (Working directory : /home/ryan/.PlayOnLinux/wineprefix/SimCity3000/drive_c)
wine: cannot find ''

Any ideas on what I could have done wrong or what I am missing? I am new to Linux and am still fumbling around with the change from Windows.

Ryan

---

### Post by howefield on 2015-08-17
Thread moved to the "*Wine*" forum.

---

