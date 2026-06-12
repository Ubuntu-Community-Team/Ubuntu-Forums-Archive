---
title: "use of `cat ...`"
date: 2006-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by incubus on 2006-06-19
I have a list of the programs I always install in Ubuntu, so all I have to do is:

```

sudo apt-get install `cat list`

```

Yesterday I got a Pentium D and installed Ubuntu amd64 to give it a try. I noticed, however, that that command doesn't work as expected.  I get an error message saying that the entry was not found in the repositories.

After playing around for a while, I noticed that `...` never does what we would expect it to do.  I lie.  It seems to do, but its output is not correctly processed by the other commands.

Is this just me or it's a deliberated change?

Thanks,
incubus

PS: By the way, what's the name of the ` symbol? I can't remember!

---

### Post by incubus on 2006-06-19
This is very weird.
If I recreate the file in my amd64 system (I really mean copy & paste), it works.

I'm probably missing something, but well... it works.

incubus

---

### Post by rydow on 2006-06-21
The name is back tick.

---

### Post by incubus on 2006-06-21
Thank you.  

Now I know why I couldn't remember: I didn't know it.

incubus

---

