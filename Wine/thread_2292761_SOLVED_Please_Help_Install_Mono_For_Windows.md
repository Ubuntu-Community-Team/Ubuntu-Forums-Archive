---
title: "SOLVED Please Help Install Mono For Windows"
date: 2015-08-30
forum: Wine
---

### Post by lambdafox on 2015-08-30
I am running Xubuntu 15.10 amd64

I installed wine, and am trying to install a program called ID3-TagIT

```
wine "c:\Program Files (x86)\ID3-TagIT 3\ID3-TagIT.exe"
wine: Install Mono for Windows to run .NET applications.
```

I downloaded the mono installer which is an msi file.

```
:~/Downloads$ wine msiexec -i mono.msi
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
fixme:storage:create_storagefile Storage share mode not implemented.
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 3 out of range
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 3 out of range
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 3 out of range
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 3 out of range

```

For simplicity, I renamed the mono installer, btw

---

### Post by coldraven on 2015-08-31
Mono is in the Software centre, I don't know for sure but  maybe that is the package that Wine refers to.

mono-runtime:
> Mono is a platform for running and developing applications based on the
ECMA/ISO Standards. Mono is an open source effort led by Xamarin.
Mono provides a complete CLR (Common Language Runtime) including compiler and
runtime, which can produce and execute CIL (Common Intermediate Language)
bytecode (aka assemblies), and a class library.

This package contains the Virtual Machine, JIT (Just-in-Time) and
AOT (Ahead-of-Time) code generator "mono-sgen".
mono-sgen executes applications for the CLI (Common Language Infrastructure).
Mono currently only supports the X86, PowerPC, ARM, S/390x, AMD64 and
MIPS architectures.

This package installs this architecture's default runtime version.

---

### Post by lambdafox on 2015-08-31
> **coldraven said:**
> Mono is in the Software centre, I don't know for sure but  maybe that is the package that Wine refers to.

mono-runtime:

Wine needs _**Mono for Windows**_ to run .Net applications.

The problem is with installing _**Mono for Windows**_ using Wine

---

### Post by mystics on 2015-08-31
What version of Wine are you running?

Here's what [Wine's website]("http://wiki.winehq.org/Mono") says about Mono:

> 
**For Wine releases 1.5.3 and later, the Wine Mono  package is recommended.** For earlier versions, an official Windows  release of Mono 2.10 is recommended. 

**Wine 1.5.6 will install Wine Mono automatically as needed.** It will search for the MSI in the following locations:
--The Unix directory stored in the "[MonoCabDir]("http://wiki.winehq.org/MonoCabDir")" value at HKCU\Software\Wine\Dotnet.
--/usr/share/wine/mono, or possibly some substitution for /usr if Wine was installed to a different location.
--wine_build_directory/../mono, if Wine is being run from a build tree.
 --Download from [http://source.winehq.org/winemono.php](http://source.winehq.org/winemono.php)


...

**In modern Wine (>= 1.5.6), without Wine Mono** installed it will appear  to Windows applications that .NET is not installed, so the only real  option is to use that package.


Emphasis added.

In other words, if you're running a version of Wine that's 1.5.3 or later, then you should be using Wine Mono, not Mono for Windows. If it didn't just download and install the necessary file mentioned above, you can always go to the link, download the file yourself, and place it in one of the necessary directories. There may already be a version of Wine Mono there (probably 0.0.8), but the one above should be more recent.

---

### Post by lambdafox on 2015-09-01
> **mystics said:**
> What version of Wine are you running?

Here's what [Wine's website]("http://wiki.winehq.org/Mono") says about Mono:



Emphasis added.

In other words, if you're running a version of Wine that's 1.5.3 or later, then you should be using Wine Mono, not Mono for Windows. If it didn't just download and install the necessary file mentioned above, you can always go to the link, download the file yourself, and place it in one of the necessary directories. There may already be a version of Wine Mono there (probably 0.0.8), but the one above should be more recent.

Wine is 1.6.2 from the ubuntu repository.  wine-mono is installed and it is version 0.0.8.

---

### Post by mystics on 2015-09-01
> **lambdafox said:**
> Wine is 1.6.2 from the ubuntu repository.  wine-mono is installed and it is version 0.0.8.

Wine Mono 0.0.8, despite being the default, is well outdated. Try updating it to version 4.5.6, which is the version linked on Wine's website:[ http://source.winehq.org/winemono.php]("http://source.winehq.org/winemono.php") 

It's possible that the updated version will fix the problem.

---

