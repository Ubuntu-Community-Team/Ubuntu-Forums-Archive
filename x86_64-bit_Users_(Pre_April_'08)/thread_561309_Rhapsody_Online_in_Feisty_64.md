---
title: "Rhapsody Online in Feisty 64"
date: 2007-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by cinajohn on 2007-09-27
So here goes another rhapsody cry for help.  

Seems by the other threads that it either works right of the bat or else it is very problematic.

When ever I try to use the service, it prompts me to install the player engine plugin...so I do, and then it tells me to install the player engien plugin...so I do, and then it tells me to install the player engine plugin...so I do, then it tells me to install the player engine plugin...so I do...you get the idea, it is an endlessly repeating loop.

I have tried a lot of things, from nspluginwrapper to manually inserting the plugin in the plugins folder to attempting to install helix or realplayer (which by the way I cant get going in 64).

So I guess my question is this...is it a lost cause because I am running the AMD64 version of feisty?...Has anyone got it working in 64?

If it has run on feisty AMD64, than how?

Thanks in advance

---

### Post by Sally on 2007-09-27
Are you using Firefox or Iceweasel? I went through the same loop, and eventually got this working by creating a dir for Rhapsody under ~/.mozilla/plugins. After you add that directory restart your browser, it should work.

---

### Post by cinajohn on 2007-09-27
Firefox.  I will try it and let you know.

Thanks for the tip

--Update-- No luck, I have done as you suggested, as well as making sure the engine is in all mozilla and firefox plugins folders.

---

### Post by hise0001 on 2007-10-22
I'm running AMD64 version of Gutsy.

I had the same install.. launch.. its says its not installed, please install... install.... launch loop going on.

I installed flash from the repository to get nsplugginwrapper installed.  I think I followed nsplugginwrapper instructions correctly to install the rhapsody plugin into nsplugginwrapper.  I don't get the install loop anymore; but, says it's authenticating forever.

Anybody got this to work?

--Hise

---

### Post by garretwcox on 2007-10-23
Same boat:
On Gutsy 64

I installed flash/nswrapper the automated way (just visited a site that needed flash, clicked the plugin, and let ubuntu install everything...very nice btw)

I then visited rhapsody, and tried to install the plugin. I first got a "no disk space available" error.
I actually traced this back to an older bug where firefox will not create a plugins directory if one doesn't exist, so I created ~/.mozilla/plugins.

When I attempted to install the plugin this time, the plugin file nprhapengine.so appeared in the plugin directory. However, when I tried to use Rhapsody, it just asked me to install the plugin again.

I moved the file to my downloads directory, and attempted to install it via nswrapperplugin via the following command line.

sudo nspluginwrapper -i ~/downloads/nprhapengine.so

this put the file npwrapper.nprhapengine.so is /usr/lib/mozilla/plugins

Unfortunately, now when I go to rhapsody and sign in, it gets stuck with a screen that just says "loading....." 

Interestingly enough, if I run the updater via

sudo nspluginwrapper -v -a -u

I get:

Update plugin /usr/lib/firefox/plugins/npwrapper.nprhapengine.so
  NS4 plugin /home/gygelly/downloads/nprhapengine.so is already installed system-wide, removing wrapper

At this point, the file npwrapper.nprhapengine.so disappears from /usr/lib/moziall/plugins

Of course, if I visit rhapsody after doing this, It goes back to asking me to install the plugin.
All of this makes me think that I MAY be using nswrapper incorrectly, if any experts on it could let me know, I would be very grateful.

---

### Post by hise0001 on 2007-10-24
garretwcox,

Thanks for your reply.  You were much more detailed than I for everyone's benefit.

You've described pretty much all of the steps that I've done and described the same errors and behaviors that I've seen.

Something I've done in troubleshooting is to enter "about : plugins" in the url field of firefox to see the summary of plugins that it recognizes.

It shows that the Rhapsody plugin is installed at that it is using the file "npwrapper.nprhapengine.so" so I think nspluginwrapper was used correctly.. It just must not work :mad:

I guess I'll have to figure out how to install firefox32.

--Hise

---

