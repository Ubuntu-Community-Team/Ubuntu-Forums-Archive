---
title: "ChessBase with Wine"
date: 2005-05-04
forum: Wine
---

### Post by thierry on 2005-05-04
Ok so my biggest problem in Linux and the only reason for me to keep a Windows system are my chess software. There are a few packages available in the Universe repository but Linux chess programs lack lots of the functions available in commercial products, and there's no really good looking GUI.

If you want to stick to open source and non commercial software I recommend Eboard (for playing) and Scid (for analysing). You can use these with Crafty, which is the strongest non commercial (but not free) chess engine available in Linux. You can download the .deb files here :

[http://packages.debian.org/unstable/games]("http://packages.debian.org/unstable/games/")

You can have an openings book also. To install I renamed the files to crafty.deb and crafty-book.deb. Then I did sudo dpkg -i crafty.deb and sudo dpkg -i --force overwrite crafty-book.deb. The option in the second command is important because to install a large book you have to overwrite the small one that comes with the Crafty package.

Now the main reason for this post is that I successfully installed Fritz 6 in Ubuntu with Wine (20050310). There's nothing in the forum on this topic yet so this is just aiming at filling a gap.

Fritz 6 works in a fake Windows 98 environment and also by accessing the WinXP files. A small difference in performance : compared to Windows XP Pro its' faster by 3.7 % in Ubuntu !

Only one problem : I couldn't install the newer Junior 9 engine and the Fritz 8 interface. If someone succeeded in that I would really appreciate knowing how. Having to boot in Windows just for one program is kind of sad.

Cheers.

---

### Post by thierry on 2005-05-09
Just some additional information after more testing :

A few functions didn't work in Fritz 6 when I used it in a fake Windows environment : database functions and change engine the most important. You can do just everything if you access the Windows partition. You only need the CD in the drive to launch the program. This should be all about ChessBase.

Now if you want a non commercial good-looking GUI for playing chess in Ubuntu I really recommend this one :

[http://www.playwitharena.com/]("http://www.playwitharena.com/")

Arena is the best Windows-based chess GUI available for free, and it seems to behave very well with Wine. The only drawback is here the performance : it was faster by 16.6 % in Windows. But you can maybe find a better configuration than mine... I should mention also that I have the Microsoft fonts installed. I don't know how it looks without.

The big advantage with this interface is that you're not limited in your choice of engines, there's a whole bunch of chess playing engines you can download and use with it. The strongest being probably ProDeo, which is actually the former commercial Rebel chess program, made available to all after it's author retired from competition and commerce. It's much stronger than Crafty !

Have a look at this page also to download superb graphics for Arena :

[http://members.chello.at/grafixbywilhelm/Index1.html]("http://members.chello.at/grafixbywilhelm/Index1.html")

The Arena project has contributors from all over the world, and I find it very much in the Ubuntu spirit.

Now one more word for those who tried Crafty and got beaten in 15 moves. Check out the following :

[http://www.ex.ac.uk/~dregis/DR/chess.html]("http://www.ex.ac.uk/%7Edregis/DR/chess.html")

This is the best chess course available on the web, you can download it all and use it offline in your favourite browser.

Enjoy !

---

### Post by jodef on 2005-05-09
Nice to find a chess lover like myself I also boot into windows for Fritz 8, as my internet server client I use jin the latest version it runs rather smoothly, as soon as I get some time I am going to try to get it running on Ubuntu.

Maybe any other chess enthusiasts in the forums could post here or maybe let's start a new thread maybe collaboratively we could get a working chess environment in Ubuntu.

---

### Post by thierry on 2005-05-10
I'm still hesitating about installing a KDE desktop just to check out Knights. I started with the idea of limiting myself to Gnome and Fluxbox, but it's really tempting... Any feedback ?

For now I'm very satisfied with Fritz 6. Arena is unfortunately not so responsive.

Knights started to accommodate UCI engines and looks very good in the description and screenshots. It's an ongoing project (as far as I know Eboard and Scid are not really developped anymore) and I think those guys definitely need support !

---

### Post by gil-galad on 2005-05-10
I can't speak for the chess engines, but eboard is actually a pretty good gui for playing chess.  I don't see anything wrong with it.

---

### Post by thierry on 2005-05-10
The look and feel, and the functionality of Arena are just much better. And you can have Crafty play like Anand or Capablanca... Ok this is a gimmick, but more seriously what I'm talking about is a training tool for club players, with powerful opening book and database functions. It's nice to have coaching functions for kids too. All this is available for Windows, and I just hope it will be one day in our OS !

---

### Post by mrbass on 2005-05-10
[QUOTE=thierry]OYou can use these with Crafty, which is the strongest non commercial (but not free) chess engine available in Linux. .[/QUOTE]
```

Rank:Program:                  New:  Comm.Priv.  old.
1    Shredder 7.04             2760    *         2766
2    Gandalf 6.0               2738    *         2582
3    The King 3.33             2733    *         2738
4    DeepSjeng 1.6a            2690    *         2697
5    List 512                  2687              New
6    Ruffian 2.1.0             2682    *         2689
7    Pro Deo 1.0               2672              2724
8    Aristarch 4.50            2666              2710
9    Crafty 19.13-64           2647              2611
10   Maestro 1.08uci           2624         **   2562
11   SmarThink 0.18a-r165      2616              2599
12   WARP 0.65                 2610         **   2631
13   Pharaon 3.1-64            2610              2559
14   Fruit X-12/11             2610              2551
15   Ktulu 6.1 beta 3          2596    *         2512
16   Tao 5.7b06                2578              2598
17   SlowChess Blitz WV        2578              2465
18   Yace 0.99.87              2576              2584
19   Thinker 4.7a              2575              2617
20   Delfi 4.5                 2569              2557
```

Personally I like Yace...anything in the top 50 is an extremely strong engine.  Here's my chess links
[http://www.chessopolis.com/cchess.htm](http://www.chessopolis.com/cchess.htm)
[http://www.tim-mann.org/engines.html](http://www.tim-mann.org/engines.html)
[http://wbec-ridderkerk.nl/](http://wbec-ridderkerk.nl/) (see rankings section)

[http://www.chessbase.com/newsdetail.asp?newsid=1048](http://www.chessbase.com/newsdetail.asp?newsid=1048)

Hmm maybe will have to try List 513 or List 512
```

Program                          Elo    +   -   Games   Score   Av.Op.  Draws

 

  1 Shredder 8                     : 2797   10  11  3048    63.2 %   2703   30.9 %
  2 Shredder 7.04                  : 2772    9  10  3957    61.9 %   2687   30.3 %
  3 X3D Fritz                      : 2770   24  23   640    59.0 %   2707   29.2 %

     

  4 Junior 9.0.0.2                 : 2767   36  33   300    56.8 %   2719   27.7 %
  5 Deep Fritz 7                   : 2766   13  14  1800    61.3 %   2686   29.7 %
  6 Fritz 8 Bilbao                 : 2763   31  25   440    53.2 %   2741   30.9 %
  7 Fritz 8.0.0.23  3-03           : 2760    7   8  6015    60.4 %   2686   28.5 %
  8 Hiarcs 9                       : 2753   11  11  2690    59.3 %   2688   33.3 %
  9 Fritz 7                        : 2752    9  13  3285    67.7 %   2623   25.0 %

 

 11 Deep Fritz 8                   : 2749   15  15  1510    60.9 %   2672   29.7 %
 12 Shredder 7                     : 2739   14  16  1550    62.9 %   2647   27.8 %
 13 Hiarcs8 Bareev                 : 2737   32  29   370    57.0 %   2688   30.3 %
 14 Junior 9 AMD                   : 2734   25  26   560    60.3 %   2661   27.3 %
 15 Gandalf 6.0                    : 2733   44  58   140    48.2 %   2746   30.7 %
 16 Junior 8                       : 2733    9   8  5129    56.9 %   2684   27.0 %
 17 Chess Tiger 15.0               : 2729    9   7  5289    56.0 %   2687   35.3 %
 18 Fritz for Fun 3                : 2717   43  35   240    52.9 %   2697   27.5 %
 19 Shredder Classic               : 2717   18  20  1000    62.5 %   2628   28.1 %
 20 Chess Tiger 14.0               : 2716    9  10  3683    61.1 %   2638   32.3 %
 -

 21 Junior 9.0.0                   : 2716   35  44   220    45.7 %   2746   33.2 %
 22 List 513                       : 2714   18  16  1200    55.0 %   2679   29.9 %
 23 The King 3.23 sel=12           : 2711   11   9  3741    53.6 %   2685   30.6 %
 24 Deep Junior 8.ZX               : 2711   46  58   140    48.9 %   2718   26.4 %
 25 The King 3.33                  : 2709   15  14  1560    57.3 %   2658   29.6 %
 26 Deep Fritz                     : 2705   27  25   530    56.4 %   2660   27.5 %
 27 List 512                       : 2701   11  10  3176    58.7 %   2641   30.4 %
 28 Fritz 6                        : 2700   26  43   370    71.1 %   2544   20.5 %
 29 Hiarcs 8                       : 2698    8   7  6489    54.4 %   2667   32.2 %
 30 Ruffian 2.0 - 2.1.0            : 2693   12  10  3013    53.2 %   2671   31.2 %
```

---

### Post by jodef on 2005-05-13
[QUOTE=thierry]I'm still hesitating about installing a KDE desktop just to check out Knights. I started with the idea of limiting myself to Gnome and Fluxbox, but it's really tempting... Any feedback ?

For now I'm very satisfied with Fritz 6. Arena is unfortunately not so responsive.

Knights started to accommodate UCI engines and looks very good in the description and screenshots. It's an ongoing project (as far as I know Eboard and Scid are not really developped anymore) and I think those guys definitely need support ![/QUOTE]

Knights is still a much underdeveloped interface : looks pretty but not that much functionality past that you would be just as well if not better just using xboard. The project looks promising but that's much farther ahead in the future.

---

### Post by hober on 2005-05-16
Really nice to see chess fans here using linux! I have used only linux for chess already  for last 3-4 years, thought so far that im only one or maybe one of the very few...

About topic i can say only so much that have installed chessbase light with wine. Works ok and i have converted some data in chessbase format to pgn. Unfortunately i dont have any windows commercial chess packages so cant check out. I dont feel any need to buy neither.

Chess programs i usually use are Crafty + Xboard + Scid. This combination does in fact everything i need, although it requires some skills to properly set up and configure. Especially xboard which is powerful interface although not easy to configure. Crafty is strong engine with nice features, for example it can annotate your set of games and produce output to html or pgn. There are also more strong engines like yace. But strongest engine for linux might be new engine called Fruit. I have written for myself xboard tournament manager in java, and in my computer in my tournaments Fruit seems to be most successfull engine. Fruit is UCI engine, one can use it in scid or in xboard via polyglot adapter or directly in jose interface. Jose is nice interface written in java, contains nice 3D chess peaces btw. On more good java interface is jin, this one is for internet chess servers.

I want to say that i dont miss any windows chess program, be it commecial or not.

---

### Post by kb00heda on 2005-05-18
I use Crafty and YACE for analysis in SCID, together with eboard for online chess (FICS, ICC). For now I am using Crafty 19.19 compiled from source (quite easy to set up). It can be fetched from

[ftp://ftp.cis.uab.edu/pub/hyatt/](ftp://ftp.cis.uab.edu/pub/hyatt/)

under "source" (there is also some tablebases and opening books if one is interested). YACE is easy to download from the authors homepage at

[http://home1.stofanet.dk/moq/](http://home1.stofanet.dk/moq/)

The latest version would be Paderborn (though I believe a newer one to exist). Again the source was easy to compile.

I own a couple of Chessbase CD:s from my days of Windows, but have yet to get them going properly under WINE. Perhaps that is an ATI issue? (Everything seems to be...!) The worst thing is the non-ability to read Chessbase format, since my  opening CD:s becomes useless. I have not found any such reader in Linux.

As for the chess engines, it would be nice to get Shredder up and running, which I think is an UCI? But even if it was possible, I do not know how to. If someone could provide some leads, I would be grateful. Fruit was an UCI too?

BTW, Lokasoft sells chess engines as well, and it seems like Ruffian and Deep SJeng offers Linux support with xboard. Have anyone tried them out?

/David

---

### Post by shiv on 2005-06-03
Chessbase 7 and Fritz 8 work well for me with Wine. Simply copy the Chessbase folder from your windows installation in order for it to work. Chessbase 9 works but has glitches. Chessbase 7 is very stable. Fritz 8 has minor glitches.

For the record, I do not have a windows partition anymore.

---

### Post by kb00heda on 2005-06-03
shiv:

OK... but somehow you've got to install Chessbase and Fritz? I mean simply copying a Windows folder can't be sufficient? Doesn't Windows spread the files all over the system? Perhaps I simply didn't understand you! :) 

Anyhow, I used the wine packages from the repositories, i.e., not any manually downloaded and installed CVS version, and never got Shredder 7 to install from the CD. Don't know if there could be a problem with my binary ATI drivers though. What kind of graphics are you using? And which version of wine?

A possible solution might be to install Windows XP using VMware, under which I indeed succeded on installing Shredder, and copy the folder from where. Which one was it again? The C:/Program/Chessbase folder...? (I think it is named that anyway!)

---

### Post by kb00heda on 2005-06-05
Well, I got Fritz and Shredder up and running just the other day, by installing the backport packages (wine, libwine, winetools). Then I configured wine using winetools (which I had not done before). 

Anyhow, although working, I found the interface to be somewhat buggy, to say the least (eventually unistallled Fritz and Shredder). On the other hand my Chessbase Reader works nicely... so I guess I'm happy. :)

---

### Post by kalias on 2005-06-15
Hi!  I am a bit of a chess nut also and was wondering how you guys installed knights, arena, and crafty, they don't seem to be in the synaptic.  I am new to ubuntu so I am not clear on how to add external packages.

Running chessbase with wine sounds interesting. Maybe I will give it a go once I tryout knights and arena.

thanks for the help 

kalias :)

---

### Post by kb00heda on 2005-06-15
About your programs:

1) Knights I think is a KDE application. It is not to find in Hoary, but under Breezy it exists. Perhaps we could ask for a backport? 

2) Crafty is not part of any Ubuntu release (neither is Breezy). I think this is due to licensing issues. However, you can download the source code, from Robert Hyatt's --- the author that is --- FTP site, to get the latest version 19.19, and have it complied yourself. It worked fine for me. If you want I can try to guide you through the steps.

3) Arena is a Windows application. Thus I ran it using Wine. The short comment: It worked quite good, but not perfect. (Also see what the others wrote earlier in the thread.)

4) Chessbase did eventually install via Wine (I had some problems configuring it at first), but as for Arena, the graphics were slow. Nevertheless, I could easily play games on their server, although watching games was quite a pain.

---

### Post by kalias on 2005-06-16
I would definitely be interested in installing crafty.  Installing a program from source code is something that I have not done on Ubuntu or linux for that matter.  If you could post a howto, I will give it a try.

thanks

kalias :)

---

### Post by kb00heda on 2005-06-16
OK, I'll try! (Actually, there will be no real installation, since this procedure only creates an executable to run.)

I did like this:

1) Download the source package

Go to <ftp://ftp.cis.uab.edu/pub/hyatt/>, click on "source" (as you will see there are, e.g., books and tablebases to download as well, if one wants them) and then scroll down to select the latest (and the greatest) "crafty-19.19.tar.gz" version. Have it put at some suitable location (in my case /home/kb00heda/Chess/Crafty/).


2) Untar and compile Crafty

In a terminal execute:

cd /home/kb00heda/Chess/Crafty
tar -xzvf crafty-19.19.tar.gz
cd crafty-19.19
make linux


In fact this is it: the tar command, with options, decompresses and untars the downloaded file, and creates a directory crafty-19.19, where all files are placed, and then "make linux" (have this changed to "make linux-amd64" if you run such a machine --- have a look at "Makefile" for details) eventually (it takes some time to run) produces an executable "crafty".

Now to run the chess engine in xboard type something like:

xboard -fcp ./crafty -fd Chess/Crafty/crafty-19.19

in a terminal (this works for me --- note that "/home/kb00heda" must not be included). There are the possibilities to add opening books and tablebases too, but I can tell you about this later, assuming running Crafty works fine.

Crafty can also be run in a terminal (without any graphics) or, e.g., from within SCID or Jose, which are database programs, that can be used for analyzing games. Actually this is how I mainly use Crafty.

---

### Post by kalias on 2005-06-17
Hey :) Thanks kb00heda it worked great!  I downloaded crafty and compiled it with no problems.  I wasn't able to get it to work with eboard but xboard worked good.  I had problems trying to figure out how to point eboard to it.  The next thing would be the books.  How do I install those?

