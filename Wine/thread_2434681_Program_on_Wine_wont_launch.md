---
title: "Program on Wine wont launch"
date: 2020-01-09
forum: Wine
---

### Post by Bhakti108 on 2020-01-09
I have a few programs running through wine but one will not run. Everything in the download appears normal. How or what do I access to see what is not happening in tghe program launch sequence. No error messages come up, the little wheel just spins and then goes out. 

Any help please?

---

### Post by slickymaster on 2020-01-09
*Thread moved to **Wine**.*

---

### Post by ajgreeny on 2020-01-09
The best way to get information about this as we do not know what app you're asking about, is to go to the wine app database at [https://appdb.winehq.org/](https://appdb.winehq.org/) and do a search. Forget about anything rated below **Silver** in their grading, and even some **Silver** will run only poorly.

Don't forget that there is no chance with some Windows applications to get them to run through Wine; some will, some won't, and some will do better with (proprietary but free to use, I believe), playonlinux which is in the repos.

---

### Post by mastablasta on 2020-01-10
you can troubleshoot by running the program from terminal / console. you run it by

```
wine *programname*.exe
```

any error codes will be displayed in the terminal. you can then copy them & paste to forums etc. for troubleshooting.

---

