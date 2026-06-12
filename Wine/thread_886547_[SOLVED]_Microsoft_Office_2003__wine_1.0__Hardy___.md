---
title: "[SOLVED] Microsoft Office 2003 / wine 1.0 / Hardy    After install Excell freezes"
date: 2008-08-11
forum: Wine
---

### Post by abcuser on 2008-08-11
Hi,
I clean installed wine 1.0 and Microsoft Office 2003 inside Ubuntu 8.04-Hardy according to blog [Only Ubuntu Linux](http://onlyubuntu.blogspot.com/2008/07/how-to-install-ms-office-2003-in-ubuntu.html) post.

After installation MS-Word starts without any problems and works fine, but Excel freezes at startup and no error is displayed. Any idea how to solve the problem?

Thanks,
Abcuser

---

### Post by abcuser on 2008-08-11
Hi,
I have found out a solution acording to blog (see link in my first post) comments Excel freezes first time when it is started.

So from Terminal I did the following:
1. Get process ID of Excel
ps aux | grep -i Excel

2. Kill the process:
kill -9 process_id_from_step_1

3. Started Excel. It reported that Excel didn't properly start and if I want to go into Excel Safe Mode. I pressed yes to go in safe-mode.

4. Excel started successfully. From selected File | Exit to exit safe-mode.

5. Started Excel and it started succesfully.

Thanks, problem solved.

Regards,
Abcuser

---

### Post by Unicast on 2008-08-24
Great thanks - worked a treat! :cool:

---

