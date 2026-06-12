---
title: "Problem with compiling wine with a new patch..."
date: 2008-10-13
forum: Wine
---

### Post by Juggercat on 2008-10-13
Hello, im trying to compile wine with a new patch... im a newb... so i got stuck on the first step... :S
when i try to install the  dependencies for wine i get the following error..

E: Build-dependencies for wine could not be satisfied.


can anyone help me? :(

thx in advance

---

### Post by david_kt on 2008-10-13
> **Juggercat said:**
> Hello, im trying to compile wine with a new patch... im a newb... so i got stuck on the first step... :S
when i try to install the  dependencies for wine i get the following error..

E: Build-dependencies for wine could not be satisfied.


can anyone help me? :(

thx in advance

Run:
```
sudo apt-get build-dep wine
```

Make sure it completed without error, and then try to compile again.

DK

---

### Post by Juggercat on 2008-10-13
the problem would be... is i get that error when i run that specific code...

---

### Post by david_kt on 2008-10-13
> **Juggercat said:**
> the problem would be... is i get that error when i run that specific code...

Post the error for me to see.

DK

---

### Post by werries on 2008-10-13
I had the same problem when i had the hardy-proposed repositories in use. Something about a new library version that everything needed, but wine wanted the older one, lol.
Had to disable the repository and then force a downgrade of the package. went fairly well after that.

---

### Post by Juggercat on 2008-10-13
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for wine could not be satisfied.

could u tell me exactly how to do that werries? like a mini how to? im new to ubuntu... thanks again everyone!

---

### Post by david_kt on 2008-10-13
> **Juggercat said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for wine could not be satisfied.

could u tell me exactly how to do that werries? like a mini how to? im new to ubuntu... thanks again everyone!

I assume you are using ubuntu hardy. Please download below script:

[http://www.kegel.com/wine/hardy.sh](http://www.kegel.com/wine/hardy.sh)

After that. open terminal and go to the directory you downloaded above file. Let's say you download it on your desktop.

Open terminal:
```
Applications > Accessories > Terminal
```
Execute below commands, one at a time:
```

cd Desktop
chmod +x hardy.sh
sudo ./hardy.sh
```

If the above commands successful, try compiling wine again.

DK

---

### Post by Juggercat on 2008-10-14
ok... now i get the following error when i execute the last line of code...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
libltdl3 is already the newest version.
libmad0 is already the newest version.
libmad0 set to manually installed.
libqt3-mt is already the newest version.
libqt3-mt set to manually installed.
libvorbisfile3 is already the newest version.
make is already the newest version.
odbcinst1debian1 is already the newest version.
odbcinst1debian1 set to manually installed.
unixodbc is already the newest version.
unixodbc set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.7-10ubuntu3) but 2.7-10ubuntu4 is to be installed
  libdbus-1-dev: Depends: libdbus-1-3 (= 1.1.20-1ubuntu1) but 1.1.20-1ubuntu2 is to be installed
  libfreetype6-dev: Depends: libfreetype6 (= 2.3.5-1ubuntu4) but 2.3.5-1ubuntu4.8.04.1 is to be installed
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.16.3-1) but 2.16.4-0ubuntu3 is to be installed
  libgnutls-dev: Depends: libgnutls13 (= 2.0.4-1ubuntu2) but 2.0.4-1ubuntu2.1 is to be installed
  libgphoto2-2-dev: Depends: libgphoto2-2 (= 2.4.0-8ubuntu6) but 2.4.0-8ubuntu7 is to be installed
  libhal-dev: Depends: libhal1 (= 0.5.11~rc2-1ubuntu7) but 0.5.11~rc2-1ubuntu8.2 is to be installed
  libldap2-dev: Depends: libldap-2.4-2 (= 2.4.7-6ubuntu3) but 2.4.9-0ubuntu0.8.04.1 is to be installed
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8g-4ubuntu3) but 0.9.8g-4ubuntu3.3 is to be installed
  libtiff4-dev: Depends: libtiff4 (= 3.8.2-7ubuntu3) but 3.8.2-7ubuntu3.1 is to be installed
  libxml2-dev: Depends: libxml2 (= 2.6.31.dfsg-2ubuntu1) but 2.6.31.dfsg-2ubuntu1.2 is to be installed
  libxslt1-dev: Depends: libxslt1.1 (= 1.1.22-1ubuntu1) but 1.1.22-1ubuntu1.2 is to be installed
