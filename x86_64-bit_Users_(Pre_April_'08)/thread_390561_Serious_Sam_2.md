---
title: "Serious Sam 2"
date: 2007-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by perky on 2007-03-22
G'day

I'm trying to get Serious Sam 2 to work on 64-bit Edgy.  I've followed[ someone's advice here]("http://forums.seriouszone.com/showthread.php?t=49869") about how to get the [native linux binaries]("http://files.seriouszone.com/download.php?fileid=1190") to work, and after following the advice in the second post, I encounter the following error:

```

./Bin/Linux-Dynamic-Release/Sam2: error while loading shared libraries: libopenal.so.0: wrong ELF class: ELFCLASS64

```
I have copied the 3 files mentioned in the above post, and made links, but it seems from my error message that I need 32bit versions of these libraries.

The libraries involved are libasound.so.2.0.0 libopenal.so.0.0.0 and libXxf86misc.so.1.1.0

Any ideas on how to do this without breaking my system? 

Thanks

---

### Post by saneone on 2007-03-22
Yes... Six steps:

1. Go there: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
2. Search for the packages u need (i386 versions!)
3. Download them
4. EXTRACT them, but DO NOT install them using dpkg or sth...
5. Copy libraries to /lib32 or /usr/lib32 (depends on where should they be)
6. Have fun :)

Yesterday i did this trick with Second Life and Mupen64 (Nintendo64 emulator)... Works like a charm...

---

### Post by perky on 2007-03-23
Thanks!!

The game loads now, but I've run into another problem. ](*,) 

When it comes to the 'create profile' screen, I can type in a name, but the finish button seems to have no effect, as well as clicking on the 'select' button in the bottom right.

Has anyone run into a similar problem?  I really don't want to boot into windows just to play a game, but it's starting to look like i'm going to have to :( ](*,)

I thought at first that it might be a permission problem - ie, the game didn;t have access to create/edit the profile file(s), but I've ruled this out after trying to run the game as root with same prob.

Please help if you have any knowledge in this area!

Cheers

---

### Post by fabertawe on 2007-03-24
> **perky said:**
> When it comes to the 'create profile' screen, I can type in a name, but the finish button seems to have no effect, as well as clicking on the 'select' button in the bottom right.

Has anyone run into a similar problem?  I really don't want to boot into windows just to play a game, but it's starting to look like i'm going to have to :( ](*,)

I had no problem creating a profile but have found it keeps getting corrupted, essentially leaving me without a save game option. So I have to play it under Windows anyway :( 

If you already installed it under Windows then try copying your existing profile over. This also worked for me initially until it became corrupted.

Paul

---

### Post by perky on 2007-03-24
> **fabertawe said:**
> I had no problem creating a profile but have found it keeps getting corrupted, essentially leaving me without a save game option. So I have to play it under Windows anyway :( 

If you already installed it under Windows then try copying your existing profile over. This also worked for me initially until it became corrupted.

Paul

Thanks for the advice.

I ended up installing it in Windows, creating a profile there, and copying it over and it worked.  Saving also seems to work.

From what you said about saving occasioanlly corrupting, it looks like it may be wise to incorporate a small backup script into the SS2 launcher.

If anyone's interested, insert the following at the top of the file RunSam2 (replace ~/Games/ss2 with the location of your ss2)

```

SSPATH=~/Games/ss2/Content/SeriousSam2
FILENAME=$SSPATH/ss-backup-$(date +%Y-%m-%d-%H-%M-%S).tgz
tar -cvf $FILENAME $SSPATH/PlayerProfiles/

```

Seems like the linux binaries still need a bit of work, but hopefully they will catch up!

Thanks again.

---

### Post by fabertawe on 2007-03-25
> **perky said:**
> From what you said about saving occasioanlly corrupting, it looks like it may be wise to incorporate a small backup script into the SS2 launcher. If anyone's interested...

Thanks for that, good Idea. I might give the Linux client another go now.

It's a great game but it sounds like they messed up their OpenGL implementation somewhere along the line. Still very playable though. 

Cheers ... Paul

---

### Post by go_beep_yourself on 2007-11-23
Does anyone know where instructions are for installing Serious Sam - The First Encounter in Ubuntu?

---

### Post by nicolam on 2008-01-05
you can get an installer for it here:
[http://liflg.org/?catid=6&gameid=71](http://liflg.org/?catid=6&gameid=71)

I've tried it, and it works just fine :)

pop in the disc, start the installer, and follow the instructions...
it's only a few clicks away!

---

### Post by soxs on 2008-01-05
I am sorry if this mismatches the thread question.. but wouldn't this little shiny package do the job.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
It will get the required 32 bit libraries for you und you'll have no trubble. I myself tested it and it workx like a charm.

Ok, HowTo:
Follow th linux beta installer readme.
When you are finished, try to start RunSam2 via terminal.
You will get some error messages about missing libraries <libname>
To get these 32bit libraries, simply use the getlibs tool.
```
getlibs <libname> 
```
Do this until there are no more missing libraries.

---

