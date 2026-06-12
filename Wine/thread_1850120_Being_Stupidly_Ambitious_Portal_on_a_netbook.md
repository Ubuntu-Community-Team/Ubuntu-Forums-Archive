---
title: "Being Stupidly Ambitious: Portal on a netbook"
date: 2011-09-25
forum: Wine
---

### Post by Notselfcreated on 2011-09-25
All right, so I don't have my hopes up.

Stock from Steam, Portal on my Aspire One D150 (Ubuntu Natty + Wine) is a slide show. A veritable PowerPoint presentation. OpenGL is installed and working fine. I have 2gb of RAM.

I know that Portal is playable on netbooks in Windows. [Source]("http://www.youtube.com/watch?v=DW54TsYl_dg"). Windows users just have to append "-dxlevel 80" to their exe link.

I did the same thing in Steam on Wine. I typed "-dxlevel 80" into the launch settings for Portal.

And if I didn't know any better I'd say that there was a tiny hair of improvement. But not enough to make it playable.

So am I just totally wasting my time here or is there something else I can fiddle with?

---

### Post by drawkcab on 2011-09-26
I wonder if vsyncing the gpu would help?  

Another thing might be to install openbox or lxde in order to lower the overhead cpu usage.  You could session into either to run wine.

---

### Post by Serujisu on 2011-09-26
It may very well be issues I've heard about between Linux and Intel integrated graphics chips. I've gotten Portal to run on my Asus EeePC 1015PEM in the past (which I believe has an Intel GMA3150) running under Windows XP, but couldn't get anything graphically intensive to run under Linux Mint 10 (World of Warcraft in particular). Someone else might know more about it on a technical level, though.

---

