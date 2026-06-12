---
title: "Upgrade from Gutsy to Jaunty, now having strange display issues"
date: 2009-06-23
forum: x86 64-bit Users
---

### Post by ktgbp on 2009-06-23
I upgraded an Ultra 20 from Gutsy to Jaunty, testing each incremental upgrade on the way.  The box is mostly used remotely, with the display exported to a Sparc solaris box running Solaris 10.  I mainly run thunderbird, firefox, and gvim sessions remotely.  

Following the final upgrade to Jaunty, i can no longer start sessions of these programs.  I can start basic X programs (xclock, xterm), but all the above fail, along with other programs I occasionally use (synaptic). 

All programs fail with the identical following error: (just replace thunderbird with the app name)

Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
The program 'thunderbird-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 47 error_code 2 request_code 151 minor_code 4)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I'm logging in via ssh -X

I re-installed firefox, thunderbird, and gvim.  I removed all existing configuration as well, and the error persists.  
straces on the programs did not seem to give me any useable information.

I've spent all morning searching and can't find anything that would show this is a known issue.  

Any ideas.

-Kyle

---

