---
title: "Firefox32 Bookmark/URL Problem"
date: 2006-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-02-04
I have Firefox32 installed in chroot. I did so in order to get RealPlayer and Flash working, and they do now. Awesome cool.

But yesterday, while at the university, suddenly half my bookmarks were not working. Now, that is totally weird, because if there was a DNS problem, wouldn't it affect all bookmarks? Interestingly, among the bookmarks that were not working were 100% of the 30-odd internet streaming radio stations that I had saved. They had all worked fine from the university before. And they all worked from home too, where I have cable.

Another weirditude: I got an e-mail about a reply to a topic I had posted in an OpenOffice.org forum, with a link:

[http://www.oooforum.org/forum/viewtopic.phtml?p=105450#105450](http://www.oooforum.org/forum/viewtopic.phtml?p=105450#105450)

But when I clicked on the link in Evolution, Firefox took me to the University of Arizona home page! I know I never visited that site ever before.

[http://www.arizona.edu/](http://www.arizona.edu/)

Now, tell me, where in that oooforum.org link is there any mention of Arizona? This is too weird.

But then I copied the link in Evolution and pasted it into the URL bar in a new tab in Firefox, and Firefox dutifully went straight to OpenOffice.org and loaded the page with the forum entry. It's just the Evolution-Firefox connection that is somehow hosed. But how bizarre! Evolution is telling Firefox to take me to the University of Arizona instead of OO.o? Where the hell did Evolution get that notion?

So now I am at home and on cable. And the same problems persist, exactly as when I was at the university yesterday. Clicking on the link in Evolution opens a tab in Firefox and delivers me to the University of Arizona. And none of the radio station links work, even though they used to work both at home and everywhere else.

I have also shut the computer down and restarted it, but no change. Note that I am running only Firefox32 in chroot. I changed the target in the Applications menu to read "dchroot -d firefox," so when I run Firefox it's definitely the version that I installed in chroot.

Does anyone have any idea what might have happened? Any ideas at all?

---

