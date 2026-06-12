---
title: "Ping for Counter Strike"
date: 2008-08-13
forum: Wine
---

### Post by connorh123 on 2008-08-13
I'm running counter strike with ubuntu 8.04 and wine 1.1.2. I've been having some lag problems in game. Is there anyway to fix this?:confused:

---

### Post by connorh123 on 2008-08-28
Guess not.

---

### Post by dankster117 on 2008-08-29
Have you applied the wine registry tweak? it dramatically helps alot of games such as WoW and halflife 2.

```
a. Find this key HKEY_CURRENT_USER\Software\Wine\
b. Highlight the wine folder in the left hand pane by clicking left on it.  The icon should change to an open folder
c. Right-click on the wine folder and select [NEW] then [KEY]
d. Replace the text New Key #1 with OpenGL
e. Right-click in the right hand pane and select [NEW] then [String Value]
f. Replace New Value #1 with DisabledExtensions (Notice it&#8217;s case sensitive!)
g. Then double click anywhere on the line, a dialog box will open.
h. In the value field type GL_ARB_vertex_buffer_object
```

---

### Post by Brynster on 2008-09-01
Also what hardware specs are you running?

---

