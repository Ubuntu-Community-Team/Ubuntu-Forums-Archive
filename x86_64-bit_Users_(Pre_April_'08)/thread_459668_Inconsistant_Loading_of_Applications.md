---
title: "Inconsistant Loading of Applications"
date: 2007-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by diddler on 2007-05-30
I am having some strange dealings with installed applications.  Some don't load the first time I click on them, but will load on the 2d or 3rd try.  Other applications that used to load just fine (Alexandria Book Collection Manager, for example) now won't load at all.  Anyone have any idea what is going on?  It seems foolish to spend a lot of time using an application and typing in data if the app is going to suddenly stop working without reason.

---

### Post by Cappy on 2007-05-31
Try opening the program in a console.
The console is located at the top left hand of the screen in (Applications-->Accessories-->Terminal).
Type ```
alexandria
``` and hit enter. Hopefully, if that is the correct command, it should give you an error or some idea what the problem is. If you don't know how to fix the problem just copy and paste the error it back to this thread.

---

### Post by diddler on 2007-06-01
Here is the dump from the terminal.  There must be a conflict with a later installed program, but I could not tell you exactly at what point it started crashing.

borf@borf-desktop:~$ alexandria
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
-----------------------
Alexandria just crashed
-----------------------
Timestamp: Fri Jun 01 22:25:40 -0500 2007
Message: Not a book
Backtrace:
/usr/lib/ruby/1.8/alexandria/library.rb:66:in `load'
/usr/lib/ruby/1.8/alexandria/library.rb:53:in `each'
/usr/lib/ruby/1.8/alexandria/library.rb:53:in `load'
/usr/lib/ruby/1.8/alexandria/library.rb:52:in `chdir'
/usr/lib/ruby/1.8/alexandria/library.rb:52:in `load'
/usr/lib/ruby/1.8/alexandria/library.rb:92:in `loadall'
/usr/lib/ruby/1.8/alexandria/library.rb:86:in `each'
/usr/lib/ruby/1.8/alexandria/library.rb:86:in `loadall'
/usr/lib/ruby/1.8/alexandria/ui/main_app.rb:266:in `load_libraries'
/usr/lib/ruby/1.8/alexandria/ui/main_app.rb:84:in `initialize'
/usr/lib/ruby/1.8/alexandria/ui.rb:41:in `new'
/usr/lib/ruby/1.8/alexandria/ui.rb:41:in `main'
/usr/lib/ruby/1.8/alexandria.rb:66:in `main'
/usr/bin/alexandria:10
Release: 0.6.1

Uname -a: Linux borf-desktop 2.6.20-16-generic #2 SMP Wed May 23 00:30:47 UTC 2007 x86_64 GNU/Linux
--
Please report this dump to 'alexandria-list@rubyforge.org' with some additional
information, such as the description of the crash and the steps to reproduce it
(if it's possible).
borf@borf-desktop:~$

---

### Post by John Jason Jordan on 2007-06-02
> **diddler said:**
> Here is the dump from the terminal.  There must be a conflict with a later installed program, but I could not tell you exactly at what point it started crashing.
I don't know enough about Linux or programming to know what is going wrong. But I can add that I have had Alexandria installed for a long time and it works fine for me -- currently on Feisty amd64. Have you tried doing a reinstall?

I have not seriously used Alexandria so far. I love the lookup feature where you can just pop in the ISBN and it will look up the rest of the data. Saves a lot of typing. But I don't like the fact that it appears to use its own database format. I have so many books that it would take me days to enter them all. What if I go to all that work and later I can't access the data because of changes to the OS that make Alexandria no longer work. I'd rather use something that stores the data in a standard database format that anything can access. It would be especially cool if I could export the data and put it on a PDA. 

Another thing is that I've never felt it was completely stable. For example, click on the About button, then try to close the window that pops up with the Close button. It won't work. You have to close the popup window with the X in the corner. There are a lot of similar little programming goofs that worry me.

And finally, I wish it would hold all the books in the same database (table) and let me make my own queries to pull out specific categories. As it is, I have to make a different table for each category if I want to look for a book by category.

---

### Post by Cappy on 2007-06-02
[http://rubyforge.org/tracker/index.php?func=detail&aid=8451&group_id=205&atid=864](http://rubyforge.org/tracker/index.php?func=detail&aid=8451&group_id=205&atid=864)

> 
Date: 2007-02-16 04:14
Sender: Marco Costantini

My guess is that something wrong has been stored in the files
that contain the information about the last entered book.
Try to find those file, they should be something like 
~/.alexandria/MyLibrary/8817841919.yaml
and possibly its cover
~/.alexandria/MyLibrary/8817841919.cover
and to delete/moving to another directory them.

Furthermore, please report the isbn number, which provider has
been likely been used, your alexandria version, and wether the
problem persist after deleting/moving the file above.


(Hopefully?) that may be the problem

---

### Post by diddler on 2007-06-02
> **John Jason Jordan said:**
> I don't know enough about Linux or programming to know what is going wrong. But I can add that I have had Alexandria installed for a long time and it works fine for me -- currently on Feisty amd64. Have you tried doing a reinstall?.

Yes.  I deleted the previous install and re-installed.  Same problem.

I agree with most of what you say.  I love so many of the Linux apps, but almost all have a bug that crops up at the most inconvenient times.  I have had programs crash when I hit the "help" button, or when I try to open up some of the drop down lists on "save" windows (GIMP is especially prone to this).  Unfortunately, I am not Linux fluent enough to diagnose these problems. 

I don't think I will ever trust a Linux app with an internal database enough to put a lot of time or effort into using it.  I found an app that looked like a video version of Alexandria but it only supported French (which I speak) and failed to recognize ANY video titles I typed in.

I think I will build my own databases with OpenOffice, then use the Linux apps to get any information I need.  Cut and paste, cut and paste.

---

### Post by diddler on 2007-06-02
I am even having problems with this forum.  I did a quote and reply, now that message shows up every time I try to reply to different message!

To Cappy:  Thanks for the advice.  I will give it a try.

---

### Post by diddler on 2007-06-02
> **Cappy said:**
> [http://rubyforge.org/tracker/index.php?func=detail&aid=8451&group_id=205&atid=864](http://rubyforge.org/tracker/index.php?func=detail&aid=8451&group_id=205&atid=864)



(Hopefully?) that may be the problem

It appears that it was.  For some reason when I did that, it also closed Firefox, but nothing lost but time.

---

