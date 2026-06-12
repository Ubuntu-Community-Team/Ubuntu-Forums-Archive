---
title: "Vmware server PAM issues"
date: 2007-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by chefdog on 2007-08-03
Allright,

Got Vmware server up and running on 64bit Ubuntu Feisty Linux, creating new vmware guest's does work, copying and open existing vmware guests; also no problem.
Now I want vmware guest (Windows HomeServer) to install on a raw partition, so accessing the harddrive natively (no virtual disks). 

My system; AMD64 X2 3800 EESFF, 4GB ram, 2 WD raptors in raid for OS, 1TB HD space for vmware guest OS, mobo is a Nvidia 630a with geforce 7025 onboard. 

I do have the dedicated drive (1TB) next to my OS drives, I can setup the guest, but when I run the guest for installing HomeServer I get errors (from the /var/log/auth.log):

Aug  3 20:22:04 chefdog-homeserver vmware-authd[4680]: PAM (other) illegal module type: @include
Aug  3 20:22:04 chefdog-homeserver vmware-authd[4680]: PAM pam_parse: expecting return value; [...common-session]
Aug  3 20:22:04 chefdog-homeserver vmware-authd[4680]: PAM (other) no module name supplied
Aug  3 20:22:04 chefdog-homeserver vmware-authd[4680]: login from 192.168.1.100 as marco 
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) illegal module type: @include
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM pam_parse: expecting return value; [...common-auth]
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) no module name supplied
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM unable to dlopen(<*unknown module path*>)
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM [error: <*unknown module path*>: cannot open shared object file: No such file or directory]
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM adding faulty module: <*unknown module path*>
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) illegal module type: @include
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM pam_parse: expecting return value; [...common-account]
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) no module name supplied
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) illegal module type: @include
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM pam_parse: expecting return value; [...common-password]
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) no module name supplied
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) illegal module type: @include
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM pam_parse: expecting return value; [...common-session]
Aug  3 20:22:38 chefdog-homeserver vmware-authd[4703]: PAM (other) no module name supplied

---

### Post by chefdog on 2007-08-04
Oww I found the right thread about this issue; [http://ubuntuforums.org/showthread.php?t=426026&highlight=vmware+deb+package&page=2](http://ubuntuforums.org/showthread.php?t=426026&highlight=vmware+deb+package&page=2)

---

### Post by tobler on 2008-01-03
Hello

I just installed vmware-server package to my home server. It has 64bit Feisty.
I am using workstation computer to access server and with SSH I was able to run vmware-console on my screen: ssh -Xf server.name vmware

Then I was going to get remote-console. First I noticed that xinetd didn't restart to activate vmware-authd.
Next problem was about PAM. Browsing trough google searches didn't help until I noticed that my vmware installation was also installing some 32bit libraries. So ldd /usr/sbin/vmware-authd told that it's 32bit program!
So PAM is trying to use 32bit auth modules!

Does anybody have better solution to have remote vmware console working on 64bit host? (Install 32bit PAM modules? Maybe not.)

---

### Post by siouzi on 2008-02-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/112937](https://bugs.launchpad.net/ubuntu/+bug/112937) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Bump

Just struggled with this one myself. The bug and the solution can be found at launchpad.

```

sudo <your favorite editor> /etc/pam.d/vmware-authd

# the file should contain only the lines below:
auth sufficient /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix.so shadow nullok
auth required /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix_auth.so shadow nullok
account sufficient /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix.so
account required /usr/lib/vmware-server/lib/libpam.so.0/security/pam_unix_acct.so

#%PAM-1.0
@include common-auth
@include common-account

```

I don't think a restart is needed... Remote console works after this change.

---

