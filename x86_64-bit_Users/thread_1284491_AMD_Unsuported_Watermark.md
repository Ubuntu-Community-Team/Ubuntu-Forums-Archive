---
title: "AMD Unsuported Watermark"
date: 2009-10-06
forum: x86 64-bit Users
---

### Post by Gosport on 2009-10-06
I have an integrated ATI Radeon HD 4200 graphics card.
I installed the proprietary driver through Ubuntu's hardware manager and now have an ugly AMD UNSUPPORTED HARDWARE watermark in the lower right corner of the screen.

I found the following solution (see below) on the web and have a few questions:
Is it safe?  Do these downloads look legit? 

I'm a noob so bear with me.  From the description it looks like I should revert to the non proprietary drivers, then download the control and signature files (In the comments, at the very botom, he posted a link to these files) and put them in this folder: common -> etc -> ati  

Next I should run the following two commands (separately?) in the terminal: 
sudo cp control /etc/ati/control
sudo cp signature /etc/ati/signature

Finally I need to reboot and the watermark should be gone!  Maybe?






Below is what I found on the web at [http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/comment-page-1/#comment-14:](http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/comment-page-1/#comment-14:)
         **AMD ‘Unsupported Hardware’ Watermark in Ubuntu**

                      September 17th, 2009             [aeriph]("http://www.hugh-grigg.net/author/admin/")                                        [Leave a comment]("http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/comment-page-1/#respond")                 [Go to comments]("http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/comment-page-1/#comments")                                  
                      I’ve just built a new desktop computer for uni. It’s got an onboard [ATI Radeon HD 4200]("http://www.amd.com/uk/products/desktop/graphics/ati-radeon-hd-4000/Pages/ati-radeon-hd-4000-series.aspx") and after installing proprietary drivers in Ubuntu (System -> Administration -> Hardware Drivers) I got this annoying watermark:
 [[IMG]http://www.hugh-grigg.net/media/2009/09/amd-unsupported-hardware-watermark-ubuntu.JPG[/IMG]]("http://www.hugh-grigg.net/media/2009/09/amd-unsupported-hardware-watermark-ubuntu.JPG")AMD 'Unsupported Hardware' in Ubuntu 9.04

 Here’s an explanation and solution, inspired by [this article]("http://www.phoronix.com/scan.php?page=news_item&px=NTkyMg").
 This seems to be a fairly common problem if you’re running older ATI GPUs – apparently the FGLRX driver on Ubuntu doesn’t support hardware below Radeon 9xxx. But the Radeon HD series is far newer than that, so in this case it seems that the driver in Ubuntu’s repository is actually out of date for the most modern GPUs.
 I tried downloading and manually installing the [latest Catalyst driver]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.5.3.1") (9.9) from AMD. This removed the watermark (hooray!) but Ubuntu didn’t seem very happy with it and would only run in low graphics mode.
 The solution was to use Ubuntu’s driver from the repo, but copy the control and signature files from Catalyst 9.9 (which does support Radeon HD). Cue a 93Mb download just to extract the 250Kb of data I need (93Mb via Tiscali is like transporting a pyramid with a skateboard).
 The driver executable installer is **ati-driver-installer-8-12-x86.x86_64.run** so to extract it run:
 sudo sh ./ati-driver-installer-8-12-x86.x86_64.run --extract

 This will extract the driver files but not actually install them. The control and signature files are in the new directory: common -> etc -> ati.
 You’ll need to overwrite their counterparts in /etc/ati, so navigate to this folder and enter:
 sudo cp control /etc/ati/control
sudo cp signature /etc/ati/signature

 Reboot and the watermark should be gone, leaving you with all the graphics power and HDness you need.
 [[IMG]http://www.hugh-grigg.net/wp-content/plugins/add-to-facebook-plugin/facebook_share_icon.gif[/IMG]]("http://www.facebook.com/share.php?u=http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/")[Share on Facebook]("http://www.facebook.com/share.php?u=http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/")
                     
                      Categories: [Nerd stuff]("http://www.hugh-grigg.net/category/nerd-stuff/")            Tags: [Ubuntu]("http://www.hugh-grigg.net/tag/ubuntu/")        
     
                                        [Comments (4)]("http://javascript%3Cb%3E%3C/b%3E:void%280%29;")         [Trackbacks (0)]("http://javascript%3Cb%3E%3C/b%3E:void%280%29;")                 [Leave a comment]("http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/comment-page-1/#respond")                 [Trackback]("http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/trackback/")          
            
[LIST=1]
[*]                                       [IMG]http://www.gravatar.com/avatar/effaaf1ce78eb8d32111d22d84242fb7?s=32&d=http%3A%2F%2Fwww.gravatar.com%2Favatar%2Fad516503a11cd5ca435acc9bb6523536%3Fs%3D32&r=G[/IMG]            
                                                                                    Mike                                                                  
         
                                        October 4th, 2009 at 04:36                     | [#1]("http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/comment-page-1/#comment-12")             
                              [Reply]("http://javascript%3Cb%3E%3C/b%3E:void%280%29;") |                  [Quote]("http://javascript%3Cb%3E%3C/b%3E:void%280%29;")                             
                                                                                 Thanks…that worked like a charm and was about 1,000% easier than what everyone else was suggesting.
[*]                                       [IMG]http://www.gravatar.com/avatar/0ea7f0bb6ce805be99b4b62fb47a1bbb?s=32&d=http%3A%2F%2Fwww.gravatar.com%2Favatar%2Fad516503a11cd5ca435acc9bb6523536%3Fs%3D32&r=G[/IMG]            
                                                  [                                  aeriph                                     ]("http://www.hugh-grigg.net/")                             
         
                                        October 5th, 2009 at 12:21                     | [#2]("http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/comment-page-1/#comment-13")             
                              [Reply]("http://javascript%3Cb%3E%3C/b%3E:void%280%29;") |                  [Quote]("http://javascript%3Cb%3E%3C/b%3E:void%280%29;")                             
                                                                                 [@Mike ]("http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/comment-page-1/#comment-12")
glad it worked for you
[*]                                       [IMG]http://www.gravatar.com/avatar/b87435f50fef2cc9bf35db884890f2c0?s=32&d=http%3A%2F%2Fwww.gravatar.com%2Favatar%2Fad516503a11cd5ca435acc9bb6523536%3Fs%3D32&r=G[/IMG]            
                                                                                    Michael                                                                  
         
                                        October 6th, 2009 at 16:43                     | [#3]("http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/comment-page-1/#comment-14")             
                              [Reply]("http://javascript%3Cb%3E%3C/b%3E:void%280%29;") |                  [Quote]("http://javascript%3Cb%3E%3C/b%3E:void%280%29;")                             
                                                                                 Do I actually need to download the huge Catalyst driver?
[*]                                       [IMG]http://www.gravatar.com/avatar/0ea7f0bb6ce805be99b4b62fb47a1bbb?s=32&d=http%3A%2F%2Fwww.gravatar.com%2Favatar%2Fad516503a11cd5ca435acc9bb6523536%3Fs%3D32&r=G[/IMG]            
                                                  [                                  aeriph                                     ]("http://www.hugh-grigg.net/")                             
         
                                        October 6th, 2009 at 17:01                     | [#4]("http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/comment-page-1/#comment-15")             
                              [Reply]("http://javascript%3Cb%3E%3C/b%3E:void%280%29;") |                  [Quote]("http://javascript%3Cb%3E%3C/b%3E:void%280%29;")                             
                                                                                 [@Michael ]("http://www.hugh-grigg.net/2009/09/17/amd-unsupported-hardware-watermark/comment-page-1/#comment-14")
well, it’s your lucky day, i’ve uploaded the control and signature files:
[http://www.hugh-grigg.net/download/control](http://www.hugh-grigg.net/download/control)
[http://www.hugh-grigg.net/download/signature](http://www.hugh-grigg.net/download/signature)
So if you trust me feel free to download them from there. If not then yes, you’ll have to download the entire driver.
[/LIST]

---

### Post by Gosport on 2009-10-08
Nobody has an opinion on this possible solution??  What about my reading of the procedures?

---

### Post by Yellow Pasque on 2009-10-08
You might get a better response here: [http://www.phoronix.com/forums/forumdisplay.php?f=19](http://www.phoronix.com/forums/forumdisplay.php?f=19)

Use the bugmenot account if you don't feel like registering: [http://www.bugmenot.com/view/phoronix.com](http://www.bugmenot.com/view/phoronix.com)

---

### Post by Gosport on 2009-10-09
Thank you!  I'll try that.

---

### Post by Gosport on 2009-10-26
I found this review of a similar board to mine running a ATI Radeon HD 4200 intigrated graphics card.  Looks like Karmic Koala will indeed remedy the situation.  Yeah!



[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16813128394](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16813128394)

N/ATech Level: average Ownership:  1 week to 1 month 			 			 				10/6/2009 11:14:15 AM
 				 					[IMG]http://c1.neweggimages.com/WebResource/Themes/2005/Nest/goldegg.gif[/IMG][IMG]http://c1.neweggimages.com/WebResource/Themes/2005/Nest/goldegg.gif[/IMG][IMG]http://c1.neweggimages.com/WebResource/Themes/2005/Nest/goldegg.gif[/IMG][IMG]http://c1.neweggimages.com/WebResource/Themes/2005/Nest/goldegg.gif[/IMG][IMG]http://c1.neweggimages.com/WebResource/Themes/2005/Nest/goldegg.gif[/IMG]  					**Good board** 				
 				 					 					
					 **Pros:** Great onboard video, good connections.  Great HTPC board.

					**Cons:** For the price?  None.

					**Other Thoughts:** Runs Linux Ubuntu 9.1 Karmic Koala Beta like a champ with my AMD Regor 245 and OCZ 1066 ram. I tried Ubuntu 9.04 but found issue with the AMD video driver leaving an "Unsupported Hardware" watermark icon on my lower left screen. I tried the Alpha 6 and then the Beta of Karmic and it works great. The EXT4 boots very fast.

---

### Post by 4partee on 2009-10-26
Try this:

[http://ubuntuforums.org/showthread.php?t=1293110&highlight=hd4200&page=6](http://ubuntuforums.org/showthread.php?t=1293110&highlight=hd4200&page=6)

---

### Post by Gosport on 2009-10-26
Darn!  Oh well, I've heard that the driver will be supported in the April release without having to jump through all these hoops.

---

