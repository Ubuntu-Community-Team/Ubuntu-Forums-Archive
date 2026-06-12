---
title: "Pidgin 2.0.0 deb anyone?  Get it while it's hot!"
date: 2007-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by cmost on 2007-05-04
I love Gaim!  They've thrown a lot of nice features into the new Pidgin 2.0 release, which just came out yesterday.  Since there are a lot of dependencies, I thought i'd save people some trouble and compile a deb package for amd64.  I compiled gstreamer support into this deb too.  Unfortunately, I don't have a way to host the file.  If someone can host it, please message me and I'll transfer the deb file to your capable hands.  Cheers!

*** EDIT ***
Sorry for the delay guys!  Here's the link to grab this deb.  Enjoy!

[http://rapidshare.com/files/29614005/pidgin_2.0.0-1_amd64.deb.html](http://rapidshare.com/files/29614005/pidgin_2.0.0-1_amd64.deb.html)

---

### Post by marcos89 on 2007-05-04
Email the package to me, ill host em ... [email]marcosrdz@gmail.com[/email]

---

### Post by jfca283 on 2007-05-05
after installation, i wonder how can i apply a theme?

---

### Post by Cappy on 2007-05-05
Here is the changelog: [http://developer.pidgin.im/browser/ChangeLog](http://developer.pidgin.im/browser/ChangeLog)

Here is my pick of the most significant changes for non-developers:

89	        Sounds:
90	        * Beautiful new default sounds (Brad Turcotte)
91	        * Use GStreamer for playing sounds, instead of libao
92	        * A volume control in the preferences (Casey Harkins)

126	        * New music messaging plugin (Christian Muise, Google Summer of Code)
127	        * gaim-remote has been superceded by new DBUS bindings within libpurple
128	          (Piotr Zielinski, Google Summer of Code)
131	        * The functionality of the auto-reconnect plugin has been
132	          moved into the core, and the plugin itself has been removed.
133	        * 'Highlight when nick said' option added to Message Notification
134	          plugin.
136	        * New Log Reader plugin that can read and display logs from Adium,
137	          MSN Messenger, and Trillian in the log viewer
138	        * New Contact Availability plugin that attempts to predict the
139	          times when people in your buddylist will most likely respond
140	          to you, based on times in the past when they have responded
141	          (Geoffrey Foster, Google Summer of Code)
142	        * A few new plugins: Autoaccept, Autoreply, Buddy Notes, New Line,
143	          Offline Message Emulation, Conversation Colors and Markerline.

 MSN Features:
146	        * Custom smiley receiving support (Irving Cordova & Francesco Fracassi)
147	        * Added support for sending (with the /nudge command) and receiving
148	          "nudges" (Julien Cegarra, Martin Bayard)
149	        * Added an account action to open your Hotmail inbox from MSN
150	        * Bi-directional text is correctly handled now (Shlomi Loubaton)
151	
152	        Yahoo Features:
153	        * Stealth Settings have been implemented
154	        * Doodle is now supported (Andrew Dieffenbach, Google Summer of Code)
155	        * Buddies' requests to add you to their lists now prompt for
156	          authorization
157	        * Account option to ignore chat and conference invitations (Peter
158	          Lawler)
159	        * Added a /list command to bring up the room list (Peter Lawler)
160	
161	        AIM/ICQ Features:
162	        * ICQ file transfer support with newer ICQ clients (Jonathan Clark,
163	          Google Summer of Code)
164	        * Many overall improvements to AIM and ICQ file transfers (Jonathan
165	          Clark, Google Summer of Code)
166	        * Support for pausing and resuming AIM and ICQ file transfers
167	          (Graham Booker)
168	        * Ability to set ICQ "require authorization" and "web aware"
169	          setting (Ettore Simone)
170	        * ICQ encoding fix for offline buddies (Ilya Konstantinov)
171	
172	        IRC Features:
173	        * SSL support for IRC connections (Daniel Atallah)
174	        * Show an error message when temporarily unable to join an IRC
175	          channel or change your nick
176	        * Added /nickserv, /memoserv, /chanserv and /operserv
177	          commands (Joao Luís Marques Pinto)
178	        * Added CTCP VERSION via /version (Andrej Krivul&#269;ík)
179	        * Added /whowas command (achris)
180	
181	        Jabber Features:
182	        * Support for SRV lookups
183	        * Support for buddy icons
184	        * Jabber User Directory searching
185	
186	        SILC Features:
187	        * Whiteboard support (Pekka Riikonen)
188	        * Sending/receiving images in IMs (Pekka Riikonen)
189	        * Cipher and HMAC selection support (Pekka Riikonen)
190	        * Buddy Icon support (Pekka Riikonen)
191	
192	        Other Protocol Changes:
193	        * Bonjour (Rendezvous) protocol support (Juanjo Molinero Horno, Google
194	          Summer of Code)
195	        * Updated Gadu-Gadu protocol support (Bartosz Oler, Google Summer of
196	          Code).  This requires the libgadu library.  See
197	          [http://pidgin.im/faq.php#libgadu](http://pidgin.im/faq.php#libgadu) for more information.
198	        * SIP/SIMPLE support (Thomas Butter, Google Summer of Code)
199	        * Sametime protocol support
200	          Requires the meanwhile library: [http://meanwhile.sourceforge.net](http://meanwhile.sourceforge.net)
201	        * QQ protocol support (Mark Huetsch, Google Summer of Code, and the
202	          developers of the OpenQ project)
203	        * Removed the Napster and TOC protocols plugins

---

### Post by cmost on 2007-05-05
@marcos89

Thanks for your offer.  My e-mail system does not permit large file attachments.  I've hosted the file on 'Rapidshare'.  I don't know why I didn't think of that in the first place.  The link was appended to my original post.

---

### Post by stmiller on 2007-05-05
Cool thanks!

---

### Post by jamesford on 2007-05-05
its available from getdeb.net too

---

### Post by Ev1L on 2007-05-06
great job with this, but i would have a little request...
When Pidgin goes autoaway, to become available again just moving mouse, it needs XScreenSaver packages (and maybe another one, I saw on pidgin site, bug section) and also a parameter during the configure (i am not sure too).
In the end I handled, but I am quite noob, so I preferred trying this package (this installs also icons better than me :p ) and now autoaway doesn't restore correctly again, so I hope in your improved package ;)

---

### Post by cmost on 2007-05-07
Hi Ev1l!  I'm not quite understanding what you're asking for.  If you can provide me a few more details about what you're needing from the pidgin package, I will be happy to recompile the package with the needed parameters.

---

### Post by Ev1L on 2007-05-07
the bug i am talking about is here: [http://developer.pidgin.im/ticket/561](http://developer.pidgin.im/ticket/561)
and the required packages are these two: libSM-devel libXScrnSaver-devel (but in synaptic i found them with slightly different names...)

let me know if you need more specific infos
but as i said, i am the noob here, i think i couldn't be more specific than this :p
but i am pretty sure that i solved the mentioned problems playing with them

---

### Post by cmost on 2007-05-07
Hi Ev1l.  I read the bug report you linked with and according to it, that bug was fixed in the 2.0.0 final code release.  My deb file uses the final 2.0.0 code so there shouldn't be any issues.  I'm running this fine and haven't had any problems so far.  :-)

---

### Post by Cappy on 2007-05-07
Does anyone know if Pidgin supports AIM Offline Messaging? Not the Pidgin's plugin but the ability to message someone who is offline, and then you can go offline, and it is store in AOL's server until that person comes back online. It came out with AOL 6.0.

---

### Post by pirothezero on 2007-05-07
I told myself to not update for a while but after talking to a friend of mine I got convinced and figured I'd give it a go. It's alright don't really like the new icons but I can live with it.

---

### Post by gummygod on 2007-05-07
no1 made a deb on dapper 32 bit have they? cause im having compiling troubles (this annoying perl error takes the place of the real one). thanks

---

### Post by Ev1L on 2007-05-08
> **cmost said:**
> Hi Ev1l.  I read the bug report you linked with and according to it, that bug was fixed in the 2.0.0 final code release.  My deb file uses the final 2.0.0 code so there shouldn't be any issues.  I'm running this fine and haven't had any problems so far.  :-)

you should be right, but anyway using you compiled file i have this problem that it doesn't come back from away when i move mouse, and the same problem i had before compiling with those 2 libs, so if you'll have a moment to try them, it would be greatly appreciated... :p

---

### Post by Corbelius on 2007-05-08
[http://ubuntuforums.org/showpost.php?p=2616416&postcount=216](http://ubuntuforums.org/showpost.php?p=2616416&postcount=216)

---

### Post by Ev1L on 2007-05-08
with those packages all works :)
congrats corbelius ;)

---

### Post by PendragonUK on 2007-05-08
So how long before Pidgin is part of an normal update? Will Gaim be replaced by Pidgin??

---

### Post by Corbelius on 2007-05-09
> **PendragonUK said:**
> So how long before Pidgin is part of an normal update? Will Gaim be replaced by Pidgin??

I think to gutsy gibbon.

---

### Post by zmigliozzi on 2007-05-09
can i buy you a drink? this is awesome.

---

