---
title: "xview-examples crash on 9.04"
date: 2009-05-01
forum: x86 64-bit Users
---

### Post by djconnel on 2009-05-01
I'm trying to isolate a problem with some archaic code I need to run, which uses xview, so I tried installing the xview-examples under 9.04, and none of them run.
```
% uname -a
Linux djconnel-t60 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
% cd /usr/lib/xview/examples/
% ls
animate        color_logo     done_proc       hot_spot	     logo	    notify_input   repaint	  seln		 slider       textsw	       xv_menu
bitmap	       color_objs     example1	      icon_demo      long_seln	    ntfy_do_dis    sample_tty	  seln_line	 source1      textsw.font      xv_termsw
btn_menu       color_panel    example2	      icon_demo2     menu	    ntfy_pipe	   screen	  simple_cursor  source2      textsw_to_ttysw
canvas_event   command_frame  example3	      image	     menu_dir	    ntfy_sig	   scroll_cells   simple_font	 split_views  trigger_notice
canvas_input   default_size   example4	      interpose      menu_dir2	    panel_repaint  scroll_cells2  simple_frame	 stop_cursor  ttycurses
choices        default_text   fonts	      item_move      multi_display  pin_menu	   scroll_view	  simple_menu	 stop_frame   type_font
client_data    dest	      frame_color     line	     multiscreen    popup	   scrollto	  simple_notice  subframe     vkbd_colors
color	       disp_fonts     fullscreen      list_6_glyphs  notice	    pw_draw	   sel_hold	  simple_panel	 svrimage     vkbd_fonts
color_animate  disp_fonts2    hdrs_n_footers  list_glyphs    notify	    quit	   sel_req	  simple_seln	 text_seln    x_draw
% ./example1 
System warning: No such file or directory, call to alloc function returned NULL pointer
Segmentation fault
```

In addition, I tried compiling and running "quit.c" from the XView programming manual, and that doesn't run, aborting on line 15:
```
% gcc -lxview -g quit.c -o quit
quit.c: In function 'main':
quit.c:20: warning: passing argument 1 of 'xv_create' makes integer from pointer without a cast
% ./quit 
System warning: No such file or directory, call to alloc function returned NULL pointer
Segmentation fault
   
% cat -n quit.c 
     1	/*
     2	 * quit.c -- simple program to display a panel button that says "Quit".
     3	 * Selecting the panel button exits the program.
     4	 */
     5	#include <xview/xview.h>
     6	#include <xview/frame.h>
     7	#include <xview/panel.h>
     8	Frame frame;
     9	main (argc, argv)
    10	int argc;
    11	char *argv[ ];
    12	{
    13	    Panel panel;
    14	    void quit();
    15	    xv_init (XV_INIT_ARGC_PTR_ARGV, &argc, argv, NULL);
    16	    frame = (Frame)xv_create (NULL, FRAME,
    17	        FRAME_LABEL,     argv[0],
    18	        XV_WIDTH,        200,
    19	        XV_HEIGHT,       100,
    20	        NULL);
    21	    panel = (Panel)xv_create (frame, PANEL, NULL);
    22	    (void) xv_create (panel, PANEL_BUTTON,
    23	             PANEL_LABEL_STRING,        "Quit",
    24	             PANEL_NOTIFY_PROC,         quit,
    25	             NULL);
    26	    xv_main_loop (frame);
    27	    exit(0);
    28	}
    29	void
    30	quit()
    31	{
    32	    xv_destroy_safe(frame);
    33	}
```

Has anyone had any luck running xview on 9.04?   The original ap (DeckBuild by Silvaco) ran fine (well, sort of...) on 8.10.  Under 9.04, as soon as I request a pull-down menu, I lose focus and need to remotely kill the job.

It seems to me (from what I can tell from the obfuscated .h files) that xview places fast and loose with conversions between long integer and pointer.  But it is mature code...



thanks!

---

### Post by fhage on 2009-06-11
You must be running the apps with 32bit libs. Use 'ldd apname' to verify this.
I'm also running into this problem, but the strange thing is the apps were working on June 9th. On June 10 my legacy Xview app now hangs the window manager and I did no updates or changes to the application. 

I tried on a 32bit system and have found the same problem with all Xview
example programs. I tested on two 9.04 systems; one 32bit 2.6.28-11-generic i686 and my 64 bit system ( 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux) The two systems use different X-servers. I tried XFCE4 and had the same symptoms. 

I get correct behavior when I remote display the applications to an Ubuntu
8.04 box.  One can expose this problem this using  the xview example program ; 'cmdtool'. On 9.04, as soon as one clicks in the window, the window manager hangs and cmdtool needs to be killed (use a virtual console to login and 'killall cmdtool'). One can still enter text from the keyboard, but one click and its over.

-Frank.

---

### Post by khofmann on 2009-07-14
Is there any news on this issue? We are experiencing the same problem and I have done some experiments to narrow it down.

- We are using two xview applications (gde, treetool) on several linux boxes, some of them with ubuntu 8.04 (hardy), some with 9.04 (jaunty), all of them running the 64bit versions. On all hardy installations, the xview-based binaries work fine, while on all jaunty installations they don't. The problems are the same as reported: the whole window manager freezes and we have to kill the offending application.

- As reported above, remotely calling an x-view application on jaunty from a hardy-box works fine.

- Conversely, calling a hardy-based xview application from a jaunty box gives the same problems as usin the jaunty program locally.

Without being an expert in these matters, I would think that the problem is not directly within the executables but rather in the X-server (or in its response to xview-based calls). As fhage said above, the problem is also observed on an XFCE4 system and thus does not rely on the windows manager (we use KDE on all machines). 
Most likely, there is some difference in the X.org system between hardy and jaunty that causes this problem. 

If I find a solution or a work-around, I will post here.

-Kay

---

### Post by professor_chaos on 2009-07-29
I have the same problem. I see mention of the problem here.
[http://www.physionet.org/physiotools/xview/](http://www.physionet.org/physiotools/xview/)

---

### Post by professor_chaos on 2009-07-29
Oh, and it may be worth noting that my user account and another has this problem, but another third user account doesn't. I haven't had time to check to reasons why, however it may be worth noting that the user account that doesn't exhibit this problem is not a admin account and is only apart of a few groups. This may be a red-herring, but worth further examination.
Cheers
Dan

---

### Post by khofmann on 2009-08-04
Still no clue of a solution or work-around. The bug has also been mentioned and discussed here: [http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg112014.html](http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg112014.html)

I find it hard to imagine that the but should be user-dependent. I created a dummy user without any privileges, but the problem persists.  

One of my colleagues who is suffering from this bug reports that it happens only intermittently - sometimes the xview application seems to work fine, at other occasions it freezes for about a minute, and sometimes the freeze seems to be permanent. For me (on another computer running 64bit jaunty) the problem happens every single time when clicking with the mouse within an xview-generated window.

---

