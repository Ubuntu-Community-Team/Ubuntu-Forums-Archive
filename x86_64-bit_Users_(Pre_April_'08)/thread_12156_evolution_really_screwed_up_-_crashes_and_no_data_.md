---
title: "evolution really screwed up - crashes and no data in contact"
date: 2005-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by s_p_a_r_k_y on 2005-01-22
I am using evolution 2.1.3.2, and its very very unstable on my AMD64 computer. If I reply to a message, it crashes. If I go to preferences, it crashes. 

Also all my contact data and calendar entries have disappeared as of late. The address book file is still there and has all my contacts in it, but it doesn't seem like the database server is working at all, which might be causing the crashes.

I'm not a debugger so I don't know whats going wrong really, but I can try to paste output from the console.

First error I see

(evolution-2.2:25263): libebook-WARNING **: e_book_construct: Could not obtain a handle to the Personal Addressbook Server with IID `OAFIID:GNOME_Evolution_DataServer_BookFactory:1.2'

(evolution-2.2:25263): evolution-addressbook-WARNING **: error loading addressbook : e_book_load_uri: no factories available for uri `file:///home/god/.evolution/addressbook/local'

If I click on the calendar button to bring up that view I get the following errors

(evolution-2.2:25263): libecal-WARNING **: e-cal.c:1070: Could not activate calendar factory (OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2)

(evolution-2.2:25263): libecal-WARNING **: e-cal.c:1070: Could not activate calendar factory (OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2)

(evolution-2.2:25263): libecal-WARNING **: e-cal.c:1070: Could not activate calendar factory (OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2)

(evolution-2.2:25263): eab-widgets-CRITICAL **: eab_view_discard_menus: assertion `view->view_instance' failed

Here is a print out of my address book folder
root@bart:/home/god # ls -l .evolution/addressbook/local/system
total 380
-rw-r--r--  1 god god 393216 2005-01-18 11:11 addressbook.db
-rw-r--r--  1 god god  11173 2005-01-18 11:11 addressbook.db.summary
 
Hope someone can help me. Evolution isn't much help for just e-mails.

---

