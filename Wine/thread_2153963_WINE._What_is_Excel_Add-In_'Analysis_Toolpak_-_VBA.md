---
title: "WINE. What is Excel Add-In 'Analysis Toolpak - VBA' for? Can't install it on Ubuntu!"
date: 2013-06-13
forum: Wine
---

### Post by ClarkH85 on 2013-06-13
I run Excel 2007 on Ubuntu 12.04 using Wine. I've installed some Excel Add-ins which I know I need: **Solver** and **Analysis ToolPak**. These work totally fine. I also sometimes write macros in Excel, so I'm in Visual Basic. So far, Visual Basic seems to work fine too. However, there is an Excel Add-In that I'm trying to install, called **Analysis ToolPak - VBA**, which crashes Excel every time I try to install it. 

First of all, I'm wondering if I even need this add-in? What does it do?

Anyway, if I need to use it, how can I install it? 

Thanks!

---

### Post by QIII on 2013-06-13
Hello!

The Analysis Pack provides a bunch of advanced statistical, math and engineering functionality to use in VBA modules behind your spreadsheets.

Unless you are doing some pretty heaving lifting with your spreadsheets and you plan to write some heavy code in VBA, you are not likely to need it.  

Occasionally Actuaries ask me to do stuff for them in VBA behind their complex spreadsheets. Shudder.   After I get out my golden crucifix and sprinkle my computer with Holy Water so that I can actually work in Excel, I've never had the need for anything in the toolpack.

Cheers.

---

### Post by Bucky Ball on 2013-06-13
*Thread moved to **Wine**.*

---

### Post by texaswriter on 2013-08-13
I also use Excel 2007 through WINE (using Crossover). The following works fine with me (and I have tested features): 

Click Office button (circular menu button in top left of excel)
Click "Excel Options" at buttom of menu that appears
Click "Add-Ins" in left-hand pane
At the bottom of the page you will see where it says "Manage:" "Excel Add-ins". Click "Go..."
Check the box next to "Analysis ToolPak" and "Analysis ToolPak - VBA". ONLY SELECT THESE ONES. I HAVE NOT TESTED OTHERS.
Click "OK".
Allow the "Office Update" dialog box finish its work. 
You may need to save your file, close excel, and re-open excel to use the new features. 
Next time you use excel, click on the "Data" tab in the ribbon. You will see there is a section here labeled "Analysis" with an icon labeled "Data Analysis".  Clicking this button will bring up a dialog box allowing you to select various data analysis tools.

---

