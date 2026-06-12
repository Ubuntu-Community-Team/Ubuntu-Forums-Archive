---
title: "EQ2 map updater"
date: 2008-04-14
forum: Wine
---

### Post by javafiend on 2008-04-14
I've seen the perl script for updating EQ2's maps on the Wine appDB, but was wondering if anyone has gotten the map updater from [http://maps.eq2interface.com/]("http://maps.eq2interface.com/") working.

If not, can anyone explain how to make the perl script work?

Included for reference:
```

Updater for EQ2Map
by Stefan Klein on Monday December 10th 2007, 14:37
Hacked a small perl script to update EQ2MAP.
Edit $eq2mapdir to the full path of your installation, fix http in $baseurl.
use at own risk.

--------------------------------------------------------
#!/usr/bin/perl

use XML::Simple;

$eq2mapdir = ".. PATH TO WINEDIR .. drive_c/Program Files/Sony/EverQuest\ II/UI/EQ2MAP/";


$baseurl = "h t t p : / / maps.eq2interface.com/POI_files/";
$basefile = "extrafile_list.xml";

my $mainfile = `wget -q -O - $baseurl$basefile`;

my $ref = XMLin($mainfile, SuppressEmpty =>'');

foreach my $file (@{$ref->{'Extra'}}) {
if (-e $eq2mapdir . $file->{LocalPath} . $file->{FileName}) {
($md5, $filename) = split(/ /,`md5sum \"$eq2mapdir$file->{LocalPath}$file->{FileName}\"`);
if ("$file->{MD5}" eq "$md5" ) {
next;
}
}

print "downloading $file->{FileName}: \t ";

`wget -q -O \"$eq2mapdir$file->{LocalPath}$file->{FileName}\" \"$baseurl$file->{ServerPath}$file->{FileName}\"`;

print " finished\n";
}

```

---

