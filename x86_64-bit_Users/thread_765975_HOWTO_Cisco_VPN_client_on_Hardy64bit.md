---
title: "HOWTO: Cisco VPN client on Hardy/64bit"
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by ire on 2008-04-24
Just thought I'd share how I got the Cisco VPN client working on Hardy 64bit

1> Download most recent VPN client from Cisco CCO. I used:

vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz

2> Obtain patches:

wget  [http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff](http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff)
wget [http://tuxx-home.at/projects/cisco-vpnclient/cisco_skbuff_offset.patch](http://tuxx-home.at/projects/cisco-vpnclient/cisco_skbuff_offset.patch)

3> untar/unzip the VPN client, cd to vpnclient

4> Edit File Makefile

5> Change all 'CFLAGS' to 'EXTRA_CFLAGS' (minus the quote)

6> Apply patches:
patch < ../vpnclient-linux-2.6.24-final.diff
patch < ../cisco_skbuff_offset.patch

7> Compile/install:
sudo ./vpn_install

8> Start VPN client:
sudo /etc/init.d/vpnclient_init start

9> Put your PCF files into this directory, ie:
sudo cp myconnection.pcf /etc/opt/cisco-vpnclient/Profiles/

10> Make profiles directory readable to general users:
 sudo chmod -R 777 /etc/opt/cisco-vpnclient/Profiles/

11> Connect:
/usr/local/bin/vpnclient connect myconnection


Hope this helps!

Thanks to the website [http://tuxx-home.at/](http://tuxx-home.at/) for all the info, most of the above was found there.

---

### Post by dcstar on 2008-04-25
> **ire said:**
> Just thought I'd share how I got the Cisco VPN client working on Hardy 64bit
........

[http://ubuntuforums.org/showthread.php?p=4556713#post4556713](http://ubuntuforums.org/showthread.php?p=4556713#post4556713)

---

### Post by wetling on 2008-09-02
So...I'm just learning Linux with Ubuntu 8.04 x64 and I'm having some difficulty.  

I tried following the directions listed above, but when I enter: 

> sudo ./vpn_install

I receive the following error (near the end): 

> Failed to make module "cisco_ipsec.ko".

Then the command: 

> sudo /etc/init.d/vpnclient_init start

doesn't work (command not found).  What am I doing wrong?

---

### Post by Thelasko on 2008-09-03
I'm confused, what's wrong with the package "[network-manager-vpnc]("http://packages.ubuntu.com/hardy/network-manager-vpnc")" in the repositories?  It should install [Cisco compatible dependencies]("http://packages.ubuntu.com/hardy/vpnc") automatically.

---

### Post by cesar_spain on 2008-09-04
UPDATED TO LATEST CLIENT VERSION => Not tested, though, just updated stuff to download

Dear all:

    I have just written a script for installing Cisco VPN Client on Ubuntu 8.04. I tested it on two different machines, and it works. 

    Give it a try. When asking you things, just press enter.

     After that, you have it available in KVPNC Gui.

César

[PHP]
#!/bin/bash
#####################################
# INSTALL_VPN.SH
#####################################
#  Script for installing the Cisco
# VPN Client in Ubuntu 8.04 - 64 bits
#
#   It can be easily adapted for 
# other distros and architectures
#####################################
# Author : Cesar Delgado Gonzalez
# Version: 1.0
# Date   : 10-March-2007
#####################################

##################################
# ENVIRONMENT
#################################

# 0.- General Variables
#----------------------
ERROR=1
OK=0
TRIES=1 # Attempts per Mirror

# 1.- Where to download
#----------------------
WORK_DIR=$HOME

# Syntax: Program - Mirror 1 - Mirror 2 ... Mirror N

# 64 bits Arch
PROGRAM=(vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz       \
          http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.02/  \
        )

# Client for AMD 64 bits Processors
#PROGRAM=(vpnclient-linux-x86_64-4.8.02.0030-k9-AMD64_ONLY_by_t3x.tar.gz \
#          http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.02/    \
#        )


PATCH=(vpnclient-linux-4.8.02-64bit.patch	\
        http://projects.tuxx-home.at/ciscovpn/patches/ \
       )

PATCH_2=(cisco_skbuff_offset.patch         \
          http://projects.tuxx-home.at/ciscovpn/patches/ \
        )

# 3.- Current Kernel Version
#---------------------------
KERNEL=`uname -r`
TYPE_KERNEL=`uname -r | awk 'BEGIN {FS="-";}{print $3}'`


################################################################################
# MODULE MISCELLANEOUS ====> GENERAL FUNCTIONS 
################################################################################

#-----------------------------------------------------------------------
# AYUDA 
#-----------------------------------------------------------------------
#  Muestra la ayuda por pantalla
#-----------------------------------------------------------------------

ayuda()
{
   echo "installVPN.sh --> Install Cisco VPN Client in Ubuntu 8.04"
   echo "  Best way to use it is through KVPNC, since it integrates it" 
}


#-----------------------------------------------------------------------
# TRATA_ERRORES
#-----------------------------------------------------------------------
#   Trata todos los posibles errores del script.
#
#    Se considerar salida err ea a toda salida del script sin la creaci 
#  de una estructura de datos (por ejm.: opcion -h provoca salida errea).
#
#     Variables de entrada:
#         $1 = Tipo de Error
#         $2 = Ruta a la que el usuario no tiene acceso (inexistencia o permisos)
#         $3 = Directorio de Trabajo
#-----------------------------------------------------------------------
trataErrores()
{

  ERROR="1"

  case $1 in
     -ayuda) # Solicitud de ayuda
            ayuda
        exit $ERROR;;

     -tryMirror) 
        echo "===========> Trying PACKAGE: $3 "
        echo "               from MIRROR : $2 "
        echo;;

     -downloadSucceed) 
        echo
        echo "*********************************************************************************"
        echo " Download succeed FOR  $3 "
        echo "                  FROM $2 "        
        echo "*********************************************************************************"
        echo ""  ;;

     -downloadFailed) 
        echo 
        echo "*********************************************************************************"
        echo "ERROR: PACKAGE $3 not found in" 
        echo "       MIRROR  $2"
        echo "*********************************************************************************"
        echo "" ;;

     -noMirrors) # There is no mirrors for this package
         echo 
         echo "*********************************************************************************"
         echo "ERROR ==> Package $2 has no mirror list"
         echo "*********************************************************************************"
         exit $ERROR;;


     -packageNotFound) # Package not found on any mirror
         echo
         echo "*********************************************************************************"
         echo "ERROR ==> Package $2 not found on any mirror of the list"
         echo "*********************************************************************************"
         exit $ERROR;;

     -requiredPack) # Failed installing required packages
         echo "ERROR ==> Can't install required packages: Linux source + Build Essentials"
         exit $ERROR;;
      
     -decompress) 
           echo " ERROR ==> File / Directory Not Available => Unpack Failed, cleaning and exiting"
           cleanEnvironment
           exit $ERROR ;;

  esac
}

