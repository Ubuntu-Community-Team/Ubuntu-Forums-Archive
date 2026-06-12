---
title: "evergreen library software"
date: 2013-10-18
forum: Wine
---

### Post by cmcanulty on 2013-10-18
I use evergreen library software at our local library. It always worked fine with wine. Now they did ad upgrade and I can't launch it anymore. I get a very long error message. Can someone give me a suggestion? Wine error is below
```

Unhandled exception: unimplemented function MSVCR80.dll.atoi called in 32-bit code (0x7bc4e430).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc4e430 ESP:0033dde4 EBP:0033de48 EFLAGS:00000202(   - --  I   - - - )
 EAX:01778e88 EBX:7bcbdff4 ECX:01f82131 EDX:00000004
 ESI:0033ddf0 EDI:0000000f
Stack dump:
0x0033dde4:  00000000 00000004 7e53b88e 80000100
0x0033ddf4:  00000001 00000000 7bc4e430 00000002
0x0033de04:  0177b978 01778e88 7e4fda1f 0033de30
0x0033de14:  0180a250 00b77e82 7e4fda1f 00000029
0x0033de24:  00000004 00000000 01f821be 0033de64
0x0033de34:  7e571ff4 0033de60 7e4fdbe8 0000003b
Backtrace:
=>0 0x7bc4e430 call_dll_entry_point+0x310() in ntdll (0x0033de48)
  1 0x0034020d (0x0033de64)
0x7bc4e430 call_dll_entry_point+0x310 in ntdll: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (105 modules)
PE	  350000-  37a000	Deferred        nspr4
PE	  380000-  387000	Deferred        plc4
PE	  390000-  397000	Deferred        plds4
PE	  3a0000-  3a6000	Deferred        mozalloc
PE	  3b0000-  3c8000	Deferred        nssutil3
PE	  3d0000-  3f8000	Deferred        softokn3
PE	  400000-  434000	Deferred        evergreen
PE	  760000-  7e2000	Deferred        mozsqlite3
PE	  7f0000-  88d000	Deferred        nss3
PE	  890000-  8b5000	Deferred        ssl3
PE	  8c0000-  8d8000	Deferred        smime3
PE	  8e0000-  ab8000	Deferred        mozjs
PE	  ac0000- 1945000	Export          xul
PE	 1950000- 19e8000	Deferred        gkmedias
PE	 1df0000- 1df7000	Deferred        xpcom
PE	10000000-1000e000	Deferred        mozglue
ELF	7b800000-7ba5b000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba5b000	\               kernel32
ELF	7bc00000-7bcda000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcda000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d95c000-7d974000	Deferred        userenv<elf>
  \-PE	7d960000-7d974000	\               userenv
ELF	7d974000-7daa8000	Deferred        oleaut32<elf>
  \-PE	7d990000-7daa8000	\               oleaut32
ELF	7daa8000-7daea000	Deferred        usp10<elf>
  \-PE	7dab0000-7daea000	\               usp10
ELF	7daea000-7db5a000	Deferred        setupapi<elf>
  \-PE	7daf0000-7db5a000	\               setupapi
ELF	7db5a000-7db90000	Deferred        uxtheme<elf>
  \-PE	7db60000-7db90000	\               uxtheme
ELF	7db90000-7dc98000	Deferred        comctl32<elf>
  \-PE	7dba0000-7dc98000	\               comctl32
ELF	7dc98000-7dd12000	Deferred        shlwapi<elf>
  \-PE	7dcb0000-7dd12000	\               shlwapi
ELF	7dd12000-7df45000	Deferred        shell32<elf>
  \-PE	7dd20000-7df45000	\               shell32
ELF	7df45000-7e086000	Deferred        msvcp90<elf>
  \-PE	7df80000-7e086000	\               msvcp90
ELF	7e086000-7e128000	Deferred        msvcp80<elf>
  \-PE	7e090000-7e128000	\               msvcp80
ELF	7e128000-7e264000	Deferred        ole32<elf>
  \-PE	7e140000-7e264000	\               ole32
ELF	7e2be000-7e2d2000	Deferred        msimg32<elf>
  \-PE	7e2c0000-7e2d2000	\               msimg32
ELF	7e2d2000-7e2f6000	Deferred        imm32<elf>
  \-PE	7e2e0000-7e2f6000	\               imm32
ELF	7e2f6000-7e321000	Deferred        msacm32<elf>
  \-PE	7e300000-7e321000	\               msacm32
ELF	7e321000-7e3a2000	Deferred        rpcrt4<elf>
  \-PE	7e330000-7e3a2000	\               rpcrt4
ELF	7e3a2000-7e45c000	Deferred        winmm<elf>
  \-PE	7e3b0000-7e45c000	\               winmm
ELF	7e45c000-7e482000	Deferred        iphlpapi<elf>
  \-PE	7e460000-7e482000	\               iphlpapi
ELF	7e482000-7e4b8000	Deferred        ws2_32<elf>
  \-PE	7e490000-7e4b8000	\               ws2_32
ELF	7e4b8000-7e4d4000	Deferred        wsock32<elf>
  \-PE	7e4c0000-7e4d4000	\               wsock32
ELF	7e4d4000-7e57c000	Deferred        msvcrt<elf>
  \-PE	7e4f0000-7e57c000	\               msvcrt
ELF	7e57c000-7e582000	Deferred        libxfixes.so.3
ELF	7e582000-7e58d000	Deferred        libxcursor.so.1
ELF	7e58d000-7e59d000	Deferred        libxi.so.6
ELF	7e59d000-7e5a1000	Deferred        libxcomposite.so.1
ELF	7e5a1000-7e5aa000	Deferred        libxrandr.so.2
ELF	7e5aa000-7e5b4000	Deferred        libxrender.so.1
ELF	7e5b4000-7e5ba000	Deferred        libxxf86vm.so.1
ELF	7e5ba000-7e5c1000	Deferred        libxdmcp.so.6
ELF	7e5c1000-7e5e2000	Deferred        libxcb.so.1
ELF	7e5e2000-7e5e8000	Deferred        libuuid.so.1
ELF	7e5e8000-7e602000	Deferred        libice.so.6
ELF	7e602000-7e736000	Deferred        libx11.so.6
ELF	7e736000-7e748000	Deferred        libxext.so.6
ELF	7e748000-7e751000	Deferred        libsm.so.6
ELF	7e753000-7e781000	Deferred        msvcr80<elf>
  \-PE	7e760000-7e781000	\               msvcr80
ELF	7e783000-7e815000	Deferred        winex11<elf>
  \-PE	7e790000-7e815000	\               winex11
ELF	7e94b000-7e975000	Deferred        libexpat.so.1
ELF	7e975000-7e9a9000	Deferred        libfontconfig.so.1
ELF	7e9a9000-7ea43000	Deferred        libfreetype.so.6
ELF	7ea45000-7ea49000	Deferred        libxinerama.so.1
ELF	7ea49000-7ea4d000	Deferred        libxau.so.6
ELF	7ea75000-7eae4000	Deferred        advapi32<elf>
  \-PE	7ea80000-7eae4000	\               advapi32
ELF	7eae4000-7ec02000	Deferred        gdi32<elf>
  \-PE	7eaf0000-7ec02000	\               gdi32
ELF	7ec02000-7ed5d000	Deferred        user32<elf>
  \-PE	7ec10000-7ed5d000	\               user32
ELF	7ed5d000-7ed6a000	Deferred        libnss_files.so.2
ELF	7ed6a000-7ed76000	Deferred        libnss_nis.so.2
ELF	7ed76000-7ed90000	Deferred        libnsl.so.1
ELF	7ed90000-7ed99000	Deferred        libnss_compat.so.2
ELF	7ef99000-7efc5000	Deferred        libm.so.6
ELF	7efc5000-7efce000	Deferred        librt.so.1
ELF	7efd0000-7efe6000	Deferred        libz.so.1
ELF	7efe6000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f73b5000-f755e000	Deferred        libc.so.6
ELF	f755e000-f7563000	Deferred        libdl.so.2
ELF	f7564000-f757f000	Deferred        libpthread.so.0
ELF	f75b1000-f7767000	Dwarf           libwine.so.1
ELF	f7769000-f778b000	Deferred        ld-linux.so.2
ELF	f778b000-f778c000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001e    0
	0000001d    0
	00000018    0
	00000016    0
	00000014    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001c    0
	00000019    0
	00000017    0
	00000013    0
0000001a plugplay.exe
	00000020    0
	0000001f    0
	0000001b    0
00000021 explorer.exe
	00000023    0
	00000022    0
00000024 (D) C:\Program Files (x86)\Evergreen Staff Client 2.4\evergreen.exe
	00000027    0
	00000026    0
	00000025    0 <==
System information:
    Wine build: wine-1.6
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.5.0-23-generic
```

