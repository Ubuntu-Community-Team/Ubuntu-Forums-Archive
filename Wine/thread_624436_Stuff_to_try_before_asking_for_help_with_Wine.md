---
title: "Stuff to try before asking for help with Wine"
date: 2007-11-26
forum: Wine
---

### Post by cogadh on 2007-11-26
There are many things you can do to try and get your application working in Wine. Some basics you should try with every app before resorting to posting for help:
[LIST=1]
[*]***Check AppDB*** - Wine's [Application Database](http://appdb.winehq.org/) is one of the best sources for help with running apps in Wine. First and foremost, it will tell you when an application is not worth trying at all. Secondly, but almost as important, an application's AppDB entry may include how-to information on the proper way to install and run your application.
[*]***Search for an existing how-to*** - Many popular applications have excellent how-tos already written for them that aren't necessarily part of AppDB. Google is your friend.
[*]***Update Wine*** - Unless the information you obtained from AppDB or your how-to told you to use a specific version of Wine, you should try updating to the most current version of Wine. Each update includes many bugfixes that can correct your issue. HOWEVER, it is important to note that an update could include new bugs or regressions that will cause problems with some applications.
[*]***Use the Wine virtual desktop*** - For testing purposes, Wine's virtual desktop allows you to try running an application without it directly impacting your desktop. This is especially useful when trying to run a full screen game in Wine.
[*]***Search the forums*** - There are many, many, many, many, many, many posts on running specific applications in Wine already. Chances are really good that someone has already asked the same question you have.
[*]***Try different OS versions*** - Even though the application you are trying to run was made for Windows 98, it may work better if you set the OS version in Wine to Windows XP. I once had an old Windows 95 application only run when I set the OS version to NT 4. Trying out different settings may correct your issue.
[*]***Check the terminal output*** - Perhaps I should say "*Use the terminal*" first. When run from the terminal, Wine outputs any error messages to the terminal window, which may tell you exactly what is wrong. This is especially useful for identifying when a DLL is missing and an override may be needed. Check the output for details like that and anything else that may identify where your error is occurring.[/QUOTE]
[/LIST]

---