################################################################################
# MODULE DOWNLOAD ====> FUNCTIONS FOR DOWNLOADING THE PACKAGES 
################################################################################

#-----------------------------------------------------------------------
#  DOWNLOAD PACKAGE 
#-----------------------------------------------------------------------
#   Try to download one package
#  from several mirrors. If all of them
#  fails, return 1
#
#   $1 = Number of tries per mirror
#   $2 = Package to download 
#   $3 ...  $N = List of mirrors
#-----------------------------------------------------------------------
downloadPackage () { 


   # 1.- Check that exist at least one Mirror on the input List
   #-----------------------------------------------------------
   if [ $# = 2 ]; then 
      trataErrores -noMirrors $2


   # 2.- Search for a the package on the mirrors list
   #-----------------------------------------------------------
   else

       POSITION=1
       for MIRROR in $@; do

          # 2.1.- Capture tries per mirror
          if [ $POSITION = 1 ]; then
               TRIES=$MIRROR

          # 2.2.- Capture package name
          elif [ $POSITION = 2 ]; then
               PACKAGE=$MIRROR

          # 2.3.- Try to get the package from current mirror
          else

                # Try the download
                trataErrores -tryMirror $MIRROR $PACKAGE
                `wget --tries=$TRIES $MIRROR$PACKAGE` 

                # Check if succeed
              if [ $? = $OK ]; then
                   trataErrores -downloadSucceed $MIRROR$PACKAGE $PACKAGE
                   break;
                     
              fi

               # Report the fail
               trataErrores -downloadFailed $MIRROR$PACKAGE $PACKAGE

          fi

          # 2.4.- Incrementing position
          POSITION=`expr $POSITION + 1`

       done 
   fi

   # 4.- Package not found of the list of mirrors
   #-----------------------------------------------------------
   if [ $POSITION = $# ] && [ $? != $OK ]; then
    trataErrores -packageNotFound $PACKAGE
   fi
}

#-----------------------------------------------------------------------
#  GET PACKAGES 
#-----------------------------------------------------------------------
#   Downloading the packages
# from the current mirror
#-----------------------------------------------------------------------
getPackages() {

        echo  "================================================================================"
        echo  "                    DOWNLOADING CISCO VPN CLIENT "         
        echo  "================================================================================"
        echo
        downloadPackage $TRIES ${PROGRAM[*]}
         
        echo  "================================================================================"
        echo  "      DOWNLOADING UBUNTU PATCHES FOR KERNEL  = ${KERNEL} "
        echo  "================================================================================"
        echo
        downloadPackage $TRIES ${PATCH[*]}
        downloadPackage $TRIES ${PATCH_2[*]}
 }

#-----------------------------------------------------------------------
#  INSTALL REQUIRED PACKAGES 
#-----------------------------------------------------------------------
#   Procedure that install required 
#-----------------------------------------------------------------------
installDependencies() {
 
     echo  "=============================================================================================="
     echo  " INSTALLING REQUIRED UBUNTU PACKAGES: linux kernel + build essentials + unpacking packages    "
     echo  "=============================================================================================="
     echo  " --> Command: "
     echo  " sudo apt-get install  linux-${TYPE_KERNEL} linux-headers-${KERNEL} build-essential gcc gzip bzip zip unzip rar unrar "  
     sudo apt-get install  linux-${TYPE_KERNEL} linux-headers-${KERNEL} build-essential gcc gzip bzip2 zip unzip rar unrar 
      
     # Error Treatment
     if [ ! "$?" -eq "$OK" ] ; then
        trataErrores -requiredPack
     fi 
}


################################################################################
# MODULE INSTALL ====> FUNCTIONS FOR COMPILING AND INSTALLING PROGRAM 
################################################################################

#-----------------------------------------------------------------------
#  UNPACK PACKAGES 
#-----------------------------------------------------------------------
#   Uncompress packages. Check file extension and uncompress
#  properly
#-----------------------------------------------------------------------
unpackPackages() {


   #----------------------
   # ENVIRONMENT
   #----------------------
   local OUT=$OK

   #----------------------
   # ACTIONS
   #----------------------
 
   # 0.- Tracing
   #---------------------
   echo  "================================================================================"
   echo  "             UNPACK PACKAGE: $1  "
   echo  "================================================================================"
   echo
 
   # 1.- Deflating File
   #------------------------------------------------------------
   echo "................................. FILE DECOMPRESSION .............................. "
   echo "File Extension: \${1##*.}=${1##*.}"
   local EXTENSION=${1##*.}
   echo "File Name: \${1%.*}=${1%.*}"
   FILENAME=${1%.*}

   case "$EXTENSION" in
     gz)  echo " ===> Decompress gz: gunzip -d $1"
          gunzip -d "$1" ; OUT="$?" ;;
     bz)  echo " ===> Decompress bz: bzip2 -d $1"
          bzip2 -d "$1"   ; OUT="$?" ;;
     zip) echo " ===> Decompress .zip: unzip $1" 
          unzip "$1"     ; OUT="$?" ;;
     rar) echo " ===> Decompress .rar: unrar $1"
          unrar "$1"     ; OUT="$?" ;;
     *) FILENAME="$1" ;;
   esac

   # 2.- Unpacking File
   #------------------------------------------------------------
   if [ "$OUT" -eq "$OK" ]; then
        TAR=${FILENAME##*.}

        if [ -n $TAR ] ; then # ================> There is an extension to check 

            if [ "$TAR" == "tar" ] ; then  # ====> Extension = .tar
                 echo ".............................. UNPACK TAR FILE .............................. "
                 
                 # 2.1.- Tar Base Detection
                 echo " ---> TAR base path detection: tar -tf ""$FILENAME"" | awk 'BEGIN {FS=""/""} {print $1}' | uniq"
                 TAR_BASE=`tar -tf "$FILENAME" | awk 'BEGIN {FS="/"} {print $1}' | uniq` 
                 echo " TAR Base = $TAR_BASE"

                 # 2.2.- Unpacking Tar File
                 echo " --> Unpack .tar: tar-xvf $FILENAME"
                 tar xvf "$FILENAME"

                 # 2.3.- Returning Output path to File
                 local RUTA=`dirname $FILENAME`
                 FILENAME="${RUTA}/${TAR_BASE}"
                 OUT="$?"
            fi 
        fi
   else
         trataErrores -decompress
   fi


   # 3.- Error Treatment
   #------------------------------------------------------------
   echo "................................... RESULTING FILE  ................................... "
   echo " Filename = $FILENAME "
   if [ -e $FILENAME ] && [ "$?" -eq "$OK" ] ; then 
        echo " File / Directory Available     => Unpack OK"
   else
        trataErrores -decompress
   fi

}

