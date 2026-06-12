---
title: "Is there an easier way to deal with WINEPREFIX?"
date: 2008-11-12
forum: Wine
---

### Post by theShaggy on 2008-11-12
I've been using Ubuntu and Wine coming up on a year now, but only recently discovered the usefulness of the WINEPREFIX setting.

The thing is, it can be time consuming when installing a program, since you have to create a directory for the prefix, then set the command and remember to load it from that prefix each time - not to mention that Wincfg is reset for each one.

I know Cedega does it all automatically for you, is there a script we can use for this to work in Wine?  I'm not a programmer or an advanced user (though would actually like to learn for something like his), so building a script from scratch is unreasonable.

Secondly, is there any way to run a single Mono install across multiple wineprefixes?  It's quite a sizeable thing and takes a lot of space if more than one program requires Dotnet.

Thanks!

---

### Post by cogadh on 2008-11-12
One of the third-party Wine front ends, like WineDoors or Bordeaux, may be able to do that for you. I don't know of any script that can do that for you. However, once you have your application installed, the shortcuts that are created in the applications menu will already have the prefix included, so as long as you are using them to run the app, you don't have to worry about the prefix at all. The only time you would have to worry about it is when you create it and and when you run the initial install of the application.

There is no way to have a single install run in multiple prefixes. Each prefix is essentially a separate hidden "fake Windows" directory, none of which are "aware" of each other. That is why each has its own configuration (winecfg is not reset, they are completely different config files).

---

### Post by theShaggy on 2008-11-12
I will have a look at the third-party programs.  Thanks :-)

With desktop launchers the WINEPREFIX is already set, however Wine hasn't added programs to my applications menu in months.  I'm not sure why it hasn't.

I think the function I would like to see added is the ability to work directly in that particular prefix at the command line without having to constantly add "env WINEPREFIX=prefixlocation" for every command I want to use.

As for mono: that's what I feared.  I haven't had much luck using the dotnet install from Winetricks, but Mono is well over 200 megabytes alone - not really efficient for a single program to run.

---

### Post by Craig73 on 2009-01-13
> I think the function I would like to see added is the ability to work directly in that particular prefix at the command line without having to constantly add "env WINEPREFIX=prefixlocation" for every command I want to use.

At the command prompt type "export wineprefix=..." and hit enter

This sets the environment variable (under exports) so that anything you launch from that shell session will have that variable.  (No need to type env everytime)


> As for mono: that's what I feared.  I haven't had much luck using the dotnet install from Winetricks, but Mono is well over 200 megabytes alone - not really efficient for a single program to run.

I had been wondering about this, more from a multiuser angle, and perhaps a solution would be to install dotnet to it's own wineprefix (that you would never use directly).  Then, when setting up a new program, copy that dotnet wineprefix to the new wineprefix name, and then replace all DLL/EXE's with symbolic links back to the original DLLs.  

Then the registry and any other files that might get modified are unique to the new WINEPREFIX, and all the binaries are confined to a separate folder.  

A little bit of work, but a script should help speed up creating all the symbolic links.  This is a bit of a hack, but should work.  This approach might not be so easy when you need to upgrade dotnet because you would need an approach to merge in registry changes [assuming that in an upgrade situation you wouldn't just start over anyway now that wineprefix has allowed you to segregate everything]

---

### Post by Craig73 on 2009-01-13
> I think the function I would like to see added is the ability to work directly in that particular prefix at the command line without having to constantly add "env WINEPREFIX=prefixlocation" for every command I want to use.

At the command prompt type "export wineprefix=..." and hit enter

This sets the environment variable (under exports) so that anything you launch from that shell session will have that variable.  (No need to type env everytime)


> As for mono: that's what I feared.  I haven't had much luck using the dotnet install from Winetricks, but Mono is well over 200 megabytes alone - not really efficient for a single program to run.

I had been wondering about this, more from a multiuser angle, and perhaps a solution would be to install dotnet to it's own wineprefix (that you would never use directly).  Then, when setting up a new program, copy that dotnet wineprefix to the new wineprefix name, and then replace all DLL/EXE's with symbolic links back to the original DLLs.  

Then the registry and any other files that might get modified are unique to the new WINEPREFIX, and all the binaries are confined to a separate folder.  

A little bit of work, but a script should help speed up creating all the symbolic links.  This is a bit of a hack, but should work.  This approach might not be so easy when you need to upgrade dotnet because you would need an approach to merge in registry changes [assuming that in an upgrade situation you wouldn't just start over anyway now that wineprefix has allowed you to segregate everything]

---

### Post by Craig73 on 2009-01-13
> I think the function I would like to see added is the ability to work directly in that particular prefix at the command line without having to constantly add "env WINEPREFIX=prefixlocation" for every command I want to use.

At the command prompt type "export wineprefix=..." and hit enter

This sets the environment variable (under exports) so that anything you launch from that shell session will have that variable.  (No need to type env everytime)


> As for mono: that's what I feared.  I haven't had much luck using the dotnet install from Winetricks, but Mono is well over 200 megabytes alone - not really efficient for a single program to run.

I had been wondering about this, more from a multiuser angle, and perhaps a solution would be to install dotnet to it's own wineprefix (that you would never use directly).  Then, when setting up a new program, copy that dotnet wineprefix to the new wineprefix name, and then replace all DLL/EXE's with symbolic links back to the original DLLs.  

Then the registry and any other files that might get modified are unique to the new WINEPREFIX, and all the binaries are confined to a separate folder.  

A little bit of work, but a script should help speed up creating all the symbolic links.  This is a bit of a hack, but should work.  This approach might not be so easy when you need to upgrade dotnet because you would need an approach to merge in registry changes [assuming that in an upgrade situation you wouldn't just start over anyway now that wineprefix has allowed you to segregate everything]

---

### Post by Craig73 on 2009-01-13
> I think the function I would like to see added is the ability to work directly in that particular prefix at the command line without having to constantly add "env WINEPREFIX=prefixlocation" for every command I want to use.

At the command prompt type "export wineprefix=..." and hit enter

This sets the environment variable (under exports) so that anything you launch from that shell session will have that variable.  (No need to type env everytime)


> As for mono: that's what I feared.  I haven't had much luck using the dotnet install from Winetricks, but Mono is well over 200 megabytes alone - not really efficient for a single program to run.

I had been wondering about this, more from a multiuser angle, and perhaps a solution would be to install dotnet to it's own wineprefix (that you would never use directly).  Then, when setting up a new program, copy that dotnet wineprefix to the new wineprefix name, and then replace all DLL/EXE's with symbolic links back to the original DLLs.  

Then the registry and any other files that might get modified are unique to the new WINEPREFIX, and all the binaries are confined to a separate folder.  

A little bit of work, but a script should help speed up creating all the symbolic links.  This is a bit of a hack, but should work.  This approach might not be so easy when you need to upgrade dotnet because you would need an approach to merge in registry changes [assuming that in an upgrade situation you wouldn't just start over anyway now that wineprefix has allowed you to segregate everything]

---

### Post by Craig73 on 2009-01-13
What do you know... with all these server busy messages it queued my submission and all the re-submits (sorry about the dups)

---

