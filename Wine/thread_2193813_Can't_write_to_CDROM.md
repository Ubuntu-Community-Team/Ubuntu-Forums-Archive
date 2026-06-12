---
title: "Can't write to CDROM"
date: 2013-12-14
forum: Wine
---

### Post by cearlp on 2013-12-14
I don't know if this is the correct forum for this but here goes.
Installed Wine 1.4 1.4.1-0ubuntu7 on Ubuntu 13.10.
Loaded Quicken 2002.
Everything runs fine except I can't write a Quicken backup file to the CDROM.
How does Wine assign drive letters to linux devices or is there no burn capability through wine to a linux carom?

---

### Post by varunendra on 2013-12-15
Disclaimer : Whatever I have mentioned below is mostly my 'Assumption' based on my limited knowledge about what and what can't be done in wine, and I may be wrong.

The drive letters in wine are mapped to directory paths of linux, not directly to device files. As such, you can add a drive letter (using "wine configuration" program) and map it to /cdrom and set its 'Type' (in "Advanced" option of the dialogue box) to "CDROM". But that would only allow you to read a **mounted** CD/DVD and recognize it as such.

"Mounted" is the keyword here. Any drive/partition that is not already mounted in Linux can't be accessed from wine, and 'Writing' can't be performed on a mounted disc.

Besides, as far as I know, 'writing' or 'disc burning' is a **privileged operation**, and wine should never be run in privileged mode (to avoid exposing the whole system to it).

I believe your only chance is to be able to find and install such an application in wine that allows creating virtual 'writers' (all those I know of create virtual 'read-only drives, not 'writers'), then show its drive as your writer to the program you mentioned (I have no idea what Quicken 2002 is or what it does).

Alternatively, and what is a lot more simpler to achieve if your program in question allows that, you can write to files (iso, or whatever format it outputs to) instead of directly writing to disks, then use a native linux program to write the file (hopefully ISO) to a physical disc.

---

### Post by cearlp on 2013-12-15
Thanks Varun,
I can see Quicken 2002 under wine will not function as it did under Windows.

---

### Post by varunendra on 2013-12-15
Out of curiosity, I searched Quicken and figured (roughly) what it does.

I have absolutely no experience of using such applications, but a quick search in Synaptic Package Manager brought these up that look similar to it (in the same order they turned up, doesn't mean the top one is necessarily the best and the bottom one worst) -

[indent]**1) kmymoney :** This is what its description says -
> KMyMoney is the Personal Finance Manager for KDE. It operates similar to
MS-Money and Quicken, supports different account types, categorisation of
expenses, QIF import/export, multiple currencies and initial online banking
support.

**2) grisbi :**
> Grisbi is a personal accounting program. Grisbi can handle multiple
accounts, currencies and users. It helps you manage your money using
third party, expenditure and receipt categories, as well as budgetary
lines, financial years, and other information that makes it adapted
for both personal and associative accounting.

Grisbi can import accounts from QIF, OFX and Gnucash files. It can
print reports using LaTeX or export them via HTML.

**3) gnucash :**
> Gnucash provides accounting functions suitable for use by small businesses and
individuals. It can track finances in multiple accounts, keeping running and
reconciled balances. There is support for customer, vendor and employee
processing. It has an X based graphical user interface, double entry, a
hierarchy of accounts, expense accounts (categories), and can import Quicken
QIF files and OFX files.

**4) skrooge :**
> Skrooge allows you to manage your personal finances. It is intended to be used
by individuals who want to keep track of their incomes, expenses and
investments. Its philosophy is to stay simple and intuitive.

Here is the list of Skrooge main features:
 * QIF, CSV, KMyMoney, Skrooge,  import/export
 * OFX, QFX, GnuCash, Grisbi, HomeBank import
 * Advanced Graphical Reports
 * Several tabs to help you organize your work
 * Infinite undo/redo
 * Instant filtering on operations and reports
 * Infinite categories levels
 * Mass update of operations
 * Scheduled operations
 * Track refund of your expenses
 * Automatically process operations based on search conditions
 * Multi currencies
 * Dashboard

**5) eqonomize:**
> Eqonomize! is a personal accounting software for KDE, with focus on
efficiency and ease of use for the small household economy. It
provides a complete solution, with bookkeeping by double entry and
support for scheduled recurring transactions, security investments,
and budgeting. It gives a clear overview of past and present
transactions, and development of incomes and expenses, with
descriptive tables and charts, as well as an approximation of future
account values.[/indent]

I'm sure many of us would find it helpful and interesting if you try any of these and can comment on their quality/usefulness, like whether they are satisfactory or equally good (or maybe even better !).

---

