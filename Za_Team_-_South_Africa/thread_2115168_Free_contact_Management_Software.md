---
title: "Free contact Management Software"
date: 2013-02-12
forum: Za Team - South Africa
---

### Post by polito on 2013-02-12
Dear Team!

Im looking for a free contact management software fot ubuntu, i work for NGO and we have  contact list running into thousands and we need to incorporate these contacts into a database, the database itself should have functionalities such as adding, editing, searching, deleting contacts based on certain criteria, it should be easy to manipulate and update.
Preferrable created in sql and php

Thanks and look forward to your feedback
Polito

---

### Post by tgalati4 on 2013-02-12
[http://www.sugarcrm.com/](http://www.sugarcrm.com/)  

It's a little bit of work to set up initially, but it works well.  Open source development.  Lot's of plug-ins to extend functionality.

Quicker install using a "stack":  [http://bitnami.org](http://bitnami.org)

Almost a one-click installation, but has a larger footprint and may not be as easy to extend functionality in the future.

X2CRM and OpenERP are also included as "stacks", but I have not used them and can't comment.  Check out the forums for these packages, because that is where you will spend your time searching for answers on configuration and adding functionality.

OpenERP and Open Business Management is in the Ubuntu repositories:

tgalati4@Mint14-Extensa ~ $ apt-cache search crm

obm - Open Business Management
obm-conf - Install configurations files of Open Business Management
obm-core - Install core file of Open Business Management
obm-storage - Install database of Open Business Management
obm-ui - Configure webserver for Open Business Management

openerp-desktop - OpenERP Enterprise Resource Management - metapackage
openerp6.1-core - OpenERP Enterprise Resource Management
openerp6.1-full - OpenERP Enterprise Resource Management - metapackage

---

