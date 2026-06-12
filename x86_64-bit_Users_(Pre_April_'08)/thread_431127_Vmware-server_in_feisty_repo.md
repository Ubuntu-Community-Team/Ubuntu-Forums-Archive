---
title: "Vmware-server in feisty repo"
date: 2007-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mongoose on 2007-05-02
Anyone else tried the new package out?  I had to copy the kernel modules to the kernel I actually use, but other than that pretty smooth install.

---

### Post by FerGeCo on 2007-05-03
I just installed it from the repo's .. no bugs so far

---

### Post by srt4play on 2007-05-03
I don't see a new vmware-server package?

---

### Post by Ledah on 2007-05-03
> **srt4play said:**
> I don't see a new vmware-server package?

They are in the canonical commercial repository.

---

### Post by srt4play on 2007-05-03
Hey Ledah, thank you.

---

### Post by killernurd on 2007-05-03
> **Ledah said:**
> They are in the canonical commercial repository.

Oops! I'd been looking in the wrong place :)

Thanks!

---

### Post by linescanner on 2007-05-04
Just got it installed after hours of trying to do it manually :) 

However, how do I reconfigure the networking.  It just auto answers all the set up stuff.

Ta

---

### Post by linescanner on 2007-05-04
der!!

found it.

Blond moment
 :)

---

### Post by jespdj on 2007-05-05
Helpful info: [How to install Vmware server From Canonical commercial repository in Ubuntu Feisty](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

---

### Post by fago on 2007-05-05
hm, I can't get it working because I have no eth0 on my laptop.

The default configuration fails (tries to use eth0) and dpkg exits with errors. I tried to manually configure it using  vmware-config-network.pl - that worked but when I tried to finish package installation it used the default config again and so it broke again :/

edit: anyone knows where to submit bug reports for this?

---

### Post by hiazle on 2007-05-29
Hi Good people, I hope this is not considered dead already. I tried installing Vmware Server 1.0.3 from vmware website. However, the install failed when it tried to build modules. I can't remember which module it failed to build, but my question is: is there a way to remove the partial install so I can install from the repos?

---

### Post by fakie_flip on 2007-06-01
> **jespdj said:**
> Helpful info: [How to install Vmware server From Canonical commercial repository in Ubuntu Feisty](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

What else is available in that repository?

---

### Post by jharrop on 2007-06-16
A data point installing VMWare Server 1.0.2 on Ubuntu Feisty,  2.6.20-15-generic x86_64

The method mentioned in this thread, further descirbed at:
          [http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

failed but the following which i'll call Method 2 worked fine: 

         [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

(after cleaning up all traces of Method 1).

This is what happened when I tried the first method:

When I ran

          apt-get install vmware-server vmware-tools-kernel-modules

the install finished with:

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

The VMWare server console started ok, but when I tried to start a VM, it failed with the following message:

Unable to change virtual machine power state: The process exited with an error:
vmxvmdb: Index name being generated from config file
POST(no connection): Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

POST(no connection): Failed to initialize monitor device.

Failed to initialize VM.
End of error message.

I did try vmware-any-any-update110, but sudo ./runme.pl said:

      Updating /usr/bin/vmware-config.pl ... corrupted

In fact that file did not exist.

At that point I gave up on Method 1.  As i say, Method 2 worked fine for me.

---

### Post by brharri1 on 2007-06-16
Rather than starting a new thread, I will ask my question here. When I first installed feisty, vmware-server worked fine, until one day my virtual machine would not load (unfortunately I can't remember what the error message was), so I tried re-installing vmware. Now whenever I try to install it, this is the output I get:

> brian@brian-desktop64:~$ sudo apt-get install vmware-server vmware-tools-kernel-modules
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ia32-libs-gtkglext1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  vmware-server vmware-tools-kernel-modules
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/79.5MB of archives.
After unpacking 131MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 210288 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.3-1_amd64.deb) ...
Selecting previously deselected package vmware-tools-kernel-modules.
Unpacking vmware-tools-kernel-modules (from .../vmware-tools-kernel-modules_2.6.20.16.28.1_amd64.deb) ...
Setting up vmware-server (1.0.3-1) ...
Unknown media type in type 'chemical/x-alchemy'

Unknown media type in type 'chemical/x-cache'

Unknown media type in type 'chemical/x-cdx'

Unknown media type in type 'chemical/x-chem3d'

Unknown media type in type 'chemical/x-cif'

Unknown media type in type 'chemical/x-cml'

Unknown media type in type 'chemical/x-daylight-smiles'

Unknown media type in type 'chemical/x-dmol'

Unknown media type in type 'chemical/x-gamess-input'

Unknown media type in type 'chemical/x-gaussian-input'

Unknown media type in type 'chemical/x-gaussian-log'

Unknown media type in type 'chemical/x-genbank'

Unknown media type in type 'chemical/x-hin'

Unknown media type in type 'chemical/x-inchi'

Unknown media type in type 'chemical/x-inchi-xml'

Unknown media type in type 'chemical/x-jcamp-dx'

Unknown media type in type 'chemical/x-macromodel-input'

Unknown media type in type 'chemical/x-mdl-molfile'

Unknown media type in type 'chemical/x-mdl-rdfile'

Unknown media type in type 'chemical/x-mdl-rxnfile'

Unknown media type in type 'chemical/x-mdl-sdfile'

Unknown media type in type 'chemical/x-mdl-tgf'

Unknown media type in type 'chemical/x-mmcif'

Unknown media type in type 'chemical/x-mol2'

Unknown media type in type 'chemical/x-mopac-graph'

Unknown media type in type 'chemical/x-mopac-input'

Unknown media type in type 'chemical/x-mopac-out'

Unknown media type in type 'chemical/x-msi-car'

Unknown media type in type 'chemical/x-msi-hessian'

Unknown media type in type 'chemical/x-msi-mdf'

Unknown media type in type 'chemical/x-msi-msi'

Unknown media type in type 'chemical/x-pdb'

Unknown media type in type 'chemical/x-shelx'

Unknown media type in type 'chemical/x-vmd'

Unknown media type in type 'chemical/x-xyz'


Setting up vmware-tools-kernel-modules (2.6.20.16.28.1) ...
brian@brian-desktop64:~$ vmware-server
bash: vmware-server: command not found
brian@brian-desktop64:~$                        

I have no clue what is causing those errors, and I cannot load vmware. I originally thought that maybe it was a kernel update that had messed up my vmware installation, but when I go back to the old kernel there is no difference. 

Any help is much appreciated. It's nice to be able to say at this point that ubuntu works so well for me that not having access to windows isn't the big deal it used to be. But, it would be nice to have the option.

-Brian

---

### Post by diggity on 2007-06-16
Apparently, there is not an automatic update for the vmware-server-kernel-modules.
The kernel update will mess up the vmware install. You don't have to uninstall anything, but you need to install the **vmware-server-kernel-modules-<*new kernel version #***>

In my case, I had to install **vmware-server-kernel-modules-2.6.20-16** to match my kernel version. If you don't know what your current kernel version is type **uname -r** into a terminal.

Reboot (to load the new kernel module) and you should be able to load your virtual machine.

---

### Post by brharri1 on 2007-06-16
My kernel modules were the newest version (I just tried it again). At this point I cannot even install vmware-server, much less try and load a virtual machine.

Thanks,

Brian

---

### Post by brharri1 on 2007-06-16
Well, I got it working via the instructions from [http://www.unix-tutorials.com/go.php?id=915]("http://www.unix-tutorials.com/go.php?id=915") (basically, just compiling it myself). Would be nice to have it from the deb, but I can't think of much reason to be updating it much anyway.

---

