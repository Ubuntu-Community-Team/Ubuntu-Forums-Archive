---
title: "help needed with epson scanner"
date: 2008-11-23
forum: x86 64-bit Users
---

### Post by bregale on 2008-11-23
hi can anyone please help with my epson scanner , i have installed xsane as directed but now does still not work , i have something about having to use a backend? , as iam relitvly new to ubuntu can any one provide help ?  please make it fairly easy to follow thanks 
   my system is ubuntu hardy , amd 64, the scanner is a espson perfection 3170 photo 

ps ive been trin for weeks to get this to work 
  thanks again:lolflag:

---

### Post by Kilz on 2008-11-23
> **bregale said:**
> hi can anyone please help with my epson scanner , i have installed xsane as directed but now does still not work , i have something about having to use a backend? , as iam relitvly new to ubuntu can any one provide help ?  please make it fairly easy to follow thanks 
   my system is ubuntu hardy , amd 64, the scanner is a espson perfection 3170 photo 

ps ive been trin for weeks to get this to work 
  thanks again:lolflag:


[The Sane ]("http://www.sane-project.org/sane-backends.html")page doesnt list it, but yours maye be a new modle. Since all the other perfections are listed its a good bet this one is also.
The instructions on the [Ubuntu wiki]("https://help.ubuntu.com/community/ScanningHowTo") may be confusing to a new user. But bookmark the wiki because it will save you a lot of problems down the road.
I got my brothers epson working last year. I seem to remember that the epson2 backend was commented out. Open a terminal, and try or copy/paste in the following command.
```
sudo gedit /etc/sane.d/dll.conf
```
you will see a list of names with Epson like this

epson
#epson2

make it like this

#epson
epson2

save it and see if that helps. If not[ read this page]("http://tldp.org/HOWTO/Scanner-HOWTO/troubleshooting.html") and try its fixes.

---

### Post by C. Wizard on 2008-11-23
You need to install sane, the backend, but once you do get it working you may or may not be pleased with the results.  

As I have to scan almost daily, scanning in Linux has been the biggest single negative that has resulted from using Linux full time.  I've tried 3 different scanners, two Espon and one HP, and the results are always the same, poor to horrible.  

After spending many hours over the years working with XSane I can get a reasonable document scan, but have completely given up on trying to scan photographs.  

Even when the results are within reason, often the size of the resulting scan is huge as compared to the same results in XP with the software provided by the manufacturer.  Just last week I scanned an article out of a magazine to e-mail to a friend.  It was mostly text with a small photograph in one corner.  Using XSane the text was readable, the photo muddy, as usual, and the resulting .pdf file was 2.5 megs in size.  
I booted over to XP and scanned it again, using HP's software, at the same resolution, and the result was perfect.  The text and image where crystal clear and exactly as they looked on the page. Size of the resulting .pdf file? 487k.

There is a commercial product available that gets good reviews and it is called, Vuescan. It doesn't support all scanners, but I think it does support most Epsons. You can download a trial copy from their web site.

What I've finally done is install VirtualBox and into that XP and the HP scanning software.  Long way around the problem, but at least I don't have to boot to XP anymore.
Good Luck.

---

