---
title: "(new to ubuntu) Nothing happens when I open a program with wine, please help."
date: 2017-05-06
forum: Wine
---

### Post by con1993 on 2017-05-06
I read the read me on this topic and tried to do what I can but I'm new to this and don't know what I'm doing.

I want to use wine to open adobe creative cloud and then install and run premier.

Is this possible? Any help would be hugely appreciated.

I would have included the code recommended in the read me, but I am unfamiliar with terminal. If you could tell me the commands I can show you.

Thanks

---

### Post by con1993 on 2017-05-06
```


con@ConComp:~$ cd public
bash: cd: public: No such file or directory
con@ConComp:~$ cd Public
con@ConComp:~/Public$ cd ADOBECC
con@ConComp:~/Public/ADOBECC$ wine setup.exe
err:menubuilder:init_xdg error looking up the desktop directory
con@ConComp:~/Public/ADOBECC$ 



```

I hope this helps

---

### Post by con1993 on 2017-05-07
```


con@ConComp:~$ winecfg
Warning: could not find DOS drive for current working directory '/home/con', starting in the Windows directory.
err:menubuilder:init_xdg error looking up the desktop directory
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"C:\\users\\con\\Desktop".
err:explorer:initialize_launchers Could not get user desktop folder



```

---

### Post by Bucky Ball on 2017-05-07
Before you go much further, you might want to [look at this]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=17546"). Good idea to check WineHQ to see how others have gone with the app you're intending to install before trying to install. 

Also, not sure how the Creative Cloud works, but video/audio apps don't always work that well in Wine. Anything that is going to need to use the vid card intensively is going to have trouble, and when you say Premiere, I'm presuming you mean Premiere Pro. 

Don't know how Premiere's going to go. Installed in Wine standalone by others previously, it was not good. You can only try in Creative Cloud with Wine, if you can get Creative Cloud installed in the first instance.

PS: Posting chunks of text with no clues about what you did to produce them and what you are trying to do doesn't help potential helpers a lot. Better if you give as much info as you can. Good luck. ;)

---

