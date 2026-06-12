---
title: "Problem redirecting output stream of Wine"
date: 2008-03-28
forum: Wine
---

### Post by ranamar on 2008-03-28
Hi all,
I'm using an Ubuntu 7.10 and the latest (?) version of Wine ( 0.9.58 ).
I'm running a windows application that seems to work properly, but i cannot manage to redirect the output to a file:

$ wine cmd.exe
Usage : cmd.exe [filename1] [filename2] ...

$ wine cmd.exe > /dev/null
Usage : cmd.exe [filename1] [filename2] ...

$ wine cmd.exe 2> /dev/null
Usage : cmd.exe [filename1] [filename2] ...

I've already tried to use wineconsole, but I get the same behavior and using wineconsole --backend=curses I get the following error:
                                                                                                            fixme:curses:WCCURSES_GetEvents Ooch. somebody beat us

Any idea?

Thanks in advance.

---

