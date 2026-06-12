---
title: "I suffer with correct install of: saslauthd, userdb, auth login"
date: 2007-02-06
forum: Za Team - South Africa
---

### Post by Morons on 2007-02-06
I am trying to get my Postfix mailserver to authenticate smtp by using userdb.  I create the userdb file fine.```
root@beta:~# cat /etc/courier/userdb
test@zone.tld uid=10002|gid=10001|home=/var/www/web1/user/zone.tld_test|shell=/bin/false|systempw=$1$9pUjT.t.$QYCeLjunktifiedu555k1|/var/www/www.zone.co.za/user/zone.tld_test/Maildir
```
The test is done this way```
root@beta:~# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 beta.zone.tld ESMTP Postfix (Ubuntu)
EHLO localhost
250-beta.zone.tld
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
AUTH LOGIN
334 VXNlcm5hbWU6        <<< this is Base64 for "Username"
dGVjunktifiedLmNvLnph   <<< this is Base64 username
334 UGFzc3dvcmQ6         <<< this is Base64 for "Password"
djunkA==                       <<< this is Base64 for password
535 5.7.0 Error: authentication failed: authentication failure
```
main.cf Include ```
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
smtpd_recipient_restrictions = permit_sasl_authenticated
```I hope I included all the relevant lines```
The smtpd.conf[code]root@beta:~# cat /etc/postfix/sasl/smtpd.conf
# pwcheck_method: saslauthd
#pwcheck_method: auxprop
mech_list: plain login
pwcheck_method:    auxprop
auxprop_plugin:    sasldb
sasldb_path:       /etc/courier/
```saslauthd```
root@beta:~# cat /etc/default/saslauthd
# This needs to be uncommented before saslauthd will be run automatically
START=yes

PARAMS="-m /var/spool/postfix/var/run/saslauthd -r"

# You must specify the authentication mechanisms you wish to use.
# This defaults to "pam" for PAM support, but may also include
# "shadow" or "sasldb", like this:
# MECHANISMS="pam shadow"

# MECHANISMS="pam"
MECHANISMS="sasldb"
```
What did I miss - Oh yes no error messages, If I include "pam" here i can authenticate with the user from the /etc/passwd & shadow files.  HELP PLEASE!:lolflag:

---

