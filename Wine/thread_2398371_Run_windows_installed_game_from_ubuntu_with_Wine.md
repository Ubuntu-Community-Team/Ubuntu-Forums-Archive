---
title: "Run windows installed game from ubuntu with Wine"
date: 2018-08-11
forum: Wine
---

### Post by joaoxfranco on 2018-08-11
Hi, I came across a post explaining how to do this, but since I'm a novice at linux, I'm not very sure how to do this. 
This is the original post
[https://ubuntuforums.org/showthread.php?t=1363285](https://ubuntuforums.org/showthread.php?t=1363285)

I appreciate any and all details about this. 


      ```
I googled around and found no solutions for running my steam games which  are installed in my windows partition in Ubuntu, basically I wanted to  share the same installation between linux and windows. It was surprising  how simple it actually is, so I'm posting about it here in case someone  is  searching with no results, and doesn't have enough HDD to just  reinstall the same game in his Ubuntu partition. 

1- Boot in windows, install steam and install your games
2- Boot into Linux, and install steam.
3- Go to C:\Program Files or wherever you installed your windows steam, right click on your steam folder and click "Make link"
4- Cut and paste the "Link to Steam" file into ~./wine/drive_c/Program\ Files
5- Delete your Linux steam folder, rename "Link to Steam" to "Steam".

Now just run steam via wine, I tested it with my TF2 installation, and  it worked fine. (Don't forget the -dxlevel 81 launch option for TF2)
```

      


- About Step 2, which steam version? linux or windows steam on wine?
- About Step 4 is this folder created automatically? I just installed  wine but I can not find it. Do I need to install something first, or how  do I create this folder??
- What do you mean by delete your Linux Steam folder? where is this usually located?
- where do I put this argument "  -dxlevel 81 launch option" 

The game in question is FFX-2 HD remaster. It is important for me to do this through wine, and it is very important that I don't have to reinstall  and that the game is installed in it's windows 8.1 disk/partition, as the original method describes. Please help!

---

### Post by davidcit646 on 2018-10-10
Since there's been some time that has passed, what other games have you tested? Have you experienced any graphical, audio, or hardware issues? For example, I can play Warframe fine for hours, but sometimes it randomly crashes.

---

