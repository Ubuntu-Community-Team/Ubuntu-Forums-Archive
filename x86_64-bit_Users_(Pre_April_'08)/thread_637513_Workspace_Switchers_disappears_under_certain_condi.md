---
title: "Workspace Switchers disappears under certain conditions"
date: 2007-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anaximander Thales on 2007-12-11
I've done several searches since I've encountered this -- It's an annoyance that if I remember correctly started in Feisty -- and not found anything.

Here's the entire set-up:
This is all in XFCE4 -- I have not checked out KDE or Gnome because I am quite content with XFCE.  I like having my workspace switcher set up in a column instead of in a row.  I also go with three workspaces and love Auto-hiding panels.  So, panel is set for autohide.  Workspace switcher is set to 3 rows, number of workspaces is 3.  Panel hides, workspace switcher disappears.  It's still present on the panel -- it just isn't displaying.

I know it's present, because when I set the workspace to something other than 3 (2 or 4), the switcher comesback.  This happens when the number of rows in the switcher and the number of workspaces are equal.

# of WS......# of Rows......Result
2.................2.....................Invisible
3.................3.....................Invisible
4.................4.....................Invisible
3.................2.....................Visible
4.................3.....................Visible
4.................2.....................Visible

What's odd is that when the # of WS and # of Rows are equal and the Panel is NOT set to autohide, the switcher stays visible.  So, it seems there is something about the painting of the panel and the workspace switcher that causes this.

Like I said, this is an annoyance, but I was wondering if anyone has encountered this?  If so, have you found a solution to it?  If so, what is the solution?  Or do I need to put in a bug report, and where would I do that?

---

### Post by Anaximander Thales on 2007-12-15
bump

---

