---
title: "Getting Terminal output longer than allowed"
date: 2016-01-19
forum: Wine
---

### Post by mr-good555 on 2016-01-19
Basically, I have this problem with this program, and I'm trying to get the Terminal Output, so I can open a different post once I have the details. A huge number of "fixme"s appear, and seem to loop, far beyond what's available for Terminal to keep (scrolling to the top, I no longer see previous messages, or even the command I used).

I've also tried to catch the output into a text file.

```
cd "path/to/program"
wine program.exe > output.log
```

The program runs as normal, complete with the problem I encountered, but although the file was created, it is empty.

I'm not sure if this is specifically a problem for Wine, but I'm hoping to get help for a Wine function anyway. So might as well here.

Thank you for your time.

---

### Post by steeldriver on 2016-01-19
If you are still seeing the "fixmes" in the terminal after redirecting the output to a file, then it suggests they are being sent to the error stream rather than the output stream - try either

```

wine program.exe > output.log 2>&1

```
or
```

wine program.exe 2> output.log

```

Alternately, you could paginate the output

```

wine program.exe 2>&1 | lesss

```

---

### Post by mr-good555 on 2016-01-20
Although you're right, it's worse than I thought.

The file it made was 3GB. It took about 5 minutes to load it in leafpad. I'm gonna have to find a different way around this problem.

Many thanks though.

---

### Post by steeldriver on 2016-01-20
I wouldn't try to load it in a text editor - again, `less` might be your friend here as it will allow you to 'page through' the file

```

less output.log

```

Alternatively, if youknow what you're looking foryou could use `grep`

```

grep '*search string*' output.log

```

---

