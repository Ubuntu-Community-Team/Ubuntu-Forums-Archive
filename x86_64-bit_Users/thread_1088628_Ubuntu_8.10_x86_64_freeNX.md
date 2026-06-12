---
title: "Ubuntu 8.10 x86_64 freeNX"
date: 2009-03-06
forum: x86 64-bit Users
---

### Post by psunix on 2009-03-06
Hi

I'm trying to setup freenx on my Ubuntu Server 8.10 64-bit.
But when I try to connect I get the following error message:

freenx-client
> NX> 148 Server capacity: not reached for user: sysadmin
NX> 105 Start session with: --virtualdesktop="1" --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="bla" --type="unix-default" --geometry="1024x768" --client="winnt" --keyboard="pc102\057ch" --screeninfo="1024x768x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: DA79B76C. To get detailed information about
NX> 595 ERROR: the error search for the string DA79B76C in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15


/var/log/messages
> Mar  6 14:18:08 srv02 NXSERVER-3.3.0-14[30108]: ERROR: (exception id DA79B76C) NX> 596 init: stdin arguments: user=sysadmin,userip=192%2e168%2e10%2e113,uniqueid=7AF3B3246D1D7895D04D8A6E7F7B4558,display=1023,node_number=0,server_name=srv02,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e11%2e11,encryption_mode=3,connection=local,images=64M,cache=16M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,shpix=1,rootless=0,composite=1,session=bla,shmem=1,type=unix%2ddefault,virtualdesktop=1,screeninfo=1024x768x32%2brender,keyboard=pc102%2fch,geometry=1024x768,link=adsl
Mar  6 14:18:08 srv02 NXSERVER-3.3.0-14[30108]: ERROR: (exception id DA79B76C) NXNodeExec::exec('startsession', 'user=sysadmin&userip=192%2e168%2e10%2e113&uniqueid=7AF3B3246D1D7...', 'localhost', 22) called at handlers/nxserver.pl line 3532
Mar  6 14:18:08 srv02 NXSERVER-3.3.0-14[30108]: ERROR: (exception id DA79B76C) NXShell::handler_session_start('--virtualdesktop="1" --link="adsl" --backingstore="1" --encrypti...') called at NXShell.pm line 373
Mar  6 14:18:08 srv02 NXSERVER-3.3.0-14[30108]: ERROR: (exception id DA79B76C) NXShell::handle_command('startsession', '--virtualdesktop="1" --link="adsl" --backingstore="1" --encrypti...') called at NXShell.pm line 145
Mar  6 14:18:08 srv02 NXSERVER-3.3.0-14[30108]: ERROR: (exception id DA79B76C) NXShell::run() called at nxserver.pl line 4467
Mar  6 14:18:08 srv02 NXSERVER-3.3.0-14[30108]: ERROR: (exception id DA79B76C) eval {...} called at nxserver.pl line 4426

I also checked the user:
> /usr/NX/bin/nxserver --usercheck sysadmin
NX> 900 Verifying public key authentication for NX user: sysadmin.
NX> 900 Public key authentication succeeded.
NX> 999 Bye.

This is how I installed freenx.

1. Downloaded *.deb-Packages from nochmachine.org
2. I installed these packages in this order

> sudo dpkg -i nxclient_3.3.0-6_x86_64.deb
sudo dpkg -i nxnode_3.3.0-12_x86_64.deb
sudo dpkg -i nxserver_3.3.0-14_x86_64.deb

3. Then I added 
> AuthorizedKeysFile      %h/.ssh/authorized_keys2
to /etc/ssh/sshd_config
and restated the ssh server.

4. After this I added the user I need to connect.
> /usr/NX/bin/nxserver --useradd sysadmin

Thanks for any help

psunix

---

