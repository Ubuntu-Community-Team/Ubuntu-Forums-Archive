---
title: "Skype phones and webcams for ubuntu"
date: 2006-09-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2006-09-04
hi i wanted to get a pair of webcams and skype phones or similar things to use to talk to my dad internationally.

hopefully through something free or gaim etc.

can anyone recommend good quality hardware, apps and also hardware that is good but quite cheap to buy still.

i need them to "just work" easy as possible because my dad won't know what he's doing over in spain otherwise!

any help is appreciated. thanks.

---

### Post by McMarley on 2006-09-04
logiteck ( [http://www.logitech.com/](http://www.logitech.com/) ) quikcams are pretty usefull and easy to use ( my dad and I use them to tralk via skype ). unless your father has never touched a computer before then he won't have any problems.

what else did you say you needed???

---

### Post by jonah1980 on 2006-09-04
will these also work with ekiga, or is skype better?

thanks, any recommendations on models etc?

also is the audio/mic ok as my dad's hearing isn't amazing!

and are webcams all usb or not? if so do you have to mic your sound in seperately?

thanks

---

### Post by zuser on 2006-09-04
As to microphone, I recommend getting headset and cam without mic.
I have been using skype for some time and believe that headphone is better unless you will have several participants and need the open conversation.

I dont believe skype for Linux supports cams yet. I think video is still a windo$ luxury. I dont know what other systems may be available that support video.

---

### Post by RAOF on 2006-09-04
> **zuser said:**
> ...
I dont believe skype for Linux supports cams yet. I think video is still a windo$ luxury. I dont know what other systems may be available that support video.

Ekiga (which was Gnome Meeting) supports video, and it's installed by default.  If your webcam works with V4L or V4L2 (Video 4 Linux - the linux video input api), it'll work with ekiga.

---

### Post by Relic2K on 2006-09-05
I use mainly AMSN, it has full webcam support and is compatible with the Windows Clients :) There is a new version out now that works great.

---

### Post by jonah1980 on 2006-09-07
thanks for all the suggestions, i'm still figuring out the best move.

turns out that my sister and brother in law have now also got skype on windows.

so is there anything i can use for ubuntu that's free, good and works easily with skype. and "just works" easily with hardware etc.

i first wanted to use ekiga cos myself and my dad have it preinstalled but this won't work with skype will it?

i've also decided the webcam is less important than the free phone calls, so in people experience would a headset/headphones and mic be best with linux or the usb telephones you can get? maybe i can add the webcam later, is this possible. sorry for my ignorance, most of this communications technology is totally new to me. thanks for advice.

---

### Post by Rhubarb on 2006-09-07
Skype and Ekiga are completely incompatible.
Skype is proprietry (and hence evil)
Ekiga follows nice SIP protocol voip standards.

If it's of any help, you can get yourself an ekiga voip account (I think it's a trial account - not sure), or you can sign up to FWD and get yourself a free voip account that works with ekiga.
The windows client on FWD's site is really easy to setup.
Ekiga isn't too hard to setup using FWDs service.
[www.freeworlddialup.com]("http://www.freeworlddialup.com")

---

### Post by jonah1980 on 2006-09-07
so basically myself and my dad can use ekiga as planned and my sister etc on windows can use this fwd thingi to talk to us through?? what i mean is if we use ekiga, can windows users use free software also to talk to us instead of skype?

---

### Post by Circus-Killer on 2006-09-12
add the following to your /etc/apt/sources.list:
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

and then:
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install skype

now you can talk to your sis on skype.

---

### Post by jonah1980 on 2006-09-12
thanks but this didn't work for me

seems there is no 64bit skype repository as it says not found when i add the above to my source list

---

### Post by Circus-Killer on 2006-09-12
ah, didnt realise you were on 64bit. sorry. its a pity, cos i wanna know if skype phones generally work in linux. dont wanna waste that money on something i cant use :|

---

### Post by John.Michael.Kane on 2006-09-12
Your best bet is to get a good headset with mic,and if you need a [Linux Web Camera]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras?highlight=%28webcam%29") look at the list in the link.

Since i had no need for a webcam i just ordered a headset with mic.

---

### Post by Circus-Killer on 2006-09-12
yeh, but the headset aint as cool as a cordless skype phone that can use normal pstn lines as well for regular calls.

---

### Post by jonah1980 on 2006-09-13
ended up going for skype. struggled with ekiga and also wengo - couldn't get either working right - and ekiga had soundcard problems.

but skype worked first time no worries, so gonna use that for now. thanks for all advice, i might look into webcams in time also.

---

### Post by cvmostert on 2006-10-25
Sadly I only got to this forum now... skype is ok... i am using [www.voipbuster.com](www.voipbuster.com) account on ekiga, and talk to anyone in windows... i suppose it would be the same with freeworld dialup. x-lite is a free windows voip program that can easily be used.

ciao.

---

### Post by fabertawe on 2006-10-25
> **cvmostert said:**
> Sadly I only got to this forum now... skype is ok... i am using [www.voipbuster.com](www.voipbuster.com) account on ekiga, and talk to anyone in windows... i suppose it would be the same with freeworld dialup. x-lite is a free windows voip program that can easily be used.

ciao.

Do you use Ekiga with voipbuster for landline calling? If so, is this difficult to set up?

Cheers ... Paul

---

### Post by cvmostert on 2007-02-08
> **fabertawe said:**
> Do you use Ekiga with voipbuster for landline calling? If so, is this difficult to set up?

Cheers ... Paul

I use Ekiga with voipbuster sip setup... it is relatively easy.. just have to fill in the account..

Ok,  in Ekiga, 
1. press Ctrl+E to add an account
2. press Add
3. fill in your voipbuster details:
account name; (mine is Voipbuster)
registrar: sip.voipbuster.com (some people use sip1.voipbuster.com)
user: your_voipbuster_username
password: your_password

now you have to buy credit... and start calling to either free or non-free countries to land line.

there are other variations of this provider  [www.voipcheap.com](www.voipcheap.com) and they call free to different countries. 

Hope this helped.

---

### Post by fabertawe on 2007-02-08
> **cvmostert said:**
> I use Ekiga with voipbuster sip setup... it is relatively easy.. 
[snip]
Hope this helped.

Thanks for the info. I've been using Skype for landline calls as they gave me 6 months free in the UK. It's good to have options though.

Paul

---