#-----------------------------------------------------------------------
#  APPLY PATCHES 
#-----------------------------------------------------------------------
#   Apply all Ubuntu specific patches 
#-----------------------------------------------------------------------
applyPatches() {
     

   #----------------------
   # ACTIONS
   #----------------------
   
     echo  "================================================================================"
     echo  " APPLY PATCHES AND ADJUSTMENTS  "
     echo  "================================================================================"
     echo "cd ""${PROGRAM[0]}"""
     cd "${PROGRAM[0]}"


     # 1.- Adjusting MakeFile 
     #---------------------
     echo " ......................... ADJUSTING MAKEFILE .............................. "
     echo " ========> > Replace CFLAGS to EXTRA_CFLAGS"
     echo "sudo sed -i 's/CFLAGS/EXTRA_CFLAGS/g'  ""${PROGRAM[0]}/Makefile"""
     sudo sed -i 's/CFLAGS/EXTRA_CFLAGS/g'              "${PROGRAM[0]}/Makefile"
     echo "sudo sed -i 's/EXTRA_EXTRA_CFLAGS/EXTRA_CFLAGS/g'  ""${PROGRAM[0]}/Makefile"""
     sudo sed -i 's/EXTRA_EXTRA_CFLAGS/EXTRA_CFLAGS/g'  "${PROGRAM[0]}/Makefile" 
     
     echo 
     echo "  Resulting MakeFile"
     cat ${PROGRAM[0]}/Makefile

     # 2.- Applying Patches 
     #---------------------
     echo " ......................... APPLYING PATCHES .............................. "

     echo "......... sudo patch < ""${PATCH[0]}"""
     sudo patch < "${PATCH[0]}"

     echo "......... sudo patch < ""${PATCH_2[0]}"""
     sudo patch < "${PATCH_2[0]}"
}

