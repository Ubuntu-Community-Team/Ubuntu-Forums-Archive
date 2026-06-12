---
title: "32bit openssl"
date: 2009-01-16
forum: x86 64-bit Users
---

### Post by n9ljx on 2009-01-16
I just installed 8.10 64bit.  One of the apps I am trying to run fails when doing a ssl transaction.  The author thinks it is because it needs the 32 bit ssl library (he does not have 64 bit so he cannot test).  Problem is **I cannot find the 32bit openssl library**.  Any suggestions?

Thanks,
--scott

---

### Post by Cappy on 2009-01-16
Install getlibs from the top of: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and use
```
getlibs -p libssl0.9.8
```

If that fails, then more information will be needed such as the error from the program when running it from console or the name of the program.

---

### Post by louis_carole on 2009-10-01
Dear All,

I am also having difficulty finding the 32-bit ssl lib.  The exact instructions and error I receive (on jaunty 64-bit) are:

```
$ ./configure --prefix=$DIR/globus

checking for javac... /usr/bin/javac
configure: WARNING: the javac in your path is not from your $JAVA_HOME environment
checking for ant... /usr/bin/ant
configure: creating ./config.status
config.status: creating Makefile

$ make gsi-myproxy gsi-openssh

tar -C $DIR/globus -xzf binary-trees/globus_libtool-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_common-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_openssl-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_gsi_openssl_error-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_gsi_proxy_ssl-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_openssl_module-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_gsi_sysconfig-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_gsi_cert_utils-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_callout-*/*.tar.gz
tar -C $DIRglobus -xzf binary-trees/globus_gsi_callback-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_gsi_credential-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_gsi_proxy_core-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_gssapi_gsi-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_gss_assist-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/gssapi_error-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_user_env-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_simple_ca_setup-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_proxy_utils-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_openssl_setup-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_common_setup-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/globus_simple_ca-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/myproxy-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/gsi_openssh-*/*.tar.gz
tar -C $DIR/globus -xzf binary-trees/gsi_openssh_setup-*/*.tar.gz

$ sudo make install

ln -sf $DIR/globus/etc/gpt/packages $DIR/globus/etc/globus_packages
$DIR/globus/sbin/gpt-postinstall
running $DIR/globus/setup/gsi_openssh_setup/setup-openssh..[ Changing to $DIR/globus/setup/gsi_openssh_setup ]
Configuring gsi_openssh
------------------------------------------------------------
Executing...
ERROR: Unable to execute $DIR/globus/bin/ssh.d/ssh-keygen -t rsa1 -f $DIR/globus/etc/ssh/ssh_host_key -N "": No such file or directory
..Done
WARNING: The following packages were not set up correctly:
    gsi_openssh_setup-noflavor-pgm
Check the package documentation or run postinstall -verbose to see what happened

$  $DIR/globus/bin/ssh.d/ssh-keygen -t rsa1 -f $DIR/globus/etc/ssh/ssh_host_key -N ""

$DIR/bin/ssh.d/ssh-keygen: error while loading shared libraries: libssl.so.0.9.8: wrong ELF class: ELFCLASS64

```

The java warning, I have heard, is not an issue until you change the java package at some point in the future - the globus stuff then needs a rebuild.

I replaced the directory I specified for installation by $DIR (since my home directory tree is my own business).

The commands I ran were given by the Globus Toolkit installer for SSO access to a set of computing clusters; a seemingly simple configure-make-install triple.

The error occurs in ssh-keygen, as seen by the command-line trial of the error spit out by make install.
The library libssl.so.0.9.8 is in /lib64 (and mirrored in /lib), but is not to be found in /lib32.

There were other 32-bit library errors; I found the 32-bit libz, for example, using the synaptic gui.  The 32-bit ssl, I did found neither with a variety of synaptic search strings nor with apt-cache search.

The getlibs suggestion sounds like it is worth a try - but I am having a bit of difficulty finding third-party reviews on it.  Is this truly the only solution?

- Louis

---

### Post by Yellow Pasque on 2009-10-01
getlibs just scripts the process of installing 32-bit libraries. It makes life easy and I use it frequently. Do I count as a 3rd party? :lolflag:

---

