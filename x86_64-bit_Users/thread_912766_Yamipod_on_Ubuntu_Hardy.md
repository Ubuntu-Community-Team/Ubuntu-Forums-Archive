---
title: "Yamipod on Ubuntu Hardy"
date: 2008-09-07
forum: x86 64-bit Users
---

### Post by nbhat on 2008-09-07
I am trying to use Yamipod. As per the [Yamipod forum]("http://www.yamipod.com/main/modules/newbb/viewtopic.php?topic_id=1546&forum=2") following additional libraries required on 64 bit
ia32-libs, lib32gcc1, libc6i386, lib32asound2, lib32stdc++6

I see that all the libraries except for libc6i386 are already there on my machine but I am not able to find libc6i386 via apt-get or synpatics manager. Any pointer to find the same would be useful.

I also checked to make sure that I have libcups.so.2 based on the [previous posts]("http://ubuntuforums.org/showthread.php?t=83024") related to a bug in realbasic on 64 bit.

---

### Post by Thelasko on 2008-09-08
It should be there.  [libc6-i386]("http://packages.ubuntu.com/hardy/libc6-i386")

---

### Post by nbhat on 2008-09-08
Thanks for pointing out! I found that its already installed in hardy.

Wondering what could be wrong ?

Anybody running Yamipod on Hardy on AMD64 ?
I am getting following error while trying to run ..

Cannot find libgstreamer
Cannot find libxine
Segmentation fault

---

### Post by Thelasko on 2008-09-08
> Cannot find libgstreamer
Cannot find libxine
Is libgstreamer and libxine installed?  If they are, it could be that Yamipod is looking in the wrong place for them.

---

### Post by nbhat on 2008-09-08
Yes libgstreamer and libxine are installed. I checked yamipod forums to see similar problems. For those who are using AMD64 it was suggested to install ia32-libs, lib32gcc1, libc6i386, lib32asound2, lib32stdc++6, libc6-i386 . And I found all of these are installed as well. 

I did ldd on Yamipod binary it does not list libgstreamer or libxine

---

### Post by Thelasko on 2008-09-08
If you're just trying to connect to an iPod, Amarok and Rhythmbox are supposed to support that.

---

### Post by war4game on 2008-09-08
ST. PAUL, Minn. - Not merely a Republican. Not merely a candidate. John McCain cast himself as a leader for all Americans, regardless of party or status. ADVERTISEMENT After several days of Democratic bashing by his supporters, the Arizona senator struck a nonpartisan stance and promised that he wouldn't be bound by political party in the White House as he accepted the GOP presidential nomination Thursday before thousands of Republican loyalists."We are fellow Americans, an association that means more to me than any other," McCain told the Republican Convention, deriding "constant partisan rancor" that causes Washington gridlock. He rejected those in Washington who he said "work for themselves and not you."McCain marched through a series of big issues &#8212; defense, taxes, education, energy independence among them &#8212; without offering many specifics. Instead, there were generic promises to "make it better," of "rewarding hard work," and the like.He marked the pinnacle of his political life by delivering a speech in his preferred setting &#8212; surrounded by people. In this case, they were the GOP convention delegates who granted him the nomination that had eluded him in 2000."I don't work for a party," he declared. "I don't work for a special interest. I don't work for myself. I work for you."The GOP nominee was making an aggressive play for voters from across the political spectrum &#8212; Republicans, independents and Democrats. And even as he preached bipartisanship, McCain served up Republican dogma to the willing crowd, on abortion, taxes, national security, oil drilling.His trick was to appeal to his conservative supporters without turning off independents.On the convention's fourth and final night, McCain's campaign transformed the stage at the Xcel Energy Center to put him in a setting in which he typically performs best. He spoke from a podium at the end of a lighted catwalk extending into the crowd, hugged by the battleground delegations of Ohio, Missouri, Michigan, Pennsylvania, Florida and Minnesota. Behind him, a hulking video screen displayed a breeze-blown flag.Even so, speechmaking has never been McCain's strong point, and his delivery Thursday clearly paled next to that of his running mate or his Democratic rivals. Pausing after each idea, McCain's delivery seemed better suited to a speech in the Senate. Barack Obama, his running mate, Joe Biden and GOP vice presidential candidate Sarah Palin had been riveting; McCain was more laundry list.The delegates didn't seem to mind if their nominee lacked Obama's rhetorical polish."This guy has more experience in his little pinkie from speaking in the Senate than Obama will ever have," said Colorado delegate Gabriel Schwartz. "It was a much better speech for what it said and the way he delivered it honestly than some smooth speech from someone who can't deliver."Seeking to give voters wary of Obama an acceptable alternative, McCain praised his Democratic rival and said that Obama's supporters had his respect and admiration."But let there be no doubt, my friends, we're going to win this election," McCain said, "and after we've won, we're going to reach out our hand to any willing patriot, make this government start working for you again, and get this country back on the road to prosperity and peace."In an arena plastered with his "Country First" slogan, McCain told the GOP's most faithful supporters that he's repeatedly worked with members of both parties to fix the country's ills."That's how I will govern as president," he said. "I will reach out my hand to anyone to help me get this country moving again. I have that record and the scars to prove it. Senator Obama does not."It was a rare mention of his rival; McCain used Obama's name only six times. And, he mentioned the words Republicans and Democrats mainly in tandem, urging the two sides to work together and trying to show how he was unafraid to take on both parties to force change.McCain ended his 50-minute speech with a call to arms: He exhorted, "Fight with me. Fight with me," as the crowd's roar of approval drowned out his voice. With music blaring and balloons cascading, McCain stopped to savor the moment, then stepped down from the podium and was swallowed up among the cheering delegates. For all his talk of reaching across the aisle, McCain got in his jabs at Obama. After all, there are only two months until Election Day. He said Obama would raise taxes, close markets, increase government spending, eliminate jobs. He criticized Obama on energy, health care, and education policies. The audience was clearly hungry for it: They booed Obama after every criticism, though there were relatively few. McCain mostly refrained from the brass-knuckled rhetoric that marked Obama's speech exactly one week earlier.  [wow gold](http://my4game.com/)[cheap wow gold](http://my4game.com/)[wow gold](http://my4game.com/)[buy wow gold](http://my4game.com/)[warcraft gold](http://my4game.com/)Perhaps the Republican's sharpest hit came without even a mention of his Democratic rival. "I'm not running for president because I think I'm blessed with such personal greatness that history has anointed me to save our country in its hour of need," McCain mocked. "My country saved me. My country saved me, and I cannot forget it. And I will fight for her for as long as I draw breath, so help me God." McCain has cast Obama as a presumptuous candidate, and his campaign has likened the Democrat to a would-be messiah. The Arizona senator also issued a warning "to the old, big-spending, do-nothing, me-first, country-second Washington crowd: Change is coming." That, too, was an indirect Obama reference. McCain has suggested his Democratic rival puts personal ambition above the country. In his comments, McCain left it to his audience to connect the dots. Certainly, McCain's speech wasn't as sharp as Palin's address to the delegates the night before &#8212; or a host of other speakers who came before him. Their speeches were filled with biting attacks on Obama and his Democrats. McCain, however, can't risk turning off undecided swing voters, many of whom recoil at negative campaigning. "Americans want us to stop yelling at each other," he added, trying to use the disruption to his advantage.

---

### Post by nbhat on 2008-09-09
I got banshee to read the songs. But now I want to try to put songs into ipod as well. So I am trying both Yamipod as well as Amarok. Both I am having issues. But for Amarok I am yet go through the posts and try out!

---

