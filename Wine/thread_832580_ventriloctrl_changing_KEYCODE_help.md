---
title: "ventriloctrl changing KEYCODE help"
date: 2008-06-17
forum: Wine
---

### Post by BoysBoysBoys on 2008-06-17
Im trying to edit the ventriloctrl.c file to change the input key to something other than "a" because I use "a" to turn left in wow. So I removed the # in front of "define KEYCODE XK_Alt_L" but i get an error when i compile.

```
gcc -Wall -O3 -o ventriloctrl ventriloctrl.c -lX11
ventriloctrl.c:27: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘KEYCODE’
ventriloctrl.c: In function ‘main’:
ventriloctrl.c:146: warning: implicit declaration of function ‘createKeyEvent’
ventriloctrl.c:146: error: ‘KEYCODE’ undeclared (first use in this function)
ventriloctrl.c:146: error: (Each undeclared identifier is reported only once
ventriloctrl.c:146: error: for each function it appears in.)
ventriloctrl.c:146: error: incompatible types in assignment
ventriloctrl.c:151: error: incompatible types in assignment
make: *** [all] Error 1

```

```
// 
// Original code by Adam Pierce - http://www.doctort.org/adam/
// http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html
//

//
// find_window() -function contributed by Markus Lindqvist
//

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <X11/Xlib.h>
#include <X11/keysym.h>

// evdev input
#include <linux/input.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>

#define VERSION "v0.3-SVN"
#define VENTWIN "Ventrilo"

// define key to send to Ventrilo, default is A
define KEYCODE XK_Alt_L

XKeyEvent createKeyEvent(Display *display, Window win,
			Window winRoot, int press,
			int keycode, int modifiers)
{
	XKeyEvent event;

	event.display     = display;
	event.window      = win;
	event.root        = winRoot;
	event.subwindow   = None;
	event.time        = CurrentTime;
	event.x           = 1;
	event.y           = 1;
	event.x_root      = 1;
	event.y_root      = 1;
	event.same_screen = True;
	event.keycode     = XKeysymToKeycode(display, keycode);
	event.state       = modifiers;
	event.send_event  = 1;
	event.serial      = 0;
	if(press)
		event.type = KeyPress;
	else
		event.type = KeyRelease;

	return event;
}

Window *find_window(Display *display, Window start, const char *name)
{
	Window *children = 0;
	Window root;
	Window parent;
	int i;
	unsigned int childrenCount = 0;
	XQueryTree(display, start, &root, &parent, &children, &childrenCount);
	    
	char *window_name = 0;
	for(i=0; i<childrenCount; ++i) {
		if(XFetchName(display, children[i], &window_name) == 1) {
			//printf("value: %s\n", window_name);
			if(strcmp(name, window_name) == 0) {
				XFree(window_name);
				return &children[i];
			}
			XFree(window_name);
		}
	}

	for(i=0; i<childrenCount; ++i) {
		Window *window = find_window(display, children[i], name);
		if(window != 0) {
			XFree(children);
			return window;
		}
	}

	if(children != 0)
		XFree(children);

	return 0;
}

int main(int argc, char **argv)
{
	// xlib
	Display *display;
	Window winRoot;
	Window *winFocus = 0;
	XKeyEvent event;

	// check parameters
	if (argc < 3) {
		printf("usage: %s <device> <listen key>\n", argv[0]);
		return 1;
	}

	printf("Ventrilo Control %s for Linux by Purkka Productions\n", VERSION);
	printf("=====================================================\n");
	printf("WARNING: This program reads DIRECTLY your keyboard!\n");
	printf("         You need correct permissions to read the\n");
	printf("         event device.\n");

	// evdev
	int fd;
	fd = open(argv[1], O_RDONLY);
	if(!fd) {
		printf("Error: Can't opening device %s\n", argv[1]);
		return 1;
	}
	struct input_event ev;

	display = XOpenDisplay(0);
	if(display == NULL) {
		printf("Error: Could not open display!\n");
		return 1;
	}

	winRoot = XDefaultRootWindow(display);
	winFocus = find_window(display, winRoot, VENTWIN);

	if(!winFocus) {
		printf("Could not find Ventrilo window. Is Ventrilo running?\n");
		return 1;
	}

	printf ("Window selected. Please test pressing the key to talk before going to play.\n");
	printf ("\nUse CTRL-C to quit.\n");

	// main loop after selecting window
	while(1)
	{
		read(fd, &ev, sizeof(struct input_event));
		if(ev.type == 1) {
			if(ev.code == atoi(argv[2])) {
				if(ev.value == 1) {
					// send press event
					event = createKeyEvent(display, *winFocus, winRoot, 1, KEYCODE, 0);
					XSendEvent(event.display, event.window, True, KeyPressMask, (XEvent *)&event);
					XFlush(display);
				} else if(!ev.value) {
					// send release event
					event = createKeyEvent(display, *winFocus, winRoot, 0, KEYCODE, 0);
					XSendEvent(event.display, event.window, True, KeyPressMask, (XEvent *)&event);
					XFlush(display);
				}
			}
		}
	}

	return 0;
}
```

---

### Post by Statix0 on 2008-06-26
Your define line needs a # in front of it. Doesn't it work that way?

---