#-----------------------------------------------------------------------
#  COMPILE PROGRAM 
#-----------------------------------------------------------------------
#   Compile and install program 
#-----------------------------------------------------------------------
compileProgram() {
     echo  "================================================================================"
     echo  " COMPILE AND INSTALL PROGRAM  "
     echo  "================================================================================"
     echo "cd ""${PROGRAM[0]}"""
     cd "${PROGRAM[0]}"
    
     echo " =======> Installing VPN Client"
     echo "......... sudo ""${PROGRAM[0]}/vpn_install"""
     sudo "${PROGRAM[0]}/vpn_install"

     if [ "$?" -eq "$OK" ] ; then
         echo " =======> Starting Cisco VPN Client"
         echo "......... sudo /etc/init.d/vpnclient_init start"
         sudo /etc/init.d/vpnclient_init start
     else
         trataErrores -installProgram
     fi
}

#-----------------------------------------------------------------------
#  CLEAN ENVIRONMENT 
#-----------------------------------------------------------------------
#   Remove everything used 
#-----------------------------------------------------------------------
cleanEnvironment() {

    echo  "================================================================================"
    echo  " CLEAN ENVIRONMENT  "
    echo  "================================================================================"

    echo "......... rm -R ${PROGRAM[0]}*"
    rm -fR ${PROGRAM[0]}*

    echo "......... rm ${PATCH[0]}*"
    rm -f ${PATCH[0]}*

    echo "......... rm ${PATCH_2[0]}*"
    rm -f ${PATCH_2[0]}*
}


