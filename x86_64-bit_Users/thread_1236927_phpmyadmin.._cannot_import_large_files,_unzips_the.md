---
title: "phpmyadmin.. cannot import large files, unzips them.."
date: 2009-08-10
forum: x86 64-bit Users
---

### Post by edwardtilbury on 2009-08-10
Here's what confusing me... I can upload this zipped SQL file on a windows wamp box, but not on my ubuntu 9.04 desktop...

Unzipped the file is 17.8 MB (18632561 bytes)
Zipped the file is 1.7 MB (1802206 bytes)[INDENT]Windows 2003 /w WAMP installed
PHPmyadmin settings:
(Max: 2,048 KiB) 
Imported file compression will be automatically detected from: None, gzip, bzip2, zip
[/INDENT][INDENT]Ubuntu , Apache/PHP/Mysql installed
PHPmyadmin settings:
(Max: 32,768  KiB) 
Imported file compression will be automatically detected from: None, gzip, bzip2, zip
[/INDENT]The error.
**Fatal error**:  Allowed memory size of 33554432 bytes exhausted (tried to allocate 18599794 bytes) in **/usr/share/phpmyadmin/libraries/import.lib.php** on line **269**


I upped the sizes of allowable imports in
/etc/mysql/my.cnf

and 

/etc/php5/apache2/php.ini


**Fatal error**:  Allowed memory size of 33554432 bytes exhausted (tried to allocate 18599794 bytes) in **/usr/share/phpmyadmin/libraries/import.lib.php** on line **269**

Here's line 269 btw..
            $GLOBALS['import_text'] = substr($GLOBALS['import_text'], $size);

[I]am I missing something? I tried to execute the upload in mysql gui query but it just times out...  :(
[/I]

---

### Post by edwardtilbury on 2009-08-10
I got it working by unzipping the file.. but it kinda gets under my skin that I can do this on my windows installation and not on Ubuntu..  if you know the workaround please let me know, I probably just didn't configure something..

---

### Post by ethoxyethaan on 2009-08-10
/etc/php5/apache2/php.ini
```

max_execution_time = 30     ; Maximum execution time of each script, in seconds
max_input_time = 60 ; Maximum amount of time each script may spend parsing request data
;max_input_nesting_level = 64 ; Maximum input variable nesting level
memory_limit = 16M      ; Maximum amount of memory a script may consume (16MB)



```

change these settings.

---

