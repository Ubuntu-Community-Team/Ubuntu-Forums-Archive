---
title: "Vlc stops playing music suddenly"
date: 2009-07-04
forum: x86 64-bit Users
---

### Post by binskipy2u on 2009-07-04
after an hour, maybe 2, sometimes 1/2 hour.. itll stop in the middle of a song.. and then i hvae to close it, can NOT RESTART IT, then i click on amarok, it will NOT OPEN.. i have to REBOOT to listen to music again..
what the heck is going on???"

HELPPPPPPPPPPPPPPPP this is annoying

and yes i have every codec, multimedia dependency, and it worked on 3 other distros w/o this issue???

---

### Post by jocko on 2009-07-04
> **binskipy2u said:**
> after an hour, maybe 2, sometimes 1/2 hour.. itll stop in the middle of a song.. and then i hvae to close it, can NOT RESTART IT, then i click on amarok, it will NOT OPEN.. i have to REBOOT to listen to music again..
what the heck is going on???"

HELPPPPPPPPPPPPPPPP this is annoying

and yes i have every codec, multimedia dependency, and it worked on 3 other distros w/o this issue???
Sounds like either pulseaudio is crashing or something else is tying up the sound card.
Next time it happens, try to run this in a terminal:
```
pulseaudio -k
pulseaudio -D &
```

---

