---
title: "RTL8185 with PEAP"
date: 2008-10-10
forum: x86 64-bit Users
---

### Post by vertago1 on 2008-10-10
Hey, I recently reinstalled kubuntu hardy remix on my amd64 machine and after I setup everything I ran into an issue with ndiswrapper that I had not had before where the driver wouldn't load so I tried to work around the issue using the native driver for the RTL8185. So far the driver seems to be working but I can't get the included version of wpa_supplicant to authenticate over peap.

Can anyone tell me what the problem is?

Is it related to the "ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported" error? or is there a way to fix this problem?

I am fairly sure the immediate problem is described by, "unable to get local issuer certificate" but I do not know how to resolve the issue.

Any guidance / advice?


> ****@****-desktop:~/Desktop/Downloads/rtl8185/wpa_supplicant-0.4.9$ sudo ./wpa_supplicant -Dipw -iwlan0 -c/etc/wpa_supplicant.conf
Trying to associate with 00:02:2d:4a:49:99 (SSID='****' freq=0 MHz)
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:02:2d:4a:49:99
CTRL-EVENT-EAP-STARTED EAP authentication started
CTRL-EVENT-EAP-METHOD EAP method 25 (PEAP) selected
CTRL-EVENT-EAP-FAILURE EAP authentication failed
CTRL-EVENT-EAP-STARTED EAP authentication started
TLS - SSL error: error:0B07C065:x509 certificate routines:X509_STORE_add_cert:cert already in hash table
CTRL-EVENT-EAP-METHOD EAP method 25 (PEAP) selected
TLS: Certificate verification failed, error 20 (unable to get local issuer certificate) depth 0 for '/C=US/ST=Texas/L=****/O=****/OU=****/CN=****'
SSL: SSL3 alert: write (local SSL3 detected an error):fatal:unknown CA
OpenSSL: tls_connection_handshake - SSL_connect error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
CTRL-EVENT-EAP-FAILURE EAP authentication failed

---

### Post by Mauriciobc on 2009-06-05
Same problem here, can't get it past authentication...

---

