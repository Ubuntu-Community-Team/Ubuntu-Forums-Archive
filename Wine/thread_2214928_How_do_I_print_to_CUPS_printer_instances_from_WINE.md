---
title: "How do I print to CUPS printer instances from WINE?"
date: 2014-04-03
forum: Wine
---

### Post by EarlsFurniture on 2014-04-03
I have a business app that currently runs in XP that prints two copies of a document(an invoice), the first to one "printer" with certain settings, and the second copy to the same physical printer, but using different settings. (namely, a second paper tray and a different watermark)

I might have a lead on how to post-process the watermark part (which it seems Linux can't handle out of the box) via combining pdf files and conversions back and forth to PostScript using a CUPS filter.

I also have discovered how to create separate printer instances via CUPS cli, ala lpoptions.

Since the instances do not show up as separate selectable printers in any GUI or printing dialog in Ubuntu, I can't seem to find a way other than cli, to print to the separate  instances. This also means I can't see the instances and select them in my Windows software through WINE.

What I want to accomplish is this:

copy 1 prints to instance "Customer Copy" that pulls only from tray 1 (pink paper), and adds a watermark "Customer Copy" to the printout.
copy 2 prints to instance "Merchant Copy" that pulls only from tray 2 (yellow paper), and adds a watermark "Merchant Copy" to the printout.

Eventually, as I run out of pre-printed forms, I'll add the required graphics as part of the 'watermark' process so I can start with blank colored paper and get the desired result. But that's a year or so down the road till I'll need to get that fancy.

The software I'm using only allows me to select a printer to send the file to. I cannot send an lp or lpr command.

From what I can tell, I either need to make the separate printer instances visible and availble via GUI in Ubuntu and/or the CUPS web interface, or, I need a way to create a "printer" that really is a one-line script with the proper lp/lpr command that sends the file to the instance.

Any clues?

---

