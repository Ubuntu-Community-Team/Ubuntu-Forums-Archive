---
title: "64 Bit Software conflicts with Java and Flashplayer"
date: 2007-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dennis Shipman on 2007-08-04
I. To install the Linux self-extracting x64 file

Follow these instructions:

1. At the terminal: Type:
su
2. Enter the root password.
3. Change to the directory in which you want to install. Type:
cd
For example, to install the software in the /usr/java/ directory, Type:
cd /usr/java

Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
4. Change the permission of the file you downloaded to be executable. Type:
chmod a+x jre-1_5_0_02-linux-amd64.bin
5. Verify that you have permission to execute the file. Type:
ls -l



Change permission on the installation file

6. Start the installation process. Type:
./jre-1_5_0_02-linux-amd64.bin
Note: If the file is in the current directory, prepend it with "./"

This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.



type YES to agree to the license agreement

7. The JRE is installed into its own directory. In this example, it is installed in the /usr/java/jre1.5.0_02 directory. When the installation has completed, you will see the word Done.



Installation completes

8. The JRE is installed in jre1.5.0_(version number) sub-directory under the current directory. In this case, the JRE is installed in the /usr/java directory. Verify that the jre1.5.0_02 sub-directory is listed under the current directory. Type:
ls



Verify the installation

9. Delete the bin installation file if you want to save disk space.
10. Exit the root shell.

I need to modify the commands so this installation will work with Ubuntu 7.04 64 Bit AMD. Does anyone know how?

~$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

__________________
Edit/Delete Message

---

