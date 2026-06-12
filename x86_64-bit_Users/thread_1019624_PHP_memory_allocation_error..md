---
title: "PHP memory allocation error."
date: 2008-12-23
forum: x86 64-bit Users
---

### Post by obsrv on 2008-12-23
PHP Error:

```
Fatal error: Allowed memory size of 20971520 bytes exhausted (tried to allocate 7680 bytes) in /usr/share/mediawiki/includes/SearchMySQL.php on line 158
```

Any ideas? I get this when trying to submit a page to mediawiki system. Using Ubuntu 9.04 A2

EDIT:

When editing pages I get this:


Fatal error: Allowed memory size of 20971520 bytes exhausted (tried to allocate 7680 bytes) in /usr/share/mediawiki/includes/SiteStats.php on line 171

---

### Post by obsrv on 2008-12-23
What I think is that I need somehow to flush the PHP cache. Am I right?

---

### Post by tomdkat on 2008-12-23
Why not use "top" to see how much memory is being used by the web server?

Peace...

---

### Post by obsrv on 2008-12-23
Thanks for reply, apache2 has 7 processes and each has allocated 23mb of RAM.

---

### Post by tomdkat on 2008-12-24
How much RAM is installed in the machine?  How much free RAM do you have after Apache first starts?

Peace...

---

### Post by obsrv on 2008-12-25
I have got 8GB DDR2 800 RAM. Allocated is normaly 5%, sometimes at most (when virtual box has 5 OS running) 50%

---

### Post by obsrv on 2008-12-26
24hour passed, so BUMP!

---

### Post by ju2wheels on 2008-12-27
This sounds like one of the configuration properties in php.ini needs to be made larger.

I would check what your resource limit parameters are set to (example from default php.ini):
```

;;;;;;;;;;;;;;;;;;;
; Resource Limits ;
;;;;;;;;;;;;;;;;;;;

max_execution_time = 30     ; Maximum execution time of each script, in seconds
max_input_time = 60	; Maximum amount of time each script may spend parsing request data
memory_limit = 8M      ; Maximum amount of memory a script may consume (8MB)

```

Also check the values for post/upload max limits:
```

; Maximum size of POST data that PHP will accept.
post_max_size = 8M

; Maximum allowed size for uploaded files.
upload_max_filesize = 2M

```

Edit: It looks like one of the above values was set to 20MB and an upload failed when it tried to allocate another 7kb chunk over that 20MB.

---

### Post by obsrv on 2008-12-27
Mine is:

> ;;;;;;;;;;;;;;;;;;;
; Resource Limits ;
;;;;;;;;;;;;;;;;;;;

max_execution_time = 60     ; Maximum execution time of each script, in seconds
max_input_time = 120 ; Maximum amount of time each script may spend parsing request data
;max_input_nesting_level = 64 ; Maximum input variable nesting level
memory_limit = 1024M      ; Maximum amount of memory a script may consume (16MB)

; Maximum size of POST data that PHP will accept.
post_max_size = 128M

; Maximum allowed size for uploaded files.
upload_max_filesize = 128M


I set it to huge values since I was searching for solution. Still didn't help :(

---

### Post by trebach on 2009-01-03
You must also change the memory settings in LocalSettings.php in MediaWiki.
```
ini_set( 'memory_limit', '32M' );
```

---

### Post by Swerve1000 on 2009-01-03
That should work, I have had the same issue before with web hosts.

---

### Post by seb_renaud on 2009-09-20
I seem to be able to produce this error just by entering 'é' and submitting a page. Anyone here knows why before I dive into the PHP code myself?

---

### Post by ju2wheels on 2009-09-20
Really? I would expect something more along the lines of a charset error in that case, but Im no mediawiki expert. Is the error being thrown by php or your database?

---

### Post by seb_renaud on 2009-09-20
I believe that it is php, I get this line:

Fatal error: Allowed memory size of 20971520 bytes exhausted (tried to allocate 7680 bytes) in /var/www/w/includes/SiteStats.php on line 171

Said dine 171:

function appendUpdate( &$sql, $field, $delta ) {
...

My server is nowhere close to running out of memory ( says top ).

When I reload the page with the above error, I get this one:

Fatal error: Allowed memory size of 20971520 bytes exhausted (tried to allocate 30720 bytes) in /var/www/w/includes/SearchMySQL.php on line 60

Seems rather strange. I am not very familiar with PHP, what should I do next? Should I hack the PHP code to see what gets passed to appendUpdate()?

---