btw: What do you think of eboard? It seems a little nicer than xboard.

---

### Post by thierry on 2005-06-17
Xboard is very configurable, have a look at this page :

[http://vico.kleinplanet.de/xboard.html]("http://vico.kleinplanet.de/xboard.html")

For the openings I downloaded my repertoire from here :

[http://www.bookup.com/]("http://www.bookup.com/")

Click on "PGN Files by ECO Code" at the bottom of the page. These are high quality games I used to create a Scid database of 320.000 games +, only with the openings I play !

In Scid try these colour combinations :

Fritz 5 :          B:167,126,92  W:231,208,167
Cool:              B:64,128,128  W:215,234,213
Rain:              B:128,128,128 W:223,223,223
Junior 5 :        B:89,105,170  W:167,186,231
Nimzo :          B:175,106,101 W:238,187,187

I use Junior 5, the colours are deeper than the default blue...

I installed crafty and crafty_books as .deb packages, it's much easier (how to on first page). And for analysing together with Yace gives good results :)

---

### Post by kb00heda on 2005-06-17
Thanks for the tip! Now I'm using Vico's dyche2 style, which looks great to me, when running xboard. One small detail: if changing style make sure to create the configuration file ".Xresources" instead of ".Xdefaults". Otherwise it does not work per automatic.

Yes, installing deb-packages is definitely a lot easier. This is a good alternative. The possible drawback is not to get the latest version (I believe the Debian version was 19.15), but on the other hand, looking at the SSDF rating list

[http://web.telia.com/~u85924109/ssdf/list.htm](http://web.telia.com/~u85924109/ssdf/list.htm)

the 18.12 version even beats 19.17!

I must admit I know close to nothing about opening books, but if one insists of using Robert Hyatt's, it can be downloded from

[ftp://ftp.cis.uab.edu/pub/hyatt/books/](ftp://ftp.cis.uab.edu/pub/hyatt/books/)

grabbing the three files book.bin, bookc.bin, and books.bin. I had them placed in ~/Chess/Book (choose whatever is suitable for you). To use the book with Crafty under Xboard I execute

```
xboard -fcp "./crafty bookpath=/home/kb00heda/Chess/Book tbpath=/home/kb00heda/Chess/EGTB" -fd Chess/Crafty/crafty-19.19
``` 
from a terminal to have Crafty throw his whole arsenal at me (huga!). Note that I added an option for endgame tablebases (EGTB). This one should be omitted if they aren't present. I downloaded them (for up to 4 men at least) from the FTP (a bunch of strange-looking *.emd files) as well.

Eboard indeed has descent looks! It seems to be "optimized" for FICS. I sometimes run YACE and Crafty here. In order to get, e.g., Crafty up and running, one launches Eboard and then navigates via

Peer ---> Play against Engine ---> Generic Engine

to enter

```
./crafty bookpath=/home/kb00heda/Chess/Book tbpath=/home/kb00heda/Chess/EGTB
``` 
under "Engine Command ---> Engine Command Line" and

```
~/Chess/Crafty/crafty-19.19
```
under "Directory to Run from". Also check the box "Add to Peer/Engine Bookmarks Menu", which enables you to modify the settings through

Peer ---> Engine Bookmarks ---> Edit Bookmarks

I wanted a nice "Crafty 19.19" caption for easy recognition, and possibly have the time limits changed every now and then. Note, however, that all of the code and settings above were for my machine (and my choices of download folders), so of course one has to modify them accordingly.

I do believe both Xboard (especially since I found out how to improve the looks --- thanks again, thierry!) and Eboard are nice. Probably it is just a matter of taste and habit. Alternatives can be joyful!  :)

---

### Post by kalias on 2005-06-18
Hi guys, thanks for the inputs, I am in the process of trying them out.  I have a really dumb question being that I am new to linux.  Where do I find Xdefaults?  I browsed alot of directories and could not find it.  Do I have to make it?  Drop me a note. 

thanks :)

---

### Post by kb00heda on 2005-06-19
"Xdefaults", despite the name, doesn't exist per default. As a matter of fact we don't want it either! The proper choiche is rather "Xresources" (apparently this goes for Debian based systems). Anyway, you must create it yourself, by opening an editor, modify the file, and save it as ".Xresources" in your home folder. (Note the initial dot indicating the file to be hidden).

My file (~/.Xresources) looks like this:

```
# Two Xboard Themes:

xboard*pixmapDirectory: ~/.chesset/dyche2
#xboard*pixmapDirectory: ~/.chesset/blue


# Another Style:

#xboard*boardSize: 54,01
#xboard*whitePieceColor: #ffffd7
#xboard*blackPieceColor: #1d1d1d
#xboard*lightSquareColor: #ffcc99
#xboard*darkSquareColor: #aa5555
#xboard*highlightSquareColor: yellow
```
That is, I'm using the first line only, whilst the others are commented out (did some testing!). Also, you have to restart X in order for the changes to take place, e.g., by punching CTRL + ALT + backspace (faster than reboot). But then you must login again, so make sure to save all work first!

BTW: to list hidden files in terminals, add an option "a" to "ls", like "ls -a" or "ls -la" (I prefer the output of the latter).

---

### Post by kalias on 2005-06-26
Thanks again kb00heda :) Everything is installed and running.  Xboard looks just like bliztin which is very nice.  Thanks for the help.

---

### Post by shiv on 2005-07-11
Sorry for the late reply. I do not check this forum often. There is a bug in wine when running setup.exe for Chessbase, Shredder and/or Fritz. If you want Shredder to work, I would recommend the Classic version of shredder available from shredderchess.com. The installer and everything works 100% under wine in linux. 

For Shredder (chessbase version), it is best to either install on a windows computer or via vmware and copy the ChessProgram8 folder to your linux partition and simply execute wine ChessProgram8.exe. Use the same procedure for Chessbase 7,8.

In terms of stability and working as well as native, I can vouch for Chessbase 7 and  the Shredder Classic versions of Shredder. Fritz 8 works ok along with Chessbase 9 but has minor glitches.

---

### Post by nickless on 2005-08-26
I would like to find a suitable online chess :) Something I can play with my friends, who still use windows :D
Until now they use [http://www.fritzserver.org/PlayChessSetup.exe](http://www.fritzserver.org/PlayChessSetup.exe) for online chess, but I can't get that to work with wine (well actually I tried cedega 4.4-1)...

---

### Post by ubuntp on 2005-08-29
Shredder 9 is coming out for Linux soon using a Java interface.

---

### Post by fng on 2005-08-30
Is there a good program for a beginner learning chess?  Something to improve my overall game.

---

### Post by TakisX on 2005-09-17
If i put the blue.tar.bz2 file to the directory /home/takisx/download
what line i must put to .Xdefaults ? whatever i try i get 
takisx@nisaki:~$ xboard
xboard: Can't access XPM directory /home/takisx/.chessfig/dyche2
takisx@nisaki:~$
 Thanks

---

### Post by Faj on 2005-10-25
Hello everybody.
[ Fruit (free version 2.1) is rated 2726 here. ](http://f50.parsimony.net/cgi-bin/topic-indent.cgi?Nummer=200321&ThreadNummer=11470) :cool:

---

### Post by truckboy on 2007-08-12
Guys, this is one area that linux is just not there yet. Sorry but no decent gui on any of this stuff compared to even Blitzin. Now that dasher is out windows is still a necessary evil if you want high quality chess stuff. So easy to use and configure. However if/when linux gets the following items for chess I'll throw out windows. 

Namely a good gui with graphical seek, tell, whisper. 
Ability to play all the chessbase video's on it's own, with wine, what's the point your still using window drivers. 
Maybe most important a chess client for ICC that has premove. 
Also support of training programs such as Personal Chess Trainer and Convekta software. 

Till then, linux for all online downloading and web browsing and Windows for the chess part. Of course a shared partition to make it all happen.

---

### Post by Grigorius on 2007-08-14
Well there are some inerfaces for playing on ICC or FICS that look good: varese is one (not that easy to get started with but not that hard to learn either) ... although you can't download varese anymore because the site is offline ... pity. There is one project (that I'm aware of) that is curently developing such an interface (I've even send one of the guys working for this projec my copy of varese ...) if you want to have a look this is their website: [http://tagua.ath.cx/trac/](http://tagua.ath.cx/trac/)
[http://tagua.ath.cx/trac/wiki/Screenshots](http://tagua.ath.cx/trac/wiki/Screenshots)

*However I have to agree ... if your elo is over 2000 (and even if it is not) ... then chessbase is the only serious software for you (and it has by far the best GUI) ... that in combination with rybka - is curenty the best possible chess setup!

**If you are courious (or don't know) about rybka here is their website:
[http://www.rybkachess.com/](http://www.rybkachess.com/)
(rybka also runs on arena but the Fritz interface is the one that gives you it's full power)

---

### Post by thierry on 2007-08-30
The continued development of Scid is worth mentioning here :
 
[http://prolinux.free.fr/scid/](http://prolinux.free.fr/scid/)
 
This is an excellent database programme with powerful functions like Chessbase and Chess Assistant, and now it supports the use of uci engines including Rybka !
 
You will need to compile it from source (depends on Tcl and Tk). I can only recommend it to serious chess players using Linux.
 
There is also a fork of Scid here you might want to try :
 
[http://chessdb.sourceforge.net/](http://chessdb.sourceforge.net/)

---

### Post by Sudheesh on 2007-11-25
Any one here was able to run playchess or ChessbaseLight using wine?.  I tried but got some dll error.  The only thing that I missing in Ubuntu is the playchess client as I use this frequently to play online chess.  If any one was able to run it on Ubuntu please help...

Thanks in advance...

---

### Post by cvaty on 2008-07-21
has anyone had any luck getting fritz trainers to work under wine? 
lemme know.. i cant seem to find a way

---

### Post by thierry on 2008-07-21
In the meantime with VirtualBox OSE you can use all ChessBase products in Ubuntu ([https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)). For example you can install XP in a virtual machine with the Human visual style ([http://fioressj.deviantart.com/art/Human-for-Windows-37743373](http://fioressj.deviantart.com/art/Human-for-Windows-37743373)) and then run ChessBase 9, Fritz 10 or whatever in seamless mode.

---

### Post by carml on 2008-12-15
@ Thierry 

Thanks to your suggestion,now I can run Chessbase SW without rebooting my notebook.
I also tried to install Deep Fritz 8 under Linux using wine and it seem to run,while it's impossible to install newer version because they need Direct x 9,which aren't supported by wine.
I also tried to use Gnu Chess or Crafty,but IMHO they lack on support for inexperienced chess player,whereas a SW like Fritz can be customized to more match one's strength as chess player.:popcorn:

---

### Post by kkady32 on 2008-12-30
hi,i use xboard to play chess in Fics,
about chess engines try toga2,that is stronger as crafty and fruit,and is stronger as rybka2 free,in moment i cannot install deep rybka 3 in wine to try toga2 against rybka3 but maybe with the next wine version that will work.
for tournament i use arena that work in wine and i tested here chess engines.
another interesant chess program in linux is pychess.

---

### Post by Kappity on 2009-01-11
A couple of notes.  I had my old ChessBase program CDs lying around going to waste.  Now about using ChessBase 7 . . .

I found [these instructions]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4071") and this thread.  I believe I understand.  Install CB7 on a Windows computer.  Copy the CB folder and a particular DLL as specified in the given link, and transfer them to my Ubuntu computer.  Well, problem is that I currently don't own any Windows computers, but perhaps I can find a friend who will let me use theirs.  Not wise to do this on a work computer, even if I removed the program right away.

In the mean time Hiarcs 8 installed normally under Wine, and has a scaled back but still powerful version of ChessBase database functions.  I may just stick with that because it gives me the ability to take cbh or cbf files and convert them to pgn, so that I can import them to scid.  I should add, though, that there's some odd bugginess in the Hiarcs interface.  Nothing fatal, but sometimes the arrangement of windows will have shifted if I go to another program and then switch back to the Hiarcs window.

I'm using version 3.6.25 of scid, which has some nice advantages over 3.6.1-2, the version you get through synaptic.  I think the biggest disadvantage compared to ChessBase is that you can only search one database at a time.  Also annotating a game with multiple variations doesn't go quite as smoothly.

On my Macs, I use ExaChess, which is very nice, about CB7 level in functionality, minus some bells and whistles that I never used anyway.  With that, though, when I got a 3,000,000 game mega database in pgn, it couldn't open it.  I had to use scid to break it into 10 separate databases which Exachess could then handle.

*Oh, one last note for what I hope will be my final edit.  I needed the msttcorefonts package to get some of the fonts in Hiarcs to show correctly.*

---

### Post by Kappity on 2009-01-16
I did get ChessBase 7 to work on my computer.  Again, I followed [these instructions]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4071").  I used a borrowed Windows laptop to install it to a USB flash drive, then copied the files to my Wine drive_c as describe in that link.  The operation is a little buggy, but it's usable.  I also installed from my old discs of HIARCS 8, Fritz 7, and Shredder 6 (basically all the same program with different engines), and I can use them all as analysis engines within Chessbase.

---

### Post by Skwerly on 2009-10-23
While I realize this thread is *very* old, I am an avid chess player and figured there are others out there like me, who are just getting into Linux for the first time.  Check this out:

[http://www.shredderchess.com/chess-software/linux.html](http://www.shredderchess.com/chess-software/linux.html)

Also, has anyone installed the *latest *version of SCID successfully?  I keep downloading and get the old and dumb looking green board, not the sophisticated one that they show in the screenshots.  I think it's 4.1 version that I want, but I'm stuck with 3.76 (or something similar).  

Hi, chess players!  :)

---

### Post by kkady32 on 2009-11-06
yes,scid 4.0
u need first to install tcl8.5,tk and tk8.5(i installed tcl8.5-dev too)
after u read Readme.txt and compile:%./configure
                                     %make
                                     %sudo make install
then make a launcher in desktop or type directly:
                                     %/usr/local/bin/scid

enjoy

---

### Post by ricardisimo on 2009-11-18
Another failure. I've been using Ubuntu for five years now, and I still have yet to successfully compile one single application. Not one in five years. Can you believe that?

---

### Post by aasdfasdfg on 2010-02-01
It's a shame that this conversation hasn't been continued, as it seems to be the only one discussion chess programs on these boards. I don't like to revive dead threads, but this one is probably worth it.

Currently I am trying to research chess software in linux. I had previously purchased aquarium with rybka 3 on my windows xp system, and that seems to work nearly perfectly under wine. However, I have also heard that it is useful to analyze with two different engines, to balance out strengths and weaknesses. For this reason I am considering purchasing chessbase with fritz. Before I make this investment, I want to be sure that I can get it to work on linux. Does anyone have experience with this, or other tips about this topic?
Lastly - is development of xboard, eboard, glchess, etc static? I can't seem to tell anymore. It is pretty sad that the most popular thinking game of all time is not adequately supported by open source projects (which appears to be the state of things, as far as I can figure out).

---

### Post by YokoZar on 2010-02-01
Can any of you recommend a free chess engine that plays a believable easy game?  This is something that has been missing in Ubuntu forever.

---

### Post by howefield on 2010-02-01
> **YokoZar said:**
> ...believable easy game?..

Highly subjective phrase.

I'm not sure there is such a thing for any platform, never mind Ubuntu.

If you want believable and easy, play against real people online, in my humble opinion.

---

### Post by thierry on 2010-02-02
@ aasdfasdfg:
 
For the purpose of analizing I wouldn't recommend to buy Fritz. The latest version brings mainly cosmetic improvements the engine itself is far to be amongst the strongest. Moreover it won't work in Wine. Buying Shredder for Linux is not a very good idea either (unless you like the gui) because Stefan Meyer-Kahlen admits himself that the Linux compiles are a little bit slower than their Windows counterparts. Here are some benchmarks from a chess forum:> 
1. Windows version of Deep Shredder running in Wine in Linux 32 bit (this is the same performance or better as native Windows) 
2. Linux version of Deep Shredder 64 bit 
3. Linux version of Deep Shredder 32 bit 

2 is 5% slower than 1. 3 is 20% slower than 1. 

This is because SMK compiled with gcc for Linux and not ICC which would give him better speeds than the Microsoft visual studio compiler. 

The performance of running engines with WINE in linux is comparable or sometimes even better than native windows. 

Conclusion, though native linux version is a nice to have, the performance is not as good as running the windows version via WINE in linux. However, it is a good option for those you do not want to install WINE.
 
The best chess setup you can have now for analyzing in Linux is Rybka Aquarium running in Wine + the free Stockfish or Firebird ([http://www.chesslogik.com/FireBird.htm](http://www.chesslogik.com/FireBird.htm)) for example.
 
@ YokoZar:
 
The Phalanx engine is in the repositories and you can adjust it's strength. > 
To change Phalanx's strength, use the following options:
-e *level* -- this can vary from 0 to 100, with 0 being the toughest level
-b [+/-] -- turns opening book on and off
-f [search time in seconds] -- time Phalanx takes to search for a move
For a complete list command-line options, see the README file that comes along with the source.
 
Cheers

---

### Post by aasdfasdfg on 2010-05-29
Thank for your reply thierry - I had forgotten to check these forums and didn't see your post, but as soon as I found out about FireBird that's the exact setup I've been using for the past several months.

[SIZE=3]What do people on the Ubuntu boards think about FireBird and the controversies surrounding it?[/SIZE]

I am considering starting my own launchpad ppa to provide a FireBird package.

---

### Post by smartidiot on 2010-07-03
Stockfish is so strong that I don't feel a need to use an engine with problems.  

Personally - I have been using SCID and Stockfish.  Running VirtualBox so I can run Chess Position Trainer.

---

### Post by Msaurus on 2010-09-23
Hello there, I managed to run chessbase light 9 with wine and to play and watch games in the playchess server.

Is there someone still interested in running Chessbase light under wine and play in playchess.com?

Let me know and I'll post how to setup your wine.

:guitar:

---

### Post by vams on 2011-02-11
can you explain how you did it

---

### Post by smartidiot on 2011-03-19
I did a post on how to install SCID and Stockfish in Ubuntu Linux on my blog.

Hope it helps some people be able to learn how to play chess better.

[Attacking Chess - Studying Chess on Linux]("http://attackingchess.blogspot.com/2011/03/studying-chess-on-ubuntu-linux-part-1.html")

---

### Post by kayve on 2011-06-16
about  how you are having great success running ChessBase and Engines on your  Ubuntu machine.  I fried my Windoze disk and I was hoping to get my  chess things going on Ubuntu.  I have a Hiarcs 10 disk I was trying to  install and I don't know what ChessBase somebody pirated for me. 

email me at [email]kayvey@gmail.com[/email]

---