E: Broken packages

thx again for all ur help and time...

---

### Post by david_kt on 2008-10-14
> **Juggercat said:**
> ok... now i get the following error when i execute the last line of code...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
libltdl3 is already the newest version.
libmad0 is already the newest version.
libmad0 set to manually installed.
libqt3-mt is already the newest version.
libqt3-mt set to manually installed.
libvorbisfile3 is already the newest version.
make is already the newest version.
odbcinst1debian1 is already the newest version.
odbcinst1debian1 set to manually installed.
unixodbc is already the newest version.
unixodbc set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.7-10ubuntu3) but 2.7-10ubuntu4 is to be installed
  libdbus-1-dev: Depends: libdbus-1-3 (= 1.1.20-1ubuntu1) but 1.1.20-1ubuntu2 is to be installed
  libfreetype6-dev: Depends: libfreetype6 (= 2.3.5-1ubuntu4) but 2.3.5-1ubuntu4.8.04.1 is to be installed
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.16.3-1) but 2.16.4-0ubuntu3 is to be installed
  libgnutls-dev: Depends: libgnutls13 (= 2.0.4-1ubuntu2) but 2.0.4-1ubuntu2.1 is to be installed
  libgphoto2-2-dev: Depends: libgphoto2-2 (= 2.4.0-8ubuntu6) but 2.4.0-8ubuntu7 is to be installed
  libhal-dev: Depends: libhal1 (= 0.5.11~rc2-1ubuntu7) but 0.5.11~rc2-1ubuntu8.2 is to be installed
  libldap2-dev: Depends: libldap-2.4-2 (= 2.4.7-6ubuntu3) but 2.4.9-0ubuntu0.8.04.1 is to be installed
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8g-4ubuntu3) but 0.9.8g-4ubuntu3.3 is to be installed
  libtiff4-dev: Depends: libtiff4 (= 3.8.2-7ubuntu3) but 3.8.2-7ubuntu3.1 is to be installed
  libxml2-dev: Depends: libxml2 (= 2.6.31.dfsg-2ubuntu1) but 2.6.31.dfsg-2ubuntu1.2 is to be installed
  libxslt1-dev: Depends: libxslt1.1 (= 1.1.22-1ubuntu1) but 1.1.22-1ubuntu1.2 is to be installed
E: Broken packages

thx again for all ur help and time...

First of all disable hardy-proposed repositories, check your synaptic to disable it. Or, do:

```
gksudo gedit /etc/apt/sources.list
```

and put # in front of any lines with word proposed.

After that, do:

```
sudo apt-get update
```

and upon _successfully update_ repositroy run again:

```
sudo ./hardy.sh
```

If still get the same error, try downgrading the packages mentioned in the error:

Open synaptic, downgrade below package:
- libc6          to (= 2.7-10ubuntu3)   from 2.7-10ubuntu4 
- libdbus-1-3    to (= 1.1.20-1ubuntu1) from 1.1.20-1ubuntu2 
- libfreetype6   to (= 2.3.5-1ubuntu4)  from 2.3.5-1ubuntu4.8.04.1

etc......

After downgrading, run again sudo ./hardy.sh.

DK

---

### Post by Juggercat on 2008-10-14
ok thx for all ur help so far... really thx a lot... ok so i installed teh dependencies...

in other words... i managed to get this part of teh code to work...

sudo apt-get install build-essential

but when trying to install teh dependencies for wine...i get the following error...

rodrigo@Lilith:~/Desktop$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for wine could not be satisfied.
rodrigo@Lilith:~/Desktop$ 


:S:S here is where i get stumped... :S

lets see im following a how to... which told me to run the first line of code i specified.. up there... thx to ur help i managed to run that one.... but now i cant get the next line fo code to run....

