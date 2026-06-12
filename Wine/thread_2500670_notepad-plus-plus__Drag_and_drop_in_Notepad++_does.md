---
title: "notepad-plus-plus | Drag and drop in Notepad++ does not work"
date: 2024-09-08
forum: Wine
---

### Post by nectarinebandit on 2024-09-08
Problem:

When running Notepad++ version 8.6.9, I cannot drag and drop text files to the GUI.

Solution:

If you downgrade to an older version, e.g. 8.6.7, drag and drop works normally.

```

$ snap list notepad-plus-plus --allName

Version  Rev  Tracking       Publisher  Notes
notepad-plus-plus  8.6.7    405  latest/stable  mmtrt      disabled
notepad-plus-plus  8.6.9    408  latest/stable  mmtrt      -

$ sudo snap revert notepad-plus-plus --revision 405

notepad-plus-plus reverted to 8.6.7

```

Another comment. Drag and drop works as long as you drag the file across the top toolbars. If you drag and drop the file anywhere else, such as where the lines and text are displayed, this will not work. Only drag and drop to the top toolbars.

---

