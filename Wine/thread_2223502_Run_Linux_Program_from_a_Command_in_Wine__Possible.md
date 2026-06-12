---
title: "Run Linux Program from a Command in Wine?  Possible?"
date: 2014-05-11
forum: Wine
---

### Post by lah-ca on 2014-05-11
I am using an old Windows version of Mail Washer in Wine.  I works quite well, better than in Win7 actually.  

It has an option to launch the default mail application after processing the contents of a POP mailbox; this does not work in Wine because there is no default mail program in Wine, nor however does it work in Win7.  

The launch option, however, can be a command line string.  Is there a way of launching Thunderbird  or Evolution from a command line string in Wine?

Thx.

---

### Post by pendrokar on 2014-05-12
Yes, if you can make it point to an executable shell script.

Here is an example.
```
#!/bin/sh


$1 "$2"
echo "Running $1 with argument $2"
exit 0
```
So giving this executable the argument 'gimp' would make Ubuntu launch gimp.

---

### Post by lah-ca on 2014-05-15
> **pendrokar said:**
> Yes, if you can make it point to an executable shell script.

Here is an example.
```
#!/bin/sh


$1 "$2"
echo "Running $1 with argument $2"
exit 0
```
So giving this executable the argument 'gimp' would make Ubuntu launch gimp.

Thanks.  Sorry for the delay in acknowledging your response.  Busy.  I have not done scripting in Linux before, this will give me something to tinker with.

---