this is the how to im following [http://ubuntuforums.org/showthread.php?t=795714](http://ubuntuforums.org/showthread.php?t=795714)

---

### Post by david_kt on 2008-10-14
> **Juggercat said:**
> 
lets see im following a how to... which told me to run the first line of code i specified.. up there... thx to ur help i managed to run that one.... but now i cant get the next line fo code to run....

this is the how to im following [http://ubuntuforums.org/showthread.php?t=795714](http://ubuntuforums.org/showthread.php?t=795714)

Have you tried my previous post suggestion? What is the outcome?

DK

---

### Post by Juggercat on 2008-10-15
well ive followed all ur posts until now... i was able to run the hardy.sh command.... and after that i was able to run the code:

sudo apt-get install build-essential


but then when i try to install the dependencies for wine... i get the same error as before... :S :S :S


rodrigo@Lilith:~/Desktop$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Build-dependencies for wine could not be satisfied.
rodrigo@Lilith:~/Desktop$

---

### Post by david_kt on 2008-10-15
> **Juggercat said:**
> well ive followed all ur posts until now... i was able to run the hardy.sh command.... and after that i was able to run the code:
rodrigo@Lilith:~/Desktop$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Build-dependencies for wine could not be satisfied.
rodrigo@Lilith:~/Desktop$

After follow my suggestion, you could skip sudo apt-get build-dep wine.
But make sure when you run ./hardy.sh there is no error.

DK

---

### Post by Juggercat on 2008-10-16
thx for everything, i managed to compile it... but it didnt work right... seems im missing something... meh...

thx for everything anyway... ill try fix this somehow...

---

### Post by david_kt on 2008-10-16
> **Juggercat said:**
> thx for everything, i managed to compile it... but it didnt work right... seems im missing something... meh...

thx for everything anyway... ill try fix this somehow...

I suspect you did not ( successfully) patched it. You need to put the proper patch at proper directory, and apply patch from proper directory.

That thread you are reading does not explain it clearly. Delete the extracted wine and re-extract new one. Open text editor and copy and paste below patch:
```
diff --git a/dlls/winex11.drv/event.old b/dlls/winex11.drv/event.c
index 764e4da..4adc6b5 100644
--- a/dlls/winex11.drv/event.old
+++ b/dlls/winex11.drv/event.c
@@ -306,7 +306,7 @@ static inline void call_event_handler( Display *display, XEvent *event )
 
     if (XFindContext( display, event->xany.window, winContext, (char **)&hwnd ) != 0)
         hwnd = 0;  /* not for a registered window */
-    if (!hwnd && event->xany.window == root_window) hwnd = GetDesktopWindow();
+    if (!hwnd && event->xany.window == root_window) hwnd = 0; /* replaced "GetDesktopWindow()" with "0" */
 
     TRACE( "%s for hwnd/window %p/%lx\n",
            dbgstr_event( event->type ), hwnd, event->xany.window );
@@ -433,7 +433,7 @@ static inline BOOL can_activate_window( HWND hwnd )
     LONG style = GetWindowLongW( hwnd, GWL_STYLE );
     if (!(style & WS_VISIBLE)) return FALSE;
     if ((style & (WS_POPUP|WS_CHILD)) == WS_CHILD) return FALSE;
-    if (hwnd == GetDesktopWindow()) return FALSE;
+    if (hwnd == 0) return FALSE; /* replaced "GetDesktopWindow()" with "0" */
     return !(style & WS_DISABLED);
 }
 
@@ -656,7 +656,7 @@ static void X11DRV_FocusOut( HWND hwnd, XEvent *xev )
         if (hwnd == GetForegroundWindow())
         {
             TRACE( "lost focus, setting fg to desktop\n" );
-            SetForegroundWindow( GetDesktopWindow() );
+            SetForegroundWindow( 0 ); /* replaced "GetDesktopWindow()" with "0" */
         }
     }
 }

```

save it as desktop_switching.patch to /wine-X.X.X/dlls/winex11.drv directory of the extracted wine source you want to patch.

Open terminal, and cd to /path/to/wine-X.X.X/dlls/winex11.drv and then only you could run:
```
patch -p1 <desktop_switching.patch

```

As for other patch, it goes to another directory. Open text editor and copy and paste below patch:

```
diff --git a/dlls/kernel32/sync.c b/dlls/kernel32/sync.c
index 08385f1..ec8c16a 100644
--- a/dlls/kernel32/sync.c
+++ b/dlls/kernel32/sync.c
@@ -1826,12 +1826,12 @@ HANDLE WINAPI CreateIoCompletionPort(HANDLE hFileHandle, HANDLE hExistingComplet
     TRACE("(%p, %p, %08lx, %08x)\n",
           hFileHandle, hExistingCompletionPort, CompletionKey, dwNumberOfConcurrentThreads);
 
-    if (hExistingCompletionPort && hFileHandle == INVALID_HANDLE_VALUE)
+/*    if (hExistingCompletionPort && hFileHandle == INVALID_HANDLE_VALUE)*/
     {
         SetLastError( ERROR_INVALID_PARAMETER);
         return NULL;
     }
-
+#if 0
     if (hExistingCompletionPort)
         ret = hExistingCompletionPort;
     else
@@ -1858,6 +1858,7 @@ fail:
         CloseHandle( ret );
     SetLastError( RtlNtStatusToDosError(status) );
     return 0;
+#endif
 }
 
 /******************************************************************************

```

save it as hosting.patch to /wine-X.X.X/dlls/kernel32 directory of the extracted wine source you want to patch.

Open terminal, and cd to /wine-X.X.X/dlls/kernel32and then only you could run:
```
patch -p1 <hosting.patch
```

After that you could start compiling it.

DK

---

### Post by Juggercat on 2008-10-17
i get an error when doing the first patch :

[email]rodrigo@Lilith:~/Desktop/wine-1.1.5/dlls/winex11.drv[/email]$ patch -p1 <desktop_switching.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/dlls/winex11.drv/event.old b/dlls/winex11.drv/event.c
|index 764e4da..4adc6b5 100644
|--- a/dlls/winex11.drv/event.old
|+++ b/dlls/winex11.drv/event.c
--------------------------
File to patch: 

and it stays there askign me what file i want to patch... :S

---

### Post by david_kt on 2008-10-17
> **Juggercat said:**
> i get an error when doing the first patch :

[email]rodrigo@Lilith:~/Desktop/wine-1.1.5/dlls/winex11.drv[/email]$ patch -p1 <desktop_switching.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/dlls/winex11.drv/event.old b/dlls/winex11.drv/event.c
|index 764e4da..4adc6b5 100644
|--- a/dlls/winex11.drv/event.old
|+++ b/dlls/winex11.drv/event.c
--------------------------
File to patch: 

and it stays there askign me what file i want to patch... :S

Sure, you are using different wine. From the thread, this patch is for wine-1.0-rc1. Patch are specific to a wine version or versions.

DK

---

### Post by Juggercat on 2008-10-19
yup im using that wine version and i get this error... :

[email]rodrigo@Lilith:~/Desktop/wine-1.0-rc1/dlls/winex11.drv[/email]$ patch -p1 <desktop_switching.patch 
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/dlls/winex11.drv/event.old b/dlls/winex11.drv/event.c
|index 764e4da..4adc6b5 100644
|--- a/dlls/winex11.drv/event.old
|+++ b/dlls/winex11.drv/event.c
--------------------------
File to patch:

---

### Post by david_kt on 2008-10-19
> **Juggercat said:**
> yup im using that wine version and i get this error... :

[email]rodrigo@Lilith:~/Desktop/wine-1.0-rc1/dlls/winex11.drv[/email]$ patch -p1 <desktop_switching.patch 
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/dlls/winex11.drv/event.old b/dlls/winex11.drv/event.c
|index 764e4da..4adc6b5 100644
|--- a/dlls/winex11.drv/event.old
|+++ b/dlls/winex11.drv/event.c
--------------------------
File to patch:
I think I my instruction is wrong.

Remove -p1 and see how it work:
```

patch <desktop_switching.patch
```

DK

---

### Post by Juggercat on 2008-10-20
[email]rodrigo@Lilith:~/Desktop/wine-1.0-rc1/dlls/winex11.drv[/email]$ patch <desktop_switching.patch 
patching file event.c
[email]rodrigo@Lilith:~/Desktop/wine-1.0-rc1/dlls/winex11.drv[/email]$ 

thats what i get.. does that mean it worked?

---

### Post by david_kt on 2008-10-20
> **Juggercat said:**
> [email]rodrigo@Lilith:~/Desktop/wine-1.0-rc1/dlls/winex11.drv[/email]$ patch <desktop_switching.patch 
patching file event.c
[email]rodrigo@Lilith:~/Desktop/wine-1.0-rc1/dlls/winex11.drv[/email]$ 

thats what i get.. does that mean it worked?

Yes. After you apply both patch, you could start compiling and run your program.

DK

---

### Post by Juggercat on 2008-10-21
yey! thx for everything! :D:D:D

---

