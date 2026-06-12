---
title: "boinc on amd 64 bit"
date: 2006-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by psyncho on 2006-09-17
Hi,

I looked at the einstein, climateprediction.net, and simap projects in trying to setup boinc on my server.  In the end I found simap to be the most clear, have the best website, and have the best people responding on their forums.  I am now up and running boinc on amd 64 attached to the simap project and thought I'd share how I did it.  First, 
a little about my machine and situation:

I have a server with amd 64 bit cpu, no gui (e.g. no xwindows).

First, I installed boinc from the ubuntu multiverse repository through aptitude (if this doesn't make sense, look up aptitude on the forums or
ubuntu documentation).  This very nicely sets everything up for you, including boinc starting on its own, and a boinc user...the only problem is that the boinc client is a 64 bit version which no projects support directly yet.

Because installing through aptitude sets up the daemon (automatic running of the client on startup of the machine), you don't have to run boinc or boinc_client, you want to attach to a project using
boinc_cmd (in fact, if you do run boinc, from within your user directory, then boinc files will be placed in your user directory and boinc will start giving you access errors...to get rid of that just delete any boinc files from your user directory).

The actual boinc programs are placed in /usr/bin
The data for boinc resides in /var/lib/boinc_client
The entry for the daemon is in /etc/init.d/boinc_client

First, register with the simap project.  I did it the "special way" because I don't have a gui.  Go to here:

[http://boinc.bio.wzw.tum.de/boincsimap/create_account_form.php](http://boinc.bio.wzw.tum.de/boincsimap/create_account_form.php)

and fill out all the info.  An email will be sent to you with the project name (a URL) and a key.

In a terminal on your linux box, type 
>boinc_cmd --project_attach [project-URL] [key]
replacing [project-URL] with the project URL and [key] with the key from the email.  

Go to the simap webpage here:
[http://boinc.bio.wzw.tum.de/boincsimap/appdownloads.php](http://boinc.bio.wzw.tum.de/boincsimap/appdownloads.php)

Download the simap and hmmer apps for the amd64 bit platform. Alternatively, if they haven't posted all the apps they have on their download page, but you might be able to find them here:

[http://boinc.bio.wzw.tum.de/boincsimap/download](http://boinc.bio.wzw.tum.de/boincsimap/download)
(scroll to the bottom)

...otherwise, bug them on the forum.


You then have to make a file called app_info.xml
Mine looks like this:
 <app_info>
     <app>
         <name>simap</name>
     </app>
     <file_info>
         <name>simap_5.10_ia64-unknown-linux</name>
     </file_info>
     <app_version>
         <app_name>simap</app_name>
         <version_num>510</version_num>
         <file_ref>
             <file_name>simap_5.10_ia64-unknown-linux</file_name>
             <main_program/>
         </file_ref>
     </app_version>
        <app>
         <name>hmmer</name>
     </app>
     <file_info>
         <name>hmmer_5.07_x86_64-unknown-linux-gnu</name>
     </file_info>
     <app_version>
         <app_name>hmmer</app_name>
         <version_num>507</version_num>
         <file_ref>
             <file_name>hmmer_5.07_x86_64-unknown-linux-gnu</file_name>
             <main_program/>
         </file_ref>
     </app_version>
 </app_info>

The app_info.xml file basically lists the apps that you downloaded, so just try and make sure the names match them.

You then want to put both this app_info.xml file and the programs you downloaded into the directory for the project.  When you attach to a project, a directory is created for it inside

/var/lib/boinc_client/projects

For simap, right now, mine is:

/var/lib/boinc-client/projects/boinc.bio.wzw.tum.de_boincsimap

...so copy the app_info.xml file and app files that you downloaded into that directory.

Then, just to be thorough, restart the boinc client.  You do this by issueing the command:

/etc/init.d/boinc-client restart

It should say that its stopping and then starting again (if not then you have other issues, e.g. either its not installed or however you installed it did not create the daemon info).

you then should issue these commands:

>boinc_cmd --project [project-URL] reset
>boinc_cmd --project [project-URL] update

where [project-URL] is replaced by the projects url reported in the email sent to you when you registered.

You can then grab the messages from the client by doing this:

>boinc_cmd --get_messages seqno

It should say that it attached, is using the anonymous client, and requesting work, etc.

You can also do this:

boinc_cmd --get_state

and it will give you some info on state.  You have to be careful though because it will give you info even if the client isn't actually getting work.  You want to see that under the apps line that your
simap apps are listed.

you can always do:

boinc_cmd --help 

for help on that command.

There might be other posts on how to use boinc on 64 bit using 32 bit apps, but there weren't any when I wrote this.  This is also only for the simap project, which from what I've read is the only project that actually uses the extra computational power of the 64 bit processor (i.e. their 64 bit app runs a lot faster than their 32 bit, so I'm contributing more than the average joe to their project).

But, if you really want to search for extra-terrestrials or whatever, then keep looking, more and more people are finally writing about this because so many people are having problems with it.  Personally I found the boinc documentation to assume quite a lot, be incomplete, and mostly unclear or inaccessible (not because it was lofty, but because it was hidden away in an illogical part of their website, e.g. to set up an anonymous client download you have to follow the link for building your own client!)

cheers, 
John

---