#-----------------------------------------------------------------------
#  INSTALL PROGRAM 
#-----------------------------------------------------------------------
#   "Public" procedure of module 
#-----------------------------------------------------------------------
installProgram() {

     # 1.- Unpack files 
     #-------------------
     unpackPackages "${WORK_DIR}/${PROGRAM[0]}"
     PROGRAM[0]="$FILENAME"
     unpackPackages "${WORK_DIR}/${PATCH[0]}"
     PATCH[0]="$FILENAME"
     unpackPackages "${WORK_DIR}/${PATCH_2[0]}"
     PATCH_2[0]="$FILENAME"

     # 2- Apply Ubuntu Specific modifications
     #-------------------
     applyPatches

     # 3.- Compile Program
     #-------------------
     compileProgram 

     # 4.- Clean Environment
     #-------------------
     cleanEnvironment 
}

################################################################################
# MAIN
################################################################################
cd $WORK_DIR
installDependencies
getPackages
installProgram
exit "$OK"
#------------------------------------------------------------------------------
#                             END INSTALL VPN 
#------------------------------------------------------------------------------
[/PHP]


  Be careful with extra characters added by the forum at the end of the script. You have to supress them

---

### Post by wetling on 2008-09-04
Thelasko, I didn't know about vpnc.  I installed it and it works fine, execpt that I have to type in the concentrator IP, password, my username, and password every time.  That's not ideal.

cesar_spain, that's a great script (and appears to work) but I don't know how to execute the client.  My noobishness is preventing me from seeing where the correct executable file is (I assume it is just ./fileName to run it) so I can enter the VPN config.

---

### Post by cesar_spain on 2008-09-05
Hi:

   VPNC usually works fine, except compressed VPNs. Those only work properly with Cisco Client.

   About how to use, have you tried KVPNC? It is in Ubuntu repos. It manage many different kinds of VPN connections (much more than Network Manager). 

   It is really handy the Network Manager plugins for VPN, and I love the way it works: very simple, very clear icons that shows everything you need to know. But, unfortunately, there is a very small support for VPNs:

   a) Cisco VPNs ==> It works properly if VPN do not use compression. There is no easy way to manage Cisco certificates.

   b) Juniper VPNs ==> A pain in all Linux systems, as far as I know.

   c) Nortel VPNs ==> There is a Novell plugin to manage them, never tried though

    d) Microsoft PPTP ==> Only work with CHAP authentication, PAP is not supported. Very few amount of features to set.

   KVPNC is much better cliente, supports a larger amount of VPNs and a larger amount of options on each one.

    I hope someday the Network Manager include all available VPNs out there, but this day has not come yet.

    I prefer the NM interface to KVPN, it is really simple and handy. If vpnc works for you, stay as you are. If you experience problems, try vpnc command line connection, it will let you know if that Cisco connection is supported or not by the client.

   Hope it helps,

César

PD.: Here a screenshot of KVPNC assistant for VPN connection creation, I selected Cisco propietary, instead of free (vpnc)

[IMG]http://gimnasio.hobby-site.com/images/Pantallazo.jpg[/IMG]

---

### Post by wetling on 2008-09-06
That looks very helpful.  I guess vpnc works for me because I can start if from the terminal and connect to work, but I don't have any GUI interface like that.  

Where do I find that, or how do I add it to my applications menu?

---

### Post by cesar_spain on 2008-09-07
Hi:

   Ok, I thought you were actually working with network manager GUI, which is lovely, although it do not have good VPN support yet.

