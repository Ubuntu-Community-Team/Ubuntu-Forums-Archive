---
title: "Intel MKL Installation not working on Ubuntu 6.10"
date: 2006-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by BodyWeapon on 2006-10-28
[Problem resolved now]

In order to install mkl on 6.10, one need to get the RPM version of the mkl. Then perform a debian rpm install, and enjoy!

----------------------------
Original thread starts below
----------------------------
Dear All,

   My machine is a Dimension 9200, core 2 duo. I use the ubuntu 6.10 desktop for installation. 

   Everything goes well. (as long as packages are coming from synaptic/apt-get)

   But when I want to install Intel-MKL library. The installation script of intel is broken.

   The interesting thing is, I can use exactly the same script (just bash script) to run in Fedora core 5 (64-bit), but not in ubuntu 6.10.:-k 

   Anyway, when I run the installation script in Ubuntu 6.10, it will show
  
   install: 78: Syntax error: Bad for loop variable

   when the line is just a simple for loop statement.:confused: 

   So I go to the script and change the header from #!/bin/sh to #!/bin/bash and the script can go through the line.

   But then, the installation script will detect whether it is x86_64 or ia64. When it detects x86_64, it will use a binary called install32. but it cannot run....](*,) 

   did anyone have similar experience? May you please help?;) 

Thanks.

Bodyweapon

---

### Post by kuja on 2006-10-28
Just a small comment, I think Edgy uses dash for the default shell. It seems to be a bit more finicky with non-POSIX compliant scripts, but runs faster. I guess that script might not have been POSIX-compliant eh? You say that install32 cannot run, well, does it give you any sort of messages regarding it? Error messages perhaps?

---

### Post by BodyWeapon on 2006-10-28
When I run the install32 in ubuntu 6.10, it saids...

bash: ./install32: cannot execute binary file  :confused: 

Please help ](*,) 

Thanks

---

### Post by BodyWeapon on 2006-10-28
just to mention that the intel32 is the actual executable binaries.

in the installation script, it will either choose

intel32 (x86_64)

or

intel64 (ia64)

---

### Post by Celil Rifat on 2006-11-18
I changed the install script from sh to bash as suggested,  but then got stuck at this point:

./.././install/install: line 319: /tmp/install_temp.---------/install32: cannot execute binary file
Warning: It seems installation failed
Deleting temporary files...

How do you proceed?

---

### Post by mrphd on 2006-12-01
> **BodyWeapon said:**
> [Problem resolved now]

In order to install mkl on 6.10, one need to get the RPM version of the mkl. Then perform a debian rpm install, and enjoy!


Could you elaborate a bit on this? Where can I get an RPM version from? I'm trying to install it, but keep getting the "Bad for loop variable" error.

Thanks!

---

### Post by rcjhawk on 2006-12-13
> **mrphd said:**
> Could you elaborate a bit on this? Where can I get an RPM version from? I'm trying to install it, but keep getting the "Bad for loop variable" error.

Thanks!

OK, here's how I did it for version  8.1.024:

1) run the installation script at root:

sudo sudo ./install.sh

2) This will fail, so

cd /tmp/mkl

3) there you'll find a file named intel-mkl-8.1p-14.i386.rpm .  We need to convert this to a debian archive file:

sudo alien --to-deb --scripts intel-mkl-8.1p-14.i386.rpm

4) now install the resulting .deb:

dpkg -i intel-mkl_8.1p-15_all.deb

That's it.

Now all I have to do is figure out how to properly link the libraries with my Fortran code.  :-|

---

### Post by rcjhawk on 2006-12-13
> **rcjhawk said:**
> OK, here's how I did it for version  8.1.024:
Now all I have to do is figure out how to properly link the libraries with my Fortran code.  :-|

Found it, I think

ifort -o progname progname.f -L/opt/intel/mkl/8.1/lib/32 -lmkl_lapack -lmkl_ia32 -lguide -lpthread

seems to work (with everything on one line).

