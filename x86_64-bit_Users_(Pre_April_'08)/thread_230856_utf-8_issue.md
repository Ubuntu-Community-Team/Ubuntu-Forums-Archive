---
title: "utf-8 issue"
date: 2006-08-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by denni on 2006-08-06
utf-8 is the common encoding, and some program does'nt print out foragne characters correctly.  phpBB2 does not show foeign languages correctly do to this in dapper.  Is there any encoding program that you can run on a dir that would encode all in the directory from iso8859-1 to utf-8 wiht one command or a script.

---

### Post by denni on 2006-08-07
did find this > iconv -f iso8859-1 -t utf-8 /path/to/iso8859-1.file > /path/to_new/utf-8 file
solution but encoding the whole /usr/share/phpbb2/site/language/lang_icelandic/* is to much of a task because it is only possible to do it wiht one file at a time. Is there anyone with a skripting knowledge that can make a small skript out of this command to perform the task on a whole directory?

---

### Post by juicemansam on 2006-08-07
I'd try the following the directory that contains the files you need to change: ```
find -type f -name \*\.php -exec iconv -f iso8859-1 -t utf8 -o {}.utf8 {} \;
```
Just in case you don't know the *find* command. The first switch *-type f* specifies that you're looking for files, otherwise it would find directories as well. The second switch *-name \*.php* specifies that you want those files' names to end in .php, but you can change that to whatever you need it to be. The third, and longest switch, *-exec ... \;*, instructs *find* to run iconv, with it's own parameters, not *find*'s, on every file, notated as *{}*. Just so you can tell the resulting files appart, you can add an extension to their name, such as .utf8. The *-exec* switch must be terminated by a semicolon, either escaped or quoted, such as \; or ';' or ";". Also note that you must escape characters such as * and ., that's due to their special meanings within the shell. After running the above command you could then run a *for* loop mixed with another *find* command. For example:```
for i in `find -name \*\.utf8`
do
  mv $i -v `basename $i .uf8`
done
```
Here, the *for* conditional command assigns every file ending with .utf8 to the variable *i*, for which it will run commands with in *do* and *done*. Basename is a program that takes a file name and prints it, but if you add an extension, it removes the extension from name print-out. This *for* command basically renames all of the converted files to their original names, overwriting the original iso8859-1 versions. The "back-tick" (`) basically creates a sub-shell that will run what's inside and return the standard output, such as list of files, or a name witout a temporary extension.

A script could be easily created from the information I've provided, but it wouldn't be a cookie-cut script that you could use without tweaking it before using it. I recommend reading the following man/info/help pages: iconv, find, and for (this one would be *help for* in a bash shell). Also, I strongly recommend trying this on a copy of the directory in question until you're confident that you'll get the results you want. Also note that *find* only finds what it's told to look for within the current work directory by default, unless specified as the first parameter, such as *find /tmp -type s*, in which *find* would look for socket files inside the directory /tmp.

---

### Post by denni on 2006-08-07
And a another question related to this.  Is there a shell command to change one line in all the documents in a directory that match sudden string, like the string Charset: iso-8859-1 to Charset: utf-8

like grep something | to something else

it seems that utf-is is the default in newer linux distros and that some software developers groups are still few steps behind

---

### Post by juicemansam on 2006-08-08
I think the tool you're looking for here is *sed*. It's late for me, so I'll post more later. In the meantime have a look at it's man/info page. *Sed* is a powerful tool because of it's ability to use regular expressions (a whole other topic), which come in very handy in searching for text patterns.

---

### Post by denni on 2006-08-08
What you posted did work for changing from iso-8859-1 to utf-8 in just one click and then stripping all the files of their .utf8 ending by hand and open them all up for changing  Charset: iso-8859-1 to Charset: utf-8.  Now the phpbb2 is running with the Icelandic translation correctly.   

Did as you told and did run it all on a copy ( cp -a ... ... )

basename is very simple and lacking features but sed is loaded with features for those that have the underlying knowledge to use it.  But a am "almost" unable to discuss the linux commands and the bash scripting language do to lack of knowledge.  I have just the basic knowledge of the basic commands and have just taken a little look into the window of programming and scripting.

The scripting and linux commands are surely an interesting subject.

---

