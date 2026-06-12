---
title: "Monkey's audio problem on 64-bit?"
date: 2008-08-22
forum: x86 64-bit Users
---

### Post by logos34 on 2008-08-22
I hate .ape/Monkey's Audio codec (proprietary + the compression ratio is only slightly better at the cost of much higher cpu overhead), but I'm running into all too many of them in torrents these days.  I need the decoder to convert to flac.  Otherwise I wouldn't bother. 

I can't seem to compile mac-3.99-u4-b5...keep getting error about libmac.so file after make install.  

What am I doing wrong?  The README file explicitly says:
> 
Since 3.99 update 4 build 5, mac-port has support for AMD64.But elsewhere I read this:
> 

[http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/](http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/)

[LIST=1]
[*]            [Conor]("http://www.conorschaefer.com/blog/")
                                          Posted March 13, 2008 at 5:47 am | [Permalink]("http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/#comment-3052")              
             This is truly a magnificent post, I&#8217;ve googled it a thousand times and have it bookmarked.
 However, do you know whether there&#8217;s any hope for 64-bit users? Your guide worked perfectly when I was still running i386, but now that I&#8217;m on 64-bit, is all hope lost for me? The deb you posted of course won&#8217;t install&#8230;
[/LIST]
...

[LIST=1]
[*]             [IMG]http://www.gravatar.com/avatar/?s=32&d=identicon[/IMG]            Arrgoss
                                          Posted June 21, 2008 at 9:25 pm | [Permalink]("http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/#comment-3070")              
             Hi, thanks for the guide!
As Conor, I&#8217;d like to install it in a 64-bit machine. Any suggestion how to do it?
[*]             [IMG]http://www.gravatar.com/avatar/111ae702156920baf2febff89fd6629c?s=32&d=identicon[/IMG]            [robin]("http://r081n.com/")
                                          Posted June 29, 2008 at 10:08 pm | [Permalink]("http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/#comment-3072")              
             and here&#8217;s one more request for 64bit systems&#8230;
[*]             [IMG]http://www.gravatar.com/avatar/104eb109dc4b7f877880e27b12e2f3a2?s=32&d=identicon[/IMG]            [heliologue]("http://heliologue.com/")
                                          Posted July 11, 2008 at 2:33 pm | [Permalink]("http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/#comment-3074")              
             Those of you looking for 64-bit debs of libmac and monkeys-audio (for Hardy), look no further than [this guy&#8217;s PPA]("https://launchpad.net/%7Egx/+archive").
 Pre-hardy, there&#8217;s always [Morgoth]("http://morgoth.free.fr/ubports/")
[*]
[/LIST]
Until I manage to install mac-3.99 I can't convert directly, or with pacpl (Perl audio converter) or shntool or any [scripts.]("http://www.gomellow.com/?p=24")

I can use K3bmonkey'saudio-plugin or MediaCoder (wine), but there appears to be a problem with the resulting flac files not fast-forwarding in media player (any).  So I have to expand to .wav, then manually run flac from cli.  But it would be a lot easier if I could convert directly in one step.

any help appreciated!

---

### Post by logos34 on 2008-08-27
bump.  still looking for an answer

edit: nevermind--I converted Fedora x86_64 mac .rpm with alien...Installed ok, testing it out now...

---

### Post by logos34 on 2008-08-28
well, I guess not many people in this forum work with Monkey's audio or know much about it, but for the record I was able get it to work--partly: it seems there is one thing I cannot do, which is to split an .ape image into individual APE files--other formats work though (go figure).  It will not accept piped commands from shntool (shnconv) when the .ape output is specified, even though I went to the trouble of compiling the prepatched version (-s4) with the shntool option:

> 1) obtain source code

[COLOR=Blue]  a) grab the pre-patched sources:

    % download mac-3.99-u4-b5-s4.tar.gz
    % gunzip < mac-3.99-u4-b5-s4.tar.gz | tar xf -
    % cd mac-3.99-u4-b5-s4[/COLOR]

  OR

  b) grab the original sources and patch them:

    % download mac-3.99-u4-b5.tar.gz, mac-3.99-u4-b5-s4.patch
    % gunzip < mac-3.99-u4-b5.tar.gz | tar xf -
    % cd mac-3.99-u4-b5
    % patch -p1 < ../mac-3.99-u4-b5-s4.patch

2) compile and install

  a) for unix targets:

    [COLOR=Blue]% CXXFLAGS="-DSHNTOOL" ./configure
  [COLOR=Black]  (Mac users only):  % perl -pi -e "s/-all_load//g" libtool[/COLOR]
    % make[/COLOR]
    % make install

I still get errors with either of thee commands:

$ shnsplit -o -f ape sample.cue sample.ape


$ cuebreakpoints sample.cue | shnsplit -o ape sample.ape

(Another thing I noticed is that calling mac directly to decode to wavs takes more
than twice as long as K3b mac plugin.  Odd.)

But then splitting to .ape tracks was never my goal, but it would be nice if things
worked as they should.

After all this I have come to the conclusion that the fastest way is to simply use K3b 
to read the ape .cue sheet and decompress to .wavs, then run 

flac -8 *.wav && rm *.wav

done.

---

### Post by jbrown96 on 2008-08-28
I had to convert .ape a while ago and could not get anything working. However, I was able to use foobar in Wine, which isn't a good solution but it should get the job done.

---

### Post by logos34 on 2008-08-28
Yeah, I have foobar too, and dBpoweramp music converter.  But I want to know how to do all this in naive linux apps, preferably from the cli.  Ape is such a pain in the a** to work with in linux...The developers must have something against FOSS, because all they have is windows .exe on their site, don't even mention linux.  It does have a better compression ratio than flac (though only about 7% tops in my experience at the -c5000 insane setting), but the cpu overhead is just ridiculous trying to play one and it takes forever to decompress compared to flac.

With all the bandwidth we have now  really wish people would quit rolling their cds into .ape images to save a few MBs...flac is better

---

### Post by logos34 on 2008-09-03
Update:

For anyone that's interested, I found out at the Hydrogenaudio forums (from the shntool dev no less) that only the newer patched mac-3.99 (compiled with appropriate options) handles piped commands from shnsplit.

Also, my problem compiling mac was apparently due to something checkinstall was doing.  Just doing ./configure && make && sudo make install was enough.

I also replaced the 3.0.3 .deb version of shntool with the latest 3.0.8 (no deb for that yet unfortunately, so you need to compile it)

So now I can easily convert/split ape images from CLI (only thing is that shntool does not support lossy formats like mp3 or ogg)

---

### Post by Helekryl on 2009-09-22
For x64 users: here's a good repository with monkey's audio for amd64 (other architectures, of course, are alse included).

[COLOR="Blue"][http://ppa.launchpad.net/g-christ/ppa/ubuntu/](http://ppa.launchpad.net/g-christ/ppa/ubuntu/)[/COLOR]

A set of commands to install x64 mac from this repo (for Jaunty, replace the distro name if needed):


Open the sources list
```
sudo gedit /etc/apt/sources.list
```

Append the following line to the end of the file
```
deb http://ppa.launchpad.net/g-christ/ppa/ubuntu jaunty main
```

Then add the security key, update the packages and install monkey's audio
```
gpg --recv-keys FB34808D7ED779F6
gpg --export --armor FB34808D7ED779F6 | sudo apt-key add -
sudo apt-get update
sudo apt-get install mac

```

---

