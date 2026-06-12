---
title: "Evolution and Entourage"
date: 2005-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by FelixAlias on 2005-11-14
Hey everybody,
I've been trying for the past week to get Entourage to export to Evolution (for that matter, I've been trying to get Evolution to import LDIF files correctly). I think there is  a serious problem with the Entourage importer (for example, with an LDIF file correctly exported with Mozilla Mail, it only imports the last name and nothing else).
- Entourage exports MBOX files, and Evolution recognizes and imports them, however it only imports a message with no body, and ? and ? as the Subject and From headers.
- The LDIF file is imported, but only the last name is imported (I checked the full contact, but still nothing). I have looked in the LDIF, and all the required information is there.
- I'm also trying to find some way to use Filemaker in Linux. Does anyone know of any solutions (Mac-On-Linux will not be an option)?

So does anybody have any experience in this area? Any help would be appreciated.

---

### Post by ssam on 2005-11-14
can thunderbird import the mbox files?

mol is probably only solution for filemaker. there isn't a wine equivilent for mac os x. there seems to be a file maker server for linux (google hints at it, but i did not read any pages), but i imagine it would be x86 linux. could you migrate to something like mysql?

---

### Post by FelixAlias on 2005-11-14
Thunderbird! Of course!
Thanks, I'll give that a try.. I actually forgot about it for a while, even though it's what I usually reccomend to others and use at home. 

Actually, I did try to migrate the database to MySQL using CSV.. I wasn't able to do it, because I need some way to remove line breaks and change them into semicolons.

I do, however have a temporary solution for the Filemaker problem. I exported the Filemaker database as a SYLK (*.slk) file, and then I imported it into OpenOffice.

---

### Post by ssam on 2005-11-14
sed can convert line breaks to semicolons with out to much trouble. i can't think of the syntax off the top of my head but you might be able to find a tutorial somewere. between grep, sed, awk, and perl, you can manipulate a text file in anyway you want. you just tie the utilities together with bash. this is why so many files in unix are text files (html, xml, config files, log files, c, scripts ...)

i think thunderbird is in main so just open synaptic and search for it.

---

### Post by FelixAlias on 2005-11-14
I'll look up the sed info.

I installed Thunderbird, and it could import everything, with a one problem: Everything but the first name and last names were in the wrong fields. Actually, that doesn't matter so much, with one exception: Email is in the slot Custom 4. This really needs to be in the email slot. I may be able to re-export this from address book (I'm running Sync Entourage-Address Book as I write), so that should work.. But what about email? Thunderbird doesn't work with Mbox files, and Evolution doesn't import the MBox files correctly (KMail's option to import them is grayed out, even though kdepim-kio-plugins and all the other kio-plugins packages are installed).

Thanks though, I have the feeling a conclusion will be reached soon.

UPDATE:
After about 30 minutes of searching, I cooked up this solution:
cat dbexp.csv | tr -d '\n' > dbexpfin.csv
that worked for me. \r is for carriage returns, I believe, so it depends on what you want to remove.

Okay, so:
- Contacts issue: Probably solved after finishing the sync and re-exporting
- Filemaker issue: completely solved.
- Mail issue: Not yet solved, although I think I want to use Evolution instead of thunderbird because it integrates better with the Gnome desktop.
That's pretty good progress so far, thanks everybody.. well, ssam, anyways :P

-Felix

---

### Post by ssam on 2005-11-14
i recommend that you try the desktop support forum or the mozillazine.org forums for the thunderbird issues.

i have successfully moved mail from mac.app on mac os x to thunderbird on mac os x, and then copied that file from mac os x to linux and it work. have you tried importing the mail into mail.app as a halfway step. (i think the tiger mail.app doesn't use mbox any more, so you might have to find an older version)

---

### Post by FelixAlias on 2005-11-14
[QUOTE=ssam]i recommend that you try the desktop support forum or the mozillazine.org forums for the thunderbird issues.

i have successfully moved mail from mac.app on mac os x to thunderbird on mac os x, and then copied that file from mac os x to linux and it work. have you tried importing the mail into mail.app as a halfway step. (i think the tiger mail.app doesn't use mbox any more, so you might have to find an older version)[/QUOTE]
I guess I'll try the Mail.app step next. I'm in luck, the computer I'm exporting from is Panther! 10.3.

UPDATE:
Fantastic news!! Mail 10.3's mbox's work GREAT with evolution. I'm pretty sure I can find a sync between Entourage and Apple Mail (I did before). Also, the Address Book vCards work GREAT in evolution, with everything where it should be.

Thanks so much for your help!

---

### Post by edward4130 on 2007-01-17
If you have the program or the extract tool for entourage to go to apple mail please post.  I am considering a move fully to ubuntu on my laptop as well, getting this to happen is the key.

Thanks!  If this doesn't get updated I will post my findings as well.

-Edward

---

