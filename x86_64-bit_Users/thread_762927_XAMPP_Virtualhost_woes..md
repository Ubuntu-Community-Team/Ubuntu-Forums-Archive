---
title: "XAMPP Virtualhost woes."
date: 2008-04-22
forum: x86 64-bit Users
---

### Post by christhegoth on 2008-04-22
I've read and I've read and I just can't the problem.  Virtualhosts.  2 work, 1 doesn't.  I've checked the forums and others have had troubles but still.  I've never set up a DNS for a domain before but I'm pretty sure it's right.

The 1 that doesn't I'm guessing is due to the www. factor but I just can't see how to sort it.  It keeps pointing at the wrong folder.  The ctgsite folder.  Why I have no idea.  So I ask, nay beg ( 3 days of *head-desk*ing ) for your assistance.

test and ctgsite work fine, but gothfiles simply won't.  Help me Ubuntu-forum-kinobi, you're my only hope :confused:

/opt/lampp/etc/extra/httpd-vhosts.conf is below:

#
# Virtual Hosts
#
# If you want to maintain multiple domains/hostnames on your
# machine you can setup VirtualHost containers for them. Most configurations
# use only name-based virtual hosts so the server doesn't need to worry about
# IP addresses. This is indicated by the asterisks in the directives below.
#
# Please see the documentation at 
# <URL:http://httpd.apache.org/docs/2.2/vhosts/>
# for further details before you try to setup virtual hosts.
#
# You may use the command line option '-S' to verify your virtual host
# configuration.

#
# Use name-based virtual hosting.
#
NameVirtualHost *:80

#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
# The first VirtualHost section is used for all requests that do not
# match a ServerName or ServerAlias in any <VirtualHost> block.
#

<VirtualHost *:80>
    ServerAdmin [email]christian.j.wilcox@gmail.com[/email]
    DocumentRoot /var/www/gothfiles/
    ServerName [www.gothfiles.org.uk](www.gothfiles.org.uk)
    ServerAlias *.gothfiles.org.uk gothfiles.org.uk
    ErrorLog logs/www.gothfiles.org.uk-error_log
    CustomLog logs/www.gothfiles.org.uk-access_log common
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin [email]christian.j.wilcox@gmail.com[/email]
    DocumentRoot /var/www/ctgsite/
    ServerName christhegoth.homeunix.com
    ErrorLog logs/christhegoth.homelinux.org-error_log
    CustomLog logs/christhegoth.homelinux.org-access_log common
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin [email]christian.j.wilcox@gmail.com[/email]
    DocumentRoot /var/www/test/
    ServerName christhegoth.homelinux.net
    ErrorLog logs/christhegoth.homelinux.net-error_log
    CustomLog logs/christhegoth.homelinux.net-access_log common
</VirtualHost>

---

### Post by VitalBodies on 2008-05-09
I would wonder about this line:
ServerAlias *.gothfiles.org.uk gothfiles.org.uk

---

### Post by christhegoth on 2008-05-09
Yeah.  Shifted it to localhost a while back and it started working.

Thanks for the reply :)

---

