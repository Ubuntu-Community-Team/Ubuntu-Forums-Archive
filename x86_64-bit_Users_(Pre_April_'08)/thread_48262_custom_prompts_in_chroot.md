---
title: "custom prompts in chroot?"
date: 2005-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by nwillis on 2005-07-11
I've been running 64 bit for two weeks now.  Life is good.

Life is even good within my little chroot jail, where AdobeReader and Flash dance and sing.

But ... one little thing is nagging me,  I use a custom bash prompt like all right-thinking people.  But since (following the 32b chroot howto instructions) I have the same $HOME in the jail and out in the real 64b world, I have the same .bashrc and thus the same prompt.  Sometimes with too many terminal tabs open (too many may be equal to 1) I forget which is which and mistype a command in the wrong environment.

Nothing lifethreatening, but it got me thinking: how can set a different shell prompt for the two environs?  Is there some sh scripting trick I could use, and maybe change the color to an evil red when opening a shell in 32b, thus reminding me which is which?

If you're a scripting wizard, what are your ideas?

Maybe it would be easier to check and see if you're NOT in chroot jail somehow; I thought about maybe checking for the existence of some file that's in one root filesystem but not the other, then conditionally setting the prompt based on that.  Think that would work?

Nate

---

### Post by varunus on 2005-07-11
You could always put a condition in your .bashrc that checks for the presence of some file that's only in the chroot (or only in the 64 bit version) and then changes the P1 variable accordingly.  (Not the cleanest way, but it works.)  I'm not sure how this works for chroot, but does uname -m return different things inside and outside the chroot?  If it does, you could set up a conditional with that.

Good luck.

---

### Post by nwillis on 2005-07-15
uname returns the same thing :(

Which it ought to, I suppose -- it's the same kernel.  Thanks fo the suggestion though.

So let's pursue this file-checking thing.  I'm no scripting artist; what would be the fastest way to check for the existence of a file?  

(And I think /chroot itself is the obvious choice, I have no chroot inside the chroot and anything else could be duplicated coincidentally).
N

---

### Post by nwillis on 2005-07-22
OK, here's what I actually did (for the sake of posterity).  Note that I know as close to absolute-zero about bash scripting as possible.  So there are probably a hundred situations where this won't work or reasons why it will destroy your computer and ruin your future financially.

in .bashrc:
[INDENT]if [ -f "/chroot" ]
then
  echo "64-bit shell"
else
  echo "32-bit shell"
fi[/INDENT]

... and that seems to correctly identify which environ you're in.  There's ehll to pay if you're stupid enough to create a /chroot directory INSIDE the /chroot directory, but that's an exercise left for the reader.

Of course, in my actual .bashrc I changed the prompt color in the "then"/"else" blocks, but that's a confusing mishmash of escape characters and I was afraid it wouldn't render correctly, so anyone who does this in the future -- you'll have to look that up elsewhere.

Enjoy
N

---

### Post by negatory on 2005-07-23
That didn't work for me...but I've changed the "if [ -e "/lib64/" ]" and it worked like a charm!
Thanks
Pedro Carrico

---

