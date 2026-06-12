---
title: "get_cipher_algid unknown algorithm 23 / VST plugins with iLok not working anymore"
date: 2021-09-14
forum: Wine
---

### Post by tavasti2 on 2021-09-14
Most of the VST plugins that have iLok do not work anymore. They complain about 'changes in your computer'. I suspect that this is related to these messages:

```
0190:fixme:secur32:get_cipher_algid unknown algorithm 23
0190:fixme:secur32:get_mac_algid unknown algorithm 200, cipher 23 


```

I am using Ubuntu 18.04, and have tested with winehq staging versions  6.4, 6.14, 6.14 and 6.17, same results. I've had those plugins working  earlier, so something has changed.
I got hint that this might be related to gnutls packages. 

```

root@hermo:~# dpkg -l | grep gnutls
ii  libcurl3-gnutls:amd64                  7.58.0-2ubuntu3.14                              amd64        easy-to-use client-side URL transfer library (GnuTLS flavour)
ii  libcurl4-gnutls-dev:amd64              7.58.0-2ubuntu3.14                              amd64        development files and documentation for libcurl (GnuTLS flavour)
ii  libgnutls-openssl27:amd64              3.5.18-1ubuntu1.4                               amd64        GNU TLS library - OpenSSL wrapper 
rc  libgnutls26:amd64                      2.12.23-12ubuntu2.2+2                           amd64        GNU TLS library - runtime library
rc  libgnutls26:i386                       2.12.23-12ubuntu2.2+2                           i386         GNU TLS library - runtime library 
ii  libgnutls30:amd64                      3.5.18-1ubuntu1.4                               amd64        GNU TLS library - main runtime library
ii  libgnutls30:i386                       3.5.18-1ubuntu1.4                               i386         GNU TLS library - main runtime library 
ii  libneon27-gnutls:amd64                 0.30.2-3~ubuntu18.04.1                          amd64        HTTP and WebDAV client library (GnuTLS enabled)

```

```

root@hermo:~# apt search gnutls | grep gnutls
gnutls-bin/bionic-updates 3.5.18-1ubuntu1.4 amd64
gnutls-doc/bionic-updates,bionic-updates 3.5.18-1ubuntu1.4 all
libapache2-mod-gnutls/bionic 0.8.2-3ubuntu1 amd64
libcurl3-gnutls/bionic-updates,bionic-security,now 7.58.0-2ubuntu3.14 amd64 [installed]
libcurl4-gnutls-dev/bionic-updates,bionic-security,now 7.58.0-2ubuntu3.14 amd64 [installed,automatic]
libghc-gnutls-dev/bionic 0.2-4build1 amd64
libghc-gnutls-doc/bionic,bionic 0.2-4build1 all
libghc-gnutls-prof/bionic 0.2-4build1 amd64
libgnutls-dane0/bionic-updates 3.5.18-1ubuntu1.4 amd64
libgnutls-openssl27/bionic-updates,now 3.5.18-1ubuntu1.4 amd64 [installed]
libgnutls26/now 2.12.23-12ubuntu2.2+2 i386 [residual-config]
libgnutls28-dev/bionic-updates 3.5.18-1ubuntu1.4 amd64
libgnutls30/bionic-updates,now 3.5.18-1ubuntu1.4 amd64 [installed]
libgnutlsxx28/bionic-updates 3.5.18-1ubuntu1.4 amd64
libneon27-gnutls/bionic-updates,now 0.30.2-3~ubuntu18.04.1 amd64 [installed]
libneon27-gnutls-dbg/bionic-updates 0.30.2-3~ubuntu18.04.1 amd64
libneon27-gnutls-dev/bionic-updates 0.30.2-3~ubuntu18.04.1 amd64
libxmlsec1-gnutls/bionic 1.2.25-1build1 amd64
python-gnutls/bionic 3.0.0-1 amd64
rsyslog-gnutls/bionic,bionic-updates 8.32.0-1ubuntu4 amd64

```


Any suggestions what package I should install / downgrade / something else?

---