---

### Post by granziliao on 2007-01-01
A quick dirty hack is 
ln -sf /bin/bash /bin/sh
then execute MKLDIR/install.sh
after the installation (I mean the generation of the rpm file)
just link it back to /bin/dash.
It seems that Intel ships MKL with a buggy script.
This quick hack also works for ia32 users (in fact, this is a script problem, does not caused by the platform/binary compatibilties problems)

---

### Post by pokpig on 2007-05-18
thx for the post, I just want to verify that this is still the way to get intel mkl to work in 7.04 Feisty

here is what one should do

1.) download the intel mkl package and unpack it
2.) look at the install.sh file, somehow they know people want bash, they change the header to bash already, this is not good because in the middle somehow they mess things up and need sh, so you can either

a.) change the header to #!/bin/sh instead of #!/bin/bash

b.) go to /bin and link bash to sh as instructed in the previous post

3.) make sure you save the license file, the name is not important, but the extension is useful, I change it to abc.lic  .The location of license file is also not important, place it to some place that you know its path

4.) if you change it to /bin/sh, you need to run it by 
sh install.sh

otherwise use ./install.sh

5.) manually tell it where the license file is

6.) install is "successful", not quite of course, they think it is, but it is not, you successfully get the rpm file in /tmp/install_(rubbish no.!) 

7.) go to that folder and use alien to turn it to a deb as instructed here, the reminder is: it takes some time, be patient

8.) install the deb as instructed in previous few posts

9.) some tips

the installation place it in /opt/intel/ , you can of course copy the whole directory to the place you like, note that the libraries are in /opt/intel/mkl/9.0/lib/32/ , the ones that end with .a are the static library, in most of the case you may like to link it

to link it

ifort your_file.f90 -L<path_of_library> -l<library you need>

e.g if you are a good boy and leave the library path in /opt

ifort your_file.f90 -L/opt/intel/mkl/9.0/lib/32/ -lmkl_lapack -lmkl_ia32 -lguide

the naming convention for the library is

-l<name of library without the lib in front and the .a in the end>

so when you see libmkl_lapack.a there

link it by

-lmkl_lapack

Tired of typing the path?

I do it by


go to your home folder, edit .bashrc

define the path name and link option

lib_path="/opt/intel/mkl/9.0/lib/32"
link_them_all = "-lmkl_lapack -lmkl_ia32 -lguide "

then when you use the terminal again

ifort your_file.f90 -L$lib_path $link_them_all 

will do the job for you

hope it helps someone

---

### Post by GreenFlash on 2007-07-23
Very helpful post pokpig! It seems very fortunate for Debian based distributions that a failed MKL installation leaves a copy of the .rpm files in a temporary directory (or is this a standard trick?). The .rpm vs .deb issue was my main concern when I switched from openSUSE to Ubuntu, I hope my decision doesn't come back to bite me in the butt!

---

### Post by naveengv on 2007-10-18
Hi,
There is a workaround in Intel support site for installation of Intel MKL 9.1 on Ubuntu. 
To install Intel MKL on Ubuntu, set up a /bin/sh link to the /bin/bash interpreter and then run the installation.
1.	Remove the default link. 
                      rm /bin/sh 
2.	Reassign the link to the bash interpreter. 
	ln –s /bin/bash /bin/sh 
3.	Run the installation with options. 
	/install/install --nonrpm --dash-fix 
4.	Rollback to the default dash interpreter. 
	rm /bin/sh 
	ln –s /bin/dash /bin/sh

Refer below link for more information. 
[COLOR="Blue"]_[http://www.intel.com/support/performancetools/libraries/mkl/linux/sb/CS-027208.htm](http://www.intel.com/support/performancetools/libraries/mkl/linux/sb/CS-027208.htm)_[/COLOR]

Intel will be releasing latest version of MKL in early November 2007, which provide official support for Ubuntu. 

I will post in this forum for latest information about MKL release.

Regards,
Naveen Gv

---

