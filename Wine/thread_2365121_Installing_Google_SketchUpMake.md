---
title: "Installing Google SketchUpMake"
date: 2017-07-03
forum: Wine
---

### Post by jamesbrady on 2017-07-03
I am attempting to get Sketchup Make 2017 installed on my Ubuntu 16.04 using wine. I have the .exe file in the /opt folder. During the installation, the installer tells me I need Microsoft .NET framework 4.5.2 to continue the install. 
If I click "Install", it begins installing, but once the install bar reaches the end, it resets and does it again in one big loop. So if I try and install it in the terminal using

```
sudo apt-get install dotnet-dev-1.0.4
```

It tells me I already have the framework installed on my machine. So... I don't know where to go from here.

---

### Post by sccman on 2017-07-07
I'm not sure what dotnet-dev-1.0.4 is, but I know Winetricks allows you to install .NET Framework 4.5.2. Try using Winetricks:

```
sudo apt install winetricks && winetricks --gui
```

Then go to:

1) Select the default wineprefix
2) Install a Windows DLL or component

Then find the Package dotnet452 and click its checkbox and OK. It should install .NET Framework 4.5.2.

---