---

### Post by Lars Noodén on 2013-10-18
I'd say it looks like the first problem is trying to run it under WINE and not natively on Ubuntu server, Debian, Fedora, etc.  I didn't know there was a WINE version.  All the supporting components are in the repository: [http://evergreen-ils.org/egdownloads/](http://evergreen-ils.org/egdownloads/)  Can you try it on regular Ubuntu server?

I've only run Koha before, but that too ran on Debian.

---

### Post by cmcanulty on 2013-10-18
I have only run it on wine before. It is an exe not a deb and we don't use a server in the library.

---

### Post by Lars Noodén on 2013-10-19
The pre-requisites for Evergreen are available in the repository, so they could be added to a regular Ubuntu desktop, too. IMHO that would be about 1000% easier than trying WINE.  You could even set up a VM in Qemu or Virtualbox to do your initial testing and set up so that the experimentation is contained a little.

---

### Post by cmcanulty on 2013-10-19
I don't know how to do that, before I just clicked the .exe and it installed fine in wine and worked fine. There is no deb. No experimentation was required but the upgrade won't install in wine. the install from source looks way more complicated than a usual install from source.


```

Building the Staff Client on a Client Machine

This section is more toward an end-user who may wish to use Linux rather than Windows for client machines, but has limited Linux experience. The Staff Client can be built on Linux without installing the Evergreen Server component; this is a relatively simple process, compared to server installation, though does require some command-line work. The following directions are for building Staff Client version 1.2.1.4 on Kubuntu 7.10, so you may need to modify them for other distributions (these instructions should work as-is for Ubuntu or Ubuntu derivatives).
1: Prerequisites

    subversion client
    xulrunner

Using apt-get to acquire these:

sudo apt-get install subversion
sudo apt-get install xulrunner

Synaptic can also be used; search for subversion and select the latest version, and search for xulrunner and select version 1.8.1.4-2ubuntu5.
2: Download the Source Code
2a: Determine which version is needed.

For most end-users, a specific version is required to communicate properly with the Evergreen server. Check with your system admin, IT person, or HelpDesk to determine which Staff Client versions are supported.

Next, you'll need to determine which tag to use when downloading the source code. Tags are markers in the source code to create a snapshot of the code as it existed at a certain time; tags usually point to tested and stable code, or at least a community-recognized release version.

To determine which tag to use, browse to http://git.evergreen-ils.org/?p=Evergreen.git;a=summary. The summary page includes a list of tags and branches. Depending on whether a release was made before or after the project moved to Git, select either the Git tag or the branch converted from an SVN release tag (e.g., tags/rel_1_2_1_4.)
2b: Download the Source Code.

Now, open a terminal (command-line prompt) and navigate to the directory in which you wish to download the staff client. Navigate to the desired directory and use the following command to download the proper version of the source code by tag:

git clone git://git.evergreen-ils.org/Evergreen.git
git checkout -b tmp_branch origin/rel_1_2_1 # or git checkout rel_1_2_1

Note that you'll want to change “rel_1_2_1_4” to the appropriate tag for your installation.
3: Build the Staff Client.
Evergreen 1.2.x

From the command line, navigate to the directory in which you downloaded the source code. Then, navigate to the proper subdirectory:

cd Open-ILS/xul/staff_client

Now, we'll run the “make” script to actually build the Staff Client files. Be sure to check wtih your sysadmin about which “Staff Client Build ID” to use; the server checks the Staff Client Build ID against itself to determine whether or not a connecting client is supported. For the PINES installation at 1.2.1.4, the supported build id is “rel_1_2_1_4”. Modify the following command accordingly:

make STAFF_CLIENT_BUILD_ID='rel_1_2_1_4'

Evergreen 1.4.x

The 1.4 series of Evergreen has complicated the build process for staff clients a bit. If you downloaded a .tar.gz (tarball) of Evergreen, then your steps will resemble:

FIXME – Need instructions for getting certain Javascript files from OpenSRF, preferably without actually installing OpenSRF.

wget http://evergreen-ils.org/downloads/Evergreen-ILS-1.4.0.4.tar.gz
tar xfz Evergreen-ILS-1.4.0.4.tar.gz
cd Evergreen-ILS-1.4.0.4/
./configure --prefix=/openils --sysconfdir=/openils/conf
cd Open-ILS/xul/staff_client/
make STAFF_CLIENT_BUILD_ID='rel_1_4_0_4' install

If you're installing from a Subversion checkout:

git clone git://git.evergreen-ils.org/Evergreen.git
git checkout rel_1_4_0_4
./autogen.sh   # If you downloaded a .tar.gz of Evergreen, you may skip this step
./configure --prefix=/openils --sysconfdir=/openils/conf
cd Open-ILS/xul/staff_client/
make STAFF_CLIENT_BUILD_ID='rel_1_4_0_4' install

4: Run the Staff Client (from the command line).

Navigate to the 'build' subdirectory, then run the following command:

xulrunner application.ini

Make sure you run this from 'build\', not from 'staff_client\'.
5: Cleaning Up/Creating Shortcuts (Optional)

The source code download included many files that are needed to build the Staff Client, but not necessary to run it. You may wish to remove them to save space, or to create a directory containing the built staff client that can be copied to other machines.\ To do this, first create the directory where you wish to place your 'finished' staff client:

 mkdir ~/<Destination Directory> 

Then, copy the 'staff_client' directory to it:

cd ~/<Download Directory>/Open-ILS/xul/
cp -r staff_client ~/<Destination Directory>

Test to verify that all the necessary files were moved to the destination directory:

cd ~/<Destination Directory>/staff_client/build
xulrunner application.ini

The Staff Client should run properly. Now remove the original download directory and all sub directories:

rm -r -f ~/<Download Directory>

Almost done! Now, the command

xulrunner ~/<Destination Directory>/staff_client/build/application.ini

will run the Staff Client. You may wish to create Desktop/Start Menu/K-Menu shortcuts for the Staff Client. To do so, use the previous command as the target.
Using Wine to Install On Linux

Wine is also an alternative for those who want to install the packaged Windows versions rather than building the Staff Client manually. Wine is application that allows Linux users to run Windows executables, and is a simple way for casual Linux users to use the Evergreen Staff Client.

1: Install Wine (using apt-get):

   command-prompt:~/sudo apt-get install wine
```

---

### Post by Lars Noodén on 2013-10-19
They do seem to go out of their way to punish Linux users.  Of 2a and 2b, I would go with 2b.  git is not that hard and there is a lot of material online for it.  Do you have the version or "tag" for your server?  I don't know how tightly integrated they are, but it's probably a good idea for them to match.

---

### Post by cmcanulty on 2013-10-19
As I said we don't use a server just workstations. The library software server covers many states.I just want to install the  staff client.
 I am attaching a screenshot of the previous version running in wine

[ATTACH=CONFIG]247071[/ATTACH]

---

### Post by Lars Noodén on 2013-10-19
I've been looking but the 3 sets of instructions so far seem to be a combination of out of date, incomplete and somewhat wrong.  I'm wondering if the mailing lists would be of use.

---