[B]========================
NETWORK MANAGER VPN GUI
========================
[/B]
    First of all, if VPNC actually works for you, I would use Network Manager GUI. Here the required packages:

1.- _Installation_

[PHP]
sudo aptitude install network-manager-vpnc vpnc 
[/PHP]

2.- _Configuration_

   Here how it looks like:  [ Network Manager VPN Interface]("http://yoten.blogspot.com/2007/10/vpn-easily-via-networkmanager-in-ubuntu.html")
   
    Just Follow the steps of the wizard and you're done.

[B]========================
KVPNC GUI
========================
[/B]
  
 Much better support that Network Manager. Really rich VPN client, but it is actually only a Front-End for all the command line tools, such as vpnc, cisco vpn client, ipsec, pptp, openvpn and so on. It is really cool, but you need those other packages if you want KVPNC to work.

1.- _Installation_:

[PHP]
sudo aptitude install kvpnc vpnc 
[/PHP]
   
2.- _Configuration_:

  Follow the GUI wizard. It usually ask for basic config parameters. Then you can tweak the connection from the config menu. This feature is very very important in PPTP connections, since it is very sensitive to MTU size, usually you have to set it manually to a small value, then everything would be fine.

   It also support profiles, cisco and openvpn, and manage digital certificates. 

   I think they have done a good job with this tool, although still missing things (Nortel and Juniper). Nortel can be achieved through VTUN I think, but not an easy task. They should include in the wizard specific Nortel option.

[B]========================
LINUX VPN INFORMATION 
========================
[/B]

a.- _JUNIPER VPNs_

    If you are lucky, and your VPN provider already include a Juniper Linux VPN Client in their site (not usual, unfotunately), you just need to have Java enabled on your web browser, then go to the VPN web site. Use Firefox, I think other won't work properly.

[PHP]
  sudo aptitude install sun-java6-plugin sun-java6-fonts
[/PHP]

   Juniper Web idea is really cool, since everything is installed and preconfigured from the web site, no need to do anything, just follow the link, Java applet will do it for you. But they should also include the possibility of independent client to work, since in many places they do not include any Linux client on the web and then, what should I do? Nothing, switch to Windows. I tried to do by own with no results at all, if anyone knows the way, please post it here.

a.- _NORTEL VPNs_

   Not an easy task. Here a document describing different VPNs (all of them supported by KVPNC, except Nortel propietary), inside they give some intructions for Nortel.

[http://www.natecarlson.com/linux/linux-vpn.php](http://www.natecarlson.com/linux/linux-vpn.php)

   Here some specifics for ubuntu using VPNC:

[ http://ubuntuforums.org/showthread.php?t=441042&page=8]( http://ubuntuforums.org/showthread.php?t=441042&page=8)

 Network Manager has a plugin, done by Novell, included in SuSE. I don't know it someone ported to Ubuntu and never tried. I guess it won't be a complete solution.

   KVPNC can be configured properly for Nortel, but not easily.

   Hope that helps,

César
    


    César

---

### Post by rugbert on 2008-09-20
> **cesar_spain said:**
> Dear all:

    I have just written a script for installing Cisco VPN Client on Ubuntu 8.04. I tested it on two different machines, and it works. 

    Give it a try. When asking you things, just press enter.


How exactly do I run this? save it as a .sh file and type this:
sudo ./cisco.sh

This cisco VPN stuff is a real headache. I downgraded from 64 bit Ubuntu to 32bit JUST because I was under the assumption the cisco vpn actually worked.

If I have the PCF files and the group key to connect to the VPN at work, can I use openVPN or VPNc?

---

### Post by wetling on 2008-09-21
I don't remember how I did it, other than that I saved the file and Googled, "make file exectuable linux" or something like that.  The directions I followed had me use the terminal to change the attributes of the file.

---

### Post by rugbert on 2008-09-21
oh cool yea, didnt check the file attributes!

so this only works with kvpnc and not the gnome network manager plugin?

---

### Post by jack frost on 2008-09-27
I got it to install the script; it connects and stays connected for about 10 sec.. then disconnects.. then it ask for my password again.. we use cisco client at my work with token generated password.. I am trying to not have to use windows to connect.

---

### Post by cesar_spain on 2008-09-28
> **jack frost said:**
> I got it to install the script; it connects and stays connected for about 10 sec.. then disconnects.. then it ask for my password again.. we use cisco client at my work with token generated password.. I am trying to not have to use windows to connect.

  Try KVPNC, you can configure it to reconnect automatically every time link is down. Give it a try.

  Forget about network manager if there are tokens and things like that. You're best bet is kvpnc.

   Good luck.

César

PD: Did you manage to install the Cisco Client? KVPNC is just a front end for it.

---

### Post by cesar_spain on 2008-09-28
> **rugbert said:**
> How exactly do I run this? save it as a .sh file and type this:
sudo ./cisco.sh

This cisco VPN stuff is a real headache. I downgraded from 64 bit Ubuntu to 32bit JUST because I was under the assumption the cisco vpn actually worked.

If I have the PCF files and the group key to connect to the VPN at work, can I use openVPN or VPNc?
 

================
SCRIPT EXECUTION
================

   For executing this script:

     a) Copy / paste the text into a text file 
           gedit cisco.sh

     b) Give it execution permissions: 
           chmod +x cisco.sh 
 
     c) Run it: 
           sudo cisco.sh

    It should work. 

