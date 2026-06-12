---
title: "gDesklets buildt from source, works but doesn't remember positions"
date: 2007-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by DracoPsycho on 2007-05-07
As it is said in the title. Package from repos doesn't work so I buildt gDesklets from source and everything is fine except few of desklets won't remember their positions so I have to drag them again when gDesklets restarts. I wanted to ask if someone else encountered this problem? Desklets are from FTB family, but I remember that at 6.10 desklets remembered their positions.

---

### Post by jamesford on 2007-05-07
in edgy i had this problem, hte solution was tpo make sure gdekslets started before beryl/compiz with a startupscript like

gdesklets
sleep 6s
beryl-manager

---

### Post by DracoPsycho on 2007-05-07
That might be the case, thanks for advice :) I'll check it out when I'll be home.

---

### Post by jamesford on 2007-05-07
or maybe gdesklets had to start after beryl...i dont really remember. try both :)

---