### Post by lambdafox on 2015-09-01
> **mystics said:**
> Wine Mono 0.0.8, despite being the default, is well outdated. Try updating it to version 4.5.6, which is the version linked on Wine's website:[ http://source.winehq.org/winemono.php]("http://source.winehq.org/winemono.php") 

It's possible that the updated version will fix the problem.

The wine website is unclear on a couple of things...

1)  I can see that wine-mono-0.0.8.msi is in \usr\share\wine\mono, do I need to uninstall that version?

2)  Do I just copy the wine-mono-4.5.6.msi to that directory, or do I need to use *wine msiexec* with it?

[This thread]("https://forum.winehq.org/viewtopic.php?f=8&t=24506") suggests the wine-mono 4.56 is not compatible with Wine 1.6.2 at all, only the beta version 1.7.38 and newer.

---

### Post by lambdafox on 2015-09-01
I found many threads about wine 1.6.2 not sensing that wine-mono 0.0.8 is installed.  None of the tricks I found worked for me.  I have purged wine and am going to try installing 1.7 from the ubuntu-wine/ppa...

---

### Post by mystics on 2015-09-01
> **lambdafox said:**
> [This thread]("https://forum.winehq.org/viewtopic.php?f=8&t=24506") suggests the wine-mono 4.56 is not compatible with Wine 1.6.2 at all, only the beta version 1.7.38 and newer.

That's surprising. I could have sworn that I had it working on Wine 1.6.2 before. Maybe it was something else and my memory is just faulty. Sorry for leading you down that dead end.

---

### Post by lambdafox on 2015-09-04
I am pretty sure that this is because of[ this bug]("https://bugs.launchpad.net/ubuntu/+source/wine1.6/+bug/1383214").  The repository still lists 1:1.6.2-0ubuntu8 for vivid amd64.  It is supposedly fixed in 1:1.6.2-0ubuntu10.  I don't have time to try this this morning, but if it hasn't made it into the repository, I will try the -proposed version tomorrow.

---

### Post by lambdafox on 2015-09-05
> **lambdafox said:**
> I am pretty sure that this is because of[ this bug]("https://bugs.launchpad.net/ubuntu/+source/wine1.6/+bug/1383214").  The repository still lists 1:1.6.2-0ubuntu8 for vivid amd64.  It is supposedly fixed in 1:1.6.2-0ubuntu10.  I don't have time to try this this morning, but if it hasn't made it into the repository, I will try the -proposed version tomorrow.

Because I am a linux / ubuntu newbie, I want to run this by you all, before I try this:

To install the -proposed version of wine, but not open all packages for that, I believe this is what I need to do:

1.  open synaptic

2. on Settings-Repositories-Updates, tick Pre-released updates (vivid-proposed)

3. Create a text file in /etc/apt/preferences.d called proposed-updates with this content: 
 ```
Package: *
Pin: release a=vivid-proposed
Pin-Priority: 400
```

After that do I use package force version to install the -proposed wine?

---

### Post by lambdafox on 2015-09-06
> **lambdafox said:**
> I found many threads about wine 1.6.2 not sensing that wine-mono 0.0.8 is installed.  None of the tricks I found worked for me.  I have purged wine and am going to try installing 1.7 from the ubuntu-wine/ppa...

It just came to my attention that I never posted a follow-up to this statement.  Wine 1.7 on the wine ppa and in the repositories behaves exactly the same, that is to say, despite wine-mono being installed I get the exact same message.

---

### Post by lambdafox on 2015-09-09
I was never able to get Mono to work.  I was, however, able to install .net 2.0, which works with my application.

Here is how:
1) purge wine, winetricks, wine-gecko and wine mono.
2) delete the .wine folder from my home directory
3) add  the wine ppa to sources
ubuntu ppa
4) install latest wine1.7, winbind and winetricks
5) WINEARCH=win32 winecfg
6) WINEARCH=win32 winetricks, then install dotnet20
7) WINEARCH=win32 winefile, then double click installer

Now my application runs -- woo hoo!

---

### Post by lambdafox on 2015-10-27
[COLOR=#000000][INDENT]Xubuntu Wiley is missing a package needed to install wine1.7

3) add the [COLOR=#417394]wine[/COLOR] ppa to sources
ubuntu ppa
4) install latest wine1.6, winbind and winetricks
5) WINEARCH=win32 winecfg
do not auto install mono
do auto install gecko
6) WINEARCH=win32 winetricks, then install dotnet20
7) WINEARCH=win32 winefile, then double click installer

Now my application runs -- woo hoo![/INDENT]


[/COLOR]

---