================
INSTALLING KVPNC
================
 
   sudo aptitude install kvpnc

  If you have a Cisco Profile file, you can just load it directly into kvpn, it should work properly. Otherwise, you need to dive into Cisco VPN options.

   The cisco text client usually save profiles into a text file, somewhere in /etc folder. You can also place the profile file there and call it using the name.

    Good luck,

César

---

### Post by rmontyq on 2009-03-30
cesar_spain:

Just a quick note to thank you for your work. I have spent HOURS on different distributions of Ubuntu at different times with varying degrees of failure before I succeeded. Your script did it first time out of the box.

Good work!

---

### Post by jmcvetta on 2009-04-02
Using these instructions I was able to get the Cisco VPN client running on Intrepid with the 2.6.27 kernel:
```
$ uname  -a
Linux keynes 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

```

---

### Post by dcstar on 2009-04-04
> **jmcvetta said:**
> Using these instructions I was able to get the Cisco VPN client running on Intrepid with the 2.6.27 kernel:
```
$ uname  -a
Linux keynes 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

```

And I simply use the **vpnc** and **kvpnc** packages in the repositories and I can import a .pcf file and use it immediately - no mucking around with command line scripts.

---

### Post by Bateluer on 2009-04-24
Sorry to dig this up, but has anyone tried using the Cisco VPN Client under Jaunty.

---

### Post by Matyy on 2009-04-29
Yeah, I can't get it working in Jaunty neither x.x

---

### Post by rosv on 2009-05-04
Thanx. It works very well on ubuntu 8.04. Great script

---

### Post by cesar_spain on 2009-06-02
> **Matyy said:**
> Yeah, I can't get it working in Jaunty neither x.x

  I guess depending on the Ubuntu version, you need to use different patches. 

  I think patches are designed for especific Linux kernel version (for example, 2.6 and above). So, if you want to use the script in different versions, you need to know which things are required and where to download.
  
  Once located this info, change the arrays (patches, vpn client, etc.)

   Anyway, you can add some lines to the code, for adapting to differrent versions:

KERNEL_VERSION=`uname -a` # Don't remember exact command

case ${KERNEL_VERSION} in
  "2.2")  PATCH_1=( ...)
          PATCH_2=( ... ) 
         ;;
esac

   This ways you can use the very same script for different versions. I haven't deal with it.

    Anyway, someone should add this package to the repositories sometime. I am not sure if there is some propietary issues here, and this package can't be included.

     Thanks for the positive feedback,

César

---

### Post by cesar_spain on 2009-06-17
Here te information related to Cisco VPN Client:

[http://projects.tuxx-home.at/?id=cisco_vpn_client](http://projects.tuxx-home.at/?id=cisco_vpn_client)

  JAUNTY: May be you have to replace the source code for the one proposed there . It seems to be that it is the same patches, so, only change the source code and where to get it.

  César

---

