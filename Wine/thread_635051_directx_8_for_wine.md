---
title: "directx 8 for wine"
date: 2007-12-08
forum: Wine
---

### Post by linux noooob on 2007-12-08
So i found this website with a beta release of direct x 8 for wine. i downloaded it and i really don't know how i install it?? the file is a .patch file that is compressed in a .bz2 file.

[http://directxwine.sourceforge.net/]("http://directxwine.sourceforge.net/")

---

### Post by hikaricore on 2007-12-08
Unless you need it for a certain program/game to run I'd advise avoiding this.

DirectX is mostly already implemented and functional /w WINE.

---

### Post by cogadh on 2007-12-08
That is woefully out of date, it hasn't been updated in over two years. The DX implementation already built into Wine is way more advanced than that. Don't even bother with it.

---

### Post by linux noooob on 2007-12-08
i was told direct x doesn't work in wine and that is why 3d games don't work :confused:

---

### Post by Marrshu on 2007-12-08
> **linux noooob said:**
> i was told direct x doesn't work in wine and that is why 3d games don't work :confused:

Whoever told you that was lying or misinformed. Wine has DirectX working quite well... of course it could be better, but it's certainly better then anyone could have expected.

---

### Post by hikaricore on 2007-12-08
> **linux noooob said:**
> i was told direct x doesn't work in wine and that is why 3d games don't work :confused:

You were misinformed.

Not all aspects of every version of DirectX are fully functional.
However many of them are and they work near perfectly.

What exactly are you trying to play?
And did you look here: [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by cogadh on 2007-12-08
> **linux noooob said:**
> i was told direct x doesn't work in wine and that is why 3d games don't work :confused:
You need to stop listening to whoever told you that immediately, they have no idea what they are talking about. Many 3D games work fine with the default Wine installation. With a little Wine configuration and customization, many more will work nearly flawlessly. The list of Windows 3D games that I can play on Wine is pretty good and there are others here who play even more than I do:

Half-Life 2 (plus Episode 1 and Lost Coast)
Counter Strike: Source (though I don't really play it much)
Hitman 2
Star Wars: Knights of the Old Republic 1 and 2
Freedom Force
GTA3 and GTA Vice City
Advent Rising
American McGee's Alice
Star Trek Armada 2 (still working on getting 1 to work)
Call of Duty
Star Wars Jedi Knight Jedi Outcast and Jedi Academy

There are more that I have run in Wine, but don't run anymore (got bored with them). Just about half of my entire Windows game library runs in Wine perfectly or nearly perfectly. I only seem to have problems running brand new games or really, really old games (ones that don't work in Windows anymore either).

---

### Post by linux noooob on 2007-12-10
then why can't it run games like flyff or maplestory??

---

### Post by cogadh on 2007-12-10
Those games do have issues running in Wine that have nothing to do with DirectX. Both games use the anti-cheat software GameGuard, which will not work in Wine. GameGuard runs as a driver in Windows and Windows drivers will not work in Wine.

---

### Post by hikaricore on 2007-12-10
Maplestory uses GameGuard, which is anticheat software.  This stops dead in its tracks /w WINE mostly because of the nature of such software.
If you look at the version before GameGuard was implemented we atleast got a title screen.

It's almost useless for the WINE devs to focus on such software as anything they accomplish is likely to be broken by the next release, IE many know how bad punkbuster has been for running some games via WINE.

As for Fly For Fun, I'm not familiar with this game so I can't really comment.

---

### Post by linux noooob on 2007-12-11
thats ok^_^  and i bet there is someway to get game guard to work but as long as direct X 8 works i am happy.

---

### Post by hikaricore on 2007-12-11
As of now there is not a way to get gameguard working, and again directx works fine.

---

### Post by cogadh on 2007-12-11
And there are no plans to get GameGuard to work in Wine. As I said, GameGuard works by installing a virtual driver into Windows, which runs at boot time and sits waiting for you to run a GameGuard protected game, then it goes into action and does its thing. Just as there are no facilities in place in Wine to allow Windows hardware drivers to run, there is nothing in place to allow a game protection virtual driver to run. This affects more than just GameGuard, it also prevents the StarForce CD copy protection system from working.

---

### Post by Beren Camlost on 2007-12-11
It is perhaps worth to mention that "anti-cheat" software such as GameGuard and SecuRom creates quite a lot of issues for Windows users too that got a legal copy of the games. Such software is often buggy and in most cases it leads to even more cracked .exe's floating about. Such software is useless at best and in practise it works pretty much the opposite of intended.

---

### Post by cogadh on 2007-12-11
SecuROM is really not that bad (and it is not anti-cheat software), all it does is run a check for the presence of the real CD in the drive when the game is run. It's non-invasive and doesn't break anything, since the protection scheme is built right into the game's executable. Of course, it is also really easy to defeat. 

GameGuard and StarForce, on the other hand, both install a virtual driver on your system that stays there and runs constantly, even if you uninstall the product that they originally came with. GameGuard actually behaves much like a rootkit, which makes some Windows anti-virus products (the good ones at least) detect it as a virus attack. In the case of StarForce, its virtual driver has been known to physically break CD-ROM drives, because of the way it inteferes with communication between the system and drive's own drivers. It has also been shown that StarForce introduces a security hole into Windows systems when used under a limited user account (gotta love Windows "security").

Of course, none of this would even be required if publishers didn't charge a ridiculous $50 to $60  for each game. That's just plain greedy (does anyone really think that it cost them even close to $50 per copy to design, code and produce any game?). That greed ends up breeding piracy which ends up creating the need for copy protection and we get stuck with games that should be legally playable on Linux through Wine, but are not.

---

### Post by Mblackwell on 2007-12-12
> **cogadh said:**
> SecuROM is really not that bad (and it is not anti-cheat software), all it does is run a check for the presence of the real CD in the drive when the game is run. It's non-invasive and doesn't break anything, since the protection scheme is built right into the game's executable. Of course, it is also really easy to defeat. 

GameGuard and StarForce, on the other hand, both install a virtual driver on your system that stays there and runs constantly, even if you uninstall the product that they originally came with. GameGuard actually behaves much like a rootkit, which makes some Windows anti-virus products (the good ones at least) detect it as a virus attack. In the case of StarForce, its virtual driver has been known to physically break CD-ROM drives, because of the way it inteferes with communication between the system and drive's own drivers. It has also been shown that StarForce introduces a security hole into Windows systems when used under a limited user account (gotta love Windows "security").

Of course, none of this would even be required if publishers didn't charge a ridiculous $50 to $60  for each game. That's just plain greedy (does anyone really think that it cost them even close to $50 per copy to design, code and produce any game?). That greed ends up breeding piracy which ends up creating the need for copy protection and we get stuck with games that should be legally playable on Linux through Wine, but are not.

Actually, it can cost millions of dollars to produce a game, and the game developers usually break even... if they're lucky.

Yes it's true, you have to actually *pay people enough money to live* so they can spend all of their time developing a game instead of doing other work. Even a small development team of 20-25 people, if you pay each of them something like 40K per year, that's 800K right there just in salaries. Then you have the actual costs of running all of the facilities, equipment costs, etc. Then there's the extra people that get hired short term for bug testing, etc. There's administrative fees, and then there's the actual production of the software itself. Copying the Gold master, designing the artwork, writing the manuals, printing all of the units, and getting them on to store shelves. Then there's advertising costs, support costs, etc.

So yes it costs quite a bit to produce games of high caliber that will actually do well on the market.

---

### Post by cogadh on 2007-12-12
Your assuming that a developer or publisher only has one game in production at a time and all of their costs are being paid for by that one game. In most cases, this is simply not true. The salaries of those employees are paid for out of the total profits of the company, not out of the profits from the single game those developers are working on. The same is true of covering the building and equipment costs. About the only thing that you could say is covered directly by the sales of a game are the advertising and physical production costs of that game. Advertising is very expensive, packaging can be expensive, shipping is not, burning CDs or DVDs is definitely not.

When you look at the total sales of a AAA game, like Halo 3 for example, at $50 bucks a copy, 1.8 million units in sales (which the game easily did before the first hour after its release), thats 90 million dollars. I guarantee you it did not cost them more than 3 or 4 million dollars to develop the game and knowing MS, they probably spent more on advertising and packaging than the actual development (I think I remember reading that they spent somewhere close to 10 million). The game covered its costs and made a *huge* profit before the end of business on the first day of sales!

Granted, Halo is an extreme example, but for any AAA game, selling a million units or more is not uncommon. There is no way you can convince me that up to 100 million dollars worth of sales *per game* is only just "breaking even".

Then theres the new content delivery systems, like Steam. Why in the world is a brand new game $50 on Steam and in the stores? There is no production involved in selling a game on Steam (i.e. no CDs to burn, no packaging to make, no shipping costs, etc.). The only reason that they keep the cost that high is greed, plain and simple. The publishers and developers have realized that the majority of consumers are willing to pay almost anything for our entertainment, and they are more than willing to take advantage of that.

The game industry currently makes almost as much, if not more profit than Hollywood. Everybody knows that movie theaters overcharge for tickets and DVDs are an incredible scam (do we really need multiple versions of "Lord of the Rings"? Director's cut, original release, widescreen, fullscreen, boxed set, special edition, extra gay edition...). Why is it so hard to see that the game industry has learned from Hollywood and is basically perpetrating the same scam?

---

### Post by angryfirelord on 2007-12-12
Up until recently, it used to be that whenever a game came out, it would drop to a more reasonable price. I remember when Warcraft III was released, it was something like $50. However, after the first year it dropped to something like $30 and continued to fall afterwards. (now you can get it dirt cheap) What we're seeing is that games aren't really falling in price, in fact the popular titles (especially for consoles) are *staying* at that $50 or $60 price. I don't mind paying and supporting developers, but I'm not going to do it if the pricing is absurd.

---

### Post by Mblackwell on 2007-12-13
> **cogadh said:**
> Your assuming that a developer or publisher only has one game in production at a time and all of their costs are being paid for by that one game. In most cases, this is simply not true. The salaries of those employees are paid for out of the total profits of the company, not out of the profits from the single game those developers are working on. The same is true of covering the building and equipment costs. About the only thing that you could say is covered directly by the sales of a game are the advertising and physical production costs of that game. Advertising is very expensive, packaging can be expensive, shipping is not, burning CDs or DVDs is definitely not.

When you look at the total sales of a AAA game, like Halo 3 for example, at $50 bucks a copy, 1.8 million units in sales (which the game easily did before the first hour after its release), thats 90 million dollars. I guarantee you it did not cost them more than 3 or 4 million dollars to develop the game and knowing MS, they probably spent more on advertising and packaging than the actual development (I think I remember reading that they spent somewhere close to 10 million). The game covered its costs and made a *huge* profit before the end of business on the first day of sales!

Granted, Halo is an extreme example, but for any AAA game, selling a million units or more is not uncommon. There is no way you can convince me that up to 100 million dollars worth of sales *per game* is only just "breaking even".

Then theres the new content delivery systems, like Steam. Why in the world is a brand new game $50 on Steam and in the stores? There is no production involved in selling a game on Steam (i.e. no CDs to burn, no packaging to make, no shipping costs, etc.). The only reason that they keep the cost that high is greed, plain and simple. The publishers and developers have realized that the majority of consumers are willing to pay almost anything for our entertainment, and they are more than willing to take advantage of that.

The game industry currently makes almost as much, if not more profit than Hollywood. Everybody knows that movie theaters overcharge for tickets and DVDs are an incredible scam (do we really need multiple versions of "Lord of the Rings"? Director's cut, original release, widescreen, fullscreen, boxed set, special edition, extra gay edition...). Why is it so hard to see that the game industry has learned from Hollywood and is basically perpetrating the same scam?

I don't think you realize how game development works. The developers don't make a lot of money, they basically contract out on a loan (similar to how it works with musicians in relation to record contracts) and have to make up the costs to the publisher back in games sales. Most games don't sell in the millions of units, a lot are lucky to even make 200K unit sales. That's why you see many companies posting losses even after releasing lots of games and making decent sales.

You obviously have no idea what the average cost of game development is, which has skyrocketed and is currently (for a "next-gen" game with competitive graphics/art direction) on an average of $20 million or higher. 

I don't disagree that publishers take advantage of consumers, but game development really does cost a lot, and developers often get the shaft. The publishers do have to make up the costs, although I agree with the previous poster that they are currently not lowering game prices anymore as they should be. Some games (like Doom 3) see lowered prices, but years ago a trend started with Valve where they discovered by changing labels on the box, or adding some things in the box, you could keep game prices up almost indefinitely, at least in the 30+ dollar range for years and years.

---

### Post by cogadh on 2007-12-13
I don't understand? You obviously don't, you are spouting numbers that just don't reflect the facts. In 2006, the game industry did over 12.5 * billion* dollars in US sales, with the software alone accounting for 7.4 billion dollars of those sales.  The only area of the game industry that actually took any loss was hardware sales (i.e. the next gen consoles themselves). 

All of the top 50 best selling games for the year sold over 500 thousand units each, while all of the top 20 best selling games sold over 1 million units each. The year's top selling title, Madden '07, sold almost 2 million units in December alone and ended up selling over 6.7 million units for the year. All told, there were just over 240 million game software units sold for the year. That's just in the United States. Those numbers don't even take into account European or Japanese sales, which could easily double the sales numbers for almost all of those games.

Now, I could see small indie developers posting losses due to their costs, they don't have the big publishers to foot the advertising and distribution bills, but I'm not talking about those guys. If they charge $50 for a game, they are doing to survive, but I've never actually seen an indie game sold for that much. When Activision, EA, Microsoft or any of the other big publisher/developer companies are charging that kind of money or more, it is just padding their wallets, nothing more. 

Yes, development costs have increased, inflation and the ongoing console war does that. But I am certain that much of the excessive inflated cost of recent years is not actually the cost of making or distributing the game, but the cost of *marketing* the game. Since the industry makes so much money now, there is a real push from each publisher to get the biggest chunk of those sales for their latest "killer app". So they spend twice as much and more on advertisement to shove their new games down our throats. 

The sad part is, you can usually tell when  game is really going to suck; it has way more advertising that all the others. The amount of advertising is inversely proportional to the quality of the game. When a game is made well, it can stand on its own merits with only a reasonable amount advertising and therefore reasonable costs, which should be reflected in a reasonable price, but it is not.

[http://www.gamespot.com/news/6164101.html](http://www.gamespot.com/news/6164101.html)
[http://www.theesa.com/facts/sales_genre_data.php](http://www.theesa.com/facts/sales_genre_data.php)
[http://www.next-gen.biz/index.php?option=com_content&task=view&id=4691&Itemid=46&limit=1&limitstart=0](http://www.next-gen.biz/index.php?option=com_content&task=view&id=4691&Itemid=46&limit=1&limitstart=0)

---

### Post by keelx on 2011-07-06
The directX implementation in wine is fine. If you like to play games without textures and at around 5-10 frames-per-second. ](*,)

---

