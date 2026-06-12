---
title: "HOW TO: Installing Ubuntu 8.04 (Hardy Heron) on external hard drive"
date: 2008-06-08
forum: x86 64-bit Users
---

### Post by shailendra on 2008-06-08
Hi,

I am writing this "HOW TO" to help those who want to install Ubuntu 8.04 (or any Linux) on an external hard drive and keep windows on the internal hard drive of their PC.

I followed the steps given below to make it work.

REQUIREMENTS:
1. BIOS support for booting from USB or external devices.
2. USB external hard drive (Rotating Platter NOT a Flash Drive).
3. Ubuntu 8.04 live cd

IMPORTANT: Take backup of all your important data from the Internal and External hard drives. 

PROCEDURE:
1. Create the desired partition on your external hard drive using windows utility. This step if required if you do not want to use entire memory for Ubuntu/Linux. Else you can skip this step.
In my case I created two partitions on my USB hard drive. First partition was of 20 GB (For Ubuntu) and second partion was of 300 GB (for windows and Ubuntu).

Note: Ubuntu uses ext3 file system. So, the partition for Ubuntu will not be visible from Windows.

2. Insert the Ubuntu live CD.

3. Restart the PC and press the function key to go to the BIOS setup. 

In my case it was F12.

4. Boot from the Ubuntu live CD.

5. Select the install option.

6. Follow the installation process until the "Prepare disk space" window comes.

7. Select "Manual" option on this window. If you want to use entire USB hard drive then you can select the "Guided-use entire disk" option.

8. Select the partition you have created for Ubuntu. You can easily recognize it by looking at the size of each partitions.  It will be either "sda" or "sdb".

In my case it was "sdb1" and its size was 20 GB.

9. Click on the "Advance" button and specify the partition on the external hard drive to install the GRUB on the MBR of the external hard drive. Make sure that you do not select the internal hard drive. Otherwise Uduntu will update the MBR of the internal hard drive and your PC will not boot unless the external hard drive is connected.

10. When the installation has finished, restart your PC and remove the Ubuntu live CD.

11. Boot into your system BIOS or Boot Menu and select to boot from your USB Hard drive.

12. You will most probably get the "Error 17: Can not mount the device".

13. Return to the boot menu of Ubuntu and press "E" button to edit the command line. 

14. Change the "root(hdX,Y)" command and try to boot Ubuntu. Change the value of "X" and "Y". Start with "0". Note down the command which worked for you.

In my case the original command was "root(hd0,1)", which gave me Error 17. But the command "root(hd0,0)" worked for me.

15. Now you have to update the "menu.lst" file to make this change permanent, otherwise you will have to change it every  time you boot.

16. First take backup of the "menu.lst" file. On the terminal type the command;
"sudo cp /boot/grub/menu.lst /boot/grub/menu_copy.lst"

17. Now update the "menu.lst" file. On the terminal type the command;
"gksudo gedit /boot/grub/menu.lst

The menu.list file will be opened. 

18. Go to the section for "Ubuntu" and update the root command which worked for you and save the file.

In my case, I had to replace "root(hd0,1)" with "root(hd0,0)" at three places in the menu.lst file.

Note: Make sure that you do not update any other section.

19. Restart your PC and boot from USB external device.
You should now be able to run ubuntu.

20. To run windows simply turn on the PC. It will automatically start windows.

You can try running Windows by disconnecting the USB hard drive.


I had struggled a lot to make my system work for Windows (on my internal hard drive) and Ubuntu (external hard drive). So, I hope that above procedure will be helpful to you and will prevent you from struggling.

---

