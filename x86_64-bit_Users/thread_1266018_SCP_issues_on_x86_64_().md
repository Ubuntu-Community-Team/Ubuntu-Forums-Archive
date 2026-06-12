---
title: "SCP issues on x86_64 (?)"
date: 2009-09-14
forum: x86 64-bit Users
---

### Post by bogd on 2009-09-14
After a recent update, I'm having problems copying files via scp from some machines to others (for exact error message, see below). 

All of the machines are running Ubuntu 9.04 (jaunty). After some troubleshooting, it looks like the machines are running two different versions of scp (let's call them version A and B). 

[ Version A ]
[FONT=Courier New]bogd@st:~$ scp -V
scp: illegal option -- V
usage: scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 ... [[user@]host2:]file2
bogd@st:~$ which scp
/usr/bin/scp[/FONT]

[FONT=Courier New][ Version B ]
[/FONT][FONT=Courier New]bogd@sb:~$ scp -V
scp:  OpenSSH_5.1p1 Debian-5ubuntu1  on i686-pc-linux-gnu
bogd@sb:~$ which scp
/usr/local/bin/scp
bogd@sb:~$ ls -l /usr/local/bin/scp
lrwxrwxrwx 1 root root 4 2009-09-05 03:10 /usr/local/bin/scp -> scp2
[/FONT]

SCP works just fine between machines running the same version (A to A, or B to B). However, when copying between different versions, copying fails. All machines are running Ubuntu 9.04, upgraded with the latest packages.
An apt-get install --reinstall on st only reinstalls the /usr/bin/scp file.

[FONT=Courier New]bogd@st:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

bogd@sb:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"[/FONT]

So far, the only difference I can find between the two machines is that the first one (st) is running the 64-bit version, and the other one is a 32-bit system. However, I have no idea whether this is related to the problem or not.

For a complete log of an scp transaction, see below:

[FONT=Courier New]bogd@st:~$ scp -v test bogd@sb:/home/bogd
Executing: program /usr/bin/ssh host sb, user bogd, command scp -v -t /home/bogd
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to sb [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/bogd/.ssh/identity type -1
debug1: identity file /home/bogd/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/bogd/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'sb' is known and matches the RSA host key.
debug1: Found key in /home/bogd/.ssh/known_hosts:15
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/bogd/.ssh/identity
debug1: Offering public key: /home/bogd/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/bogd/.ssh/id_dsa
debug1: Next authentication method: password
bogd@sb's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending command: scp -v -t /home/bogd
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype [EMAIL="eow@openssh.com"]eow@openssh.com[/EMAIL] reply 0
scp: warning: Executing scp1 compatibility.
scp: FATAL: Executing ssh1 in compatibility mode failed (Check that scp1 is in your PATH).
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
Transferred: sent 1872, received 2216 bytes, in 0.1 seconds
Bytes per second: sent 29915.7, received 35413.0
debug1: Exit status 255
lost connection
[/FONT]



And if I try to copy the other way around, it just hangs:

[FONT=Courier New]bogd@sb:~$ scp -v test bogd@st:/home/bogd
scp:SshAppCommon/sshappcommon.c:154/ssh_app_get_global_regex_context: Allocating global SshRegex context.
scp:Scp2/scp2.c:505/glob_ready_cb: Received error "SSH_FC_OK"., msg: Globbing successful.
scp:Scp2/scp2.c:569/scp_glob: Starting transfer...
scp:/home/bogd/test
scp:SshFCTransfer/sshfc_transfer.c:2876/ssh_file_copy_transfer_files: File list has 2 files.
scp:SshFCTransfer/sshfc_transfer.c:2425/transfer_conn_error: Not yet connected, or connection down, waiting...
scp:SshFileCopy/sshfilecopy.c:911/ssh_file_copy_connect: Making local connection.
scp:SshFCTransfer/sshfc_transfer.c:126/transfer_set_next_source: Source file is "raw", and it needs to be parsed.
scp:SshFCTransfer/sshfc_transfer.c:1276/transfer_parse_stat_cb: No connection yet. Waiting...
scp:SshFCTransfer/sshfc_transfer.c:263/transfer_set_next_source: Next source file is /home/bogd/test .
scp:SshFCTransfer/sshfc_transfer.c:2425/transfer_conn_error: Not yet connected, or connection down, waiting...
scp:SshFileCopy/sshfilecopy.c:933/ssh_file_copy_connect: Connecting to remote host. (host = st, user = bogd, port = NULL)
scp:Scp2/scp2.c:1644/connect_callback: argv[0] = /usr/local/bin/ssh2
scp:Scp2/scp2.c:1644/connect_callback: argv[1] = -l
scp:Scp2/scp2.c:1644/connect_callback: argv[2] = bogd
scp:Scp2/scp2.c:1644/connect_callback: argv[3] = -v
scp:Scp2/scp2.c:1644/connect_callback: argv[4] = -x
scp:Scp2/scp2.c:1644/connect_callback: argv[5] = -a
scp:Scp2/scp2.c:1644/connect_callback: argv[6] = -o
scp:Scp2/scp2.c:1644/connect_callback: argv[7] = clearallforwardings yes
scp:Scp2/scp2.c:1644/connect_callback: argv[8] = -o
scp:Scp2/scp2.c:1644/connect_callback: argv[9] = passwordprompt %U@%H's password:
scp:Scp2/scp2.c:1644/connect_callback: argv[10] = -o
scp:Scp2/scp2.c:1644/connect_callback: argv[11] = nodelay yes
scp:Scp2/scp2.c:1644/connect_callback: argv[12] = -o
scp:Scp2/scp2.c:1644/connect_callback: argv[13] = authenticationnotify yes
scp:Scp2/scp2.c:1644/connect_callback: argv[14] = st
scp:Scp2/scp2.c:1644/connect_callback: argv[15] = -s
scp:Scp2/scp2.c:1644/connect_callback: argv[16] = sftp
debug: Connecting to st, port 22...
debug: Ssh2/ssh2.c:1956/main: Entering event loop.
debug: Ssh2Client/sshclient.c:1328/ssh_client_wrap: Creating transport protocol.
debug: SshAuthMethodClient/sshauthmethodc.c:137/ssh_client_authentication_initialize: Added "publickey" to usable methods.
debug: SshAuthMethodClient/sshauthmethodc.c:137/ssh_client_authentication_initialize: Added "password" to usable methods.
debug: Ssh2Client/sshclient.c:1360/ssh_client_wrap: Creating userauth protocol.
debug: client supports 2 auth methods: 'publickey,password'
debug: Ssh2Common/sshcommon.c:496/ssh_common_wrap: local ip = xx.xx.xx.xx, local port = 53260
debug: Ssh2Common/sshcommon.c:498/ssh_common_wrap: remote ip = xx.xx.xx.xx, remote port = 22
debug: SshConnection/sshconn.c:1889/ssh_conn_wrap: Wrapping...
debug: Ssh2/ssh2.c:867/connect_done_finalize: Opening /dev/tty for queries.
warning: Need basic cursor movement capability, using vt100
debug: Remote version: SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug: Ssh2Transport/trcommon.c:1373/ssh_tr_input_version: Remote version has rekey incompatibility bug.
debug: Ssh2Transport/trcommon.c:1376/ssh_tr_input_version: Remote version is OpenSSH, KEX guesses disabled.
debug: Ssh2Transport/trcommon.c:1717/ssh_tr_negotiate: lang s to c: `', lang c to s: `'
debug: Ssh2Transport/trcommon.c:1783/ssh_tr_negotiate: c_to_s: cipher aes128-cbc, mac hmac-sha1, compression none
debug: Ssh2Transport/trcommon.c:1786/ssh_tr_negotiate: s_to_c: cipher aes128-cbc, mac hmac-sha1, compression none
debug: Remote host key found from database.
debug: Ssh2Common/sshcommon.c:291/ssh_common_special: Received SSH_CROSS_STARTUP packet from connection protocol.
debug: Ssh2Common/sshcommon.c:341/ssh_common_special: Received SSH_CROSS_ALGORITHMS packet from connection protocol.
debug: server offers auth methods 'publickey,password'.
debug: SshConfig/sshconfig.c:2184/ssh2_parse_config: Unable to open /home/bogd/.ssh2/identification
debug: Ssh2AuthClient/sshauthc.c:316/ssh_authc_completion_proc: Method 'publickey' disabled.
debug: server offers auth methods 'publickey,password'.
debug: Ssh2AuthPasswdClient/authc-passwd.c:98/ssh_client_auth_passwd: Starting password query...
bogd@st's password:
debug: Ssh2Common/sshcommon.c:259/ssh_common_special: Received SSH_CROSS_AUTHENTICATED packet from connection protocol.
debug: Ssh2/ssh2.c:637/client_authentication_notify: Returning user input stream to original values.
scp:SshFCTransfer/sshfc_transfer.c:1542/transfer_stat_before_rm_cb: No connection yet. Waiting...
debug: Ssh2Common/sshcommon.c:718/ssh_common_new_channel: num_channels now 1
debug: SshTtyFlags/sshttyflags.c:339/ssh_internal_encode_tty_flags: Not a tty. (fd = 0)
scp:SshFileXferClient/sshfilexferc.c:981/ssh_file_client_receive_proc: ssh_file_client_receive_proc: bad VERSION
scp:SshFCTransfer/sshfc_transfer.c:1542/transfer_stat_before_rm_cb: No connection yet. Waiting...
scp:SshFCTransfer/sshfc_transfer.c:1542/transfer_stat_before_rm_cb: No connection yet. Waiting...
scp:SshFCTransfer/sshfc_transfer.c:1542/transfer_stat_before_rm_cb: No connection yet. Waiting...
scp:SshFCTransfer/sshfc_transfer.c:1542/transfer_stat_before_rm_cb: No connection yet. Waiting...
scp:SshFCTransfer/sshfc_transfer.c:1542/transfer_stat_before_rm_cb: No connection yet. Waiting...
scp:SshFCTransfer/sshfc_transfer.c:1542/transfer_stat_before_rm_cb: No connection yet. Waiting...
scp:SshFCTransfer/sshfc_transfer.c:1542/transfer_stat_before_rm_cb: No connection yet. Waiting...
scp:SshFCTransfer/sshfc_transfer.c:1542/transfer_stat_before_rm_cb: No connection yet. Waiting...
scp:SshFCTransfer/sshfc_transfer.c:1542/transfer_stat_before_rm_cb: No connection yet. Waiting...

[/FONT]

---

### Post by toupeiro on 2009-09-24
A few things to check.

Verify which sshd protocol version is being used in /etc/ssh/sshd_config.  

try blowing away your known_host keys on both machines for the machines in question.

Try an scp to the local ip address on both machines. (note, not the loopback/localhost address, but the actual IP.)  this will check make sure your ssh_config is compatible with your local sshd_config.  If you find one machine works, and one machine doesn't.  examine the ssh_config and sshd_config for any differences between the two machines.

---

