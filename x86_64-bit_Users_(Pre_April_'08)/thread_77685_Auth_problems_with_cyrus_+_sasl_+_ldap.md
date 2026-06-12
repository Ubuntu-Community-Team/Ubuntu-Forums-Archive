---
title: "Auth problems with cyrus + sasl + ldap"
date: 2005-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by TizianoTissino on 2005-10-17
Friday I upgraded my server to breezy. After that, I got problems with authentication in cyrus/imap.
I'm using sasl to authenticate clients; in turn, sasl use pam_ldap.
Before upgrade all worked fine; now, sometimes auth succeeds while other times fails.

This is the count of today connections: 959 were ok, 768 were not.
# grep -c ' login:' /var/log/syslog
959
# grep -c ' badlogin:' /var/log/syslog
768


Here's an extract from my logs:

 (an example on failure)
on /var/log/auth.log:
Oct 17 11:25:13 localhost saslauthd[20338]: pam_ldap: error trying to bind as user "uid=fqu,ou=People,dc=itaca,dc=coopsoc,dc=it" (Invalid credentials)
Oct 17 11:25:13 localhost saslauthd[20338]: DEBUG: auth_pam: pam_authenticate failed: Authentication failure
Oct 17 11:25:13 localhost saslauthd[20338]: do_auth         : auth failure: [user=fqu] [service=imap] [realm=] [mech=pam] [reason=PAM auth error]

on /var/log/syslog:
Oct 17 11:25:01 localhost cyrus/imapd[20650]: telling master 1
Oct 17 11:25:01 localhost cyrus/master[19162]: service imaps pid 20650 in BUSY state: now available and in READY state
Oct 17 11:25:04 localhost cyrus/imapd[20650]: telling master 2
Oct 17 11:25:04 localhost cyrus/imapd[20650]: accepted connection
Oct 17 11:25:04 localhost cyrus/imapd[20650]: telling master 3
Oct 17 11:25:04 localhost cyrus/master[19162]: service imaps pid 20650 in READY state: now unavailable and in BUSY state
Oct 17 11:25:04 localhost cyrus/master[19162]: service imaps pid 20650 in BUSY state: now serving connection
Oct 17 11:25:04 localhost cyrus/imapd[20650]: starttls: TLSv1 with cipher AES256-SHA (256/256 bits new) no authentication
Oct 17 11:25:04 localhost cyrus/imapd[20650]: badlogin: net84-253-166-106.mclink.it[84.253.166.106] plaintext ece SASL(-13):
user not found: checkpass failed
Oct 17 11:25:09 localhost cyrus/imapd[20650]: badlogin: net84-253-166-106.mclink.it[84.253.166.106] plaintext ece SASL(-13):
user not found: checkpass failed
Oct 17 11:25:13 localhost cyrus/imapd[20650]: badlogin: net84-253-166-106.mclink.it[84.253.166.106] plaintext ece SASL(-13):
user not found: checkpass failed


(an example on successfull login)
Oct 17 09:38:34 localhost cyrus/imapd[18995]: login: net84-253-166-106.mclink.it[84.253.166.106] tti plaintext+TLS
Oct 17 09:38:34 localhost cyrus/imapd[18995]: seen_db: user tti opened /var/lib/cyrus/user/t/tti.seen
Oct 17 09:38:34 localhost cyrus/imapd[18995]: open: user tti opened INBOX

---

### Post by TizianoTissino on 2005-10-18
Finally, I discovered where was the problem: each instance of imapd correctly authenticate only her first connection. All subsequent connections will get a 'badlogin' reply.

So, I set my /etc/cyrus.conf with lines like this one:
        imaps           cmd="imapd -s -U 1" listen="imaps" prefork=0 babysit=5

The -U flag tells imapd to use each instance for only one connection and then exit.

---

