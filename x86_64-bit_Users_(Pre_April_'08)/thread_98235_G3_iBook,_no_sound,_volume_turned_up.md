---
title: "G3 iBook, no sound, volume turned up"
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Scrufdog on 2005-12-02
Under sound preferences it has PowerMac Tumbler as default sound card, and nothing else is selectable.

This is a white G3 iBook

---

### Post by wishyjr on 2005-12-05
ive got pretty much the same laptop (g3 ibook) but my sound doesnt seem to work at all, i do however get 'pops and scratches' whenever an error or message shows up.

are there any specific sound drivers for built-in mac sound stuff? i'd be keen to get my built-in mic weorking for skype or something like that too but it'd be nice if it at least played music.

multimedia system selector is showing my output as: ALSA and my input as: OSS. On clicking the test button i get an error
**Failed to construct test pipeline for '(name of driver here)'** Any thoughts?

---

### Post by tmeier on 2005-12-08
I am running a G4 powerbook, but things might be similar.

Have you tried double clicking on the speaker icon up by the clock.  This brings up the volume control window.  click on File and change device and make sure it is selected on the Alsa Mixer.   Then go to EDIT and Preferences.  Scroll through the list of tracks to be visible and put a checkmark next to DRC if it is not already there.  click OK.  Then select the switches tab(in the volume control window) and take the checkmark out of the DRC box.  This may give you sound.  That is how it worked for me.  Might be different on a G3 ibook, but I'm guessing not.  I hope this helps.

---

### Post by deathshadow on 2005-12-12
Under Breezy - in my experience at least on one of the Clamshell iBooks it's no longer called "DRC"

Go into the mixer and choose [COLOR="DarkRed"]edit > preferences[/COLOR] and make sure the [COLOR="#8b0000"]Deemphasis[/COLOR] and [COLOR="#8b0000"]Power Amplifier[/COLOR] boxes are checked. This does NOT have an effect on the sound YET, but makes a separate TAB called "Switches"

Check both the [COLOR="#8b0000"]Deemphasis[/COLOR] and [COLOR="#8b0000"]Power Amplifier[/COLOR] boxes on that new tab, and you are good to go.

The reason you get weak crackling noise is the internal amplifier off. The sound is identical to what happens when you plug unpowered speakers into a line output.

---

### Post by stitch on 2005-12-13
For Deathshadow: where is the mixer ?
I cannot find the settings in the volume panel.

Thanks

Stitch

---

