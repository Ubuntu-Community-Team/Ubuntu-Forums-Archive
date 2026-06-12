---
title: "How to batch convert a folder with flacs to mp3?"
date: 2009-01-29
forum: x86 64-bit Users
---

### Post by cooperative on 2009-01-29
I'll have a folder with few hundreds of subfolders containing flacs. Over the years I have ripped all my cd's to flac and due to some limitiations at the moment I am forced to convert all flacs to mp3. Or actually What I need is for the flacs to be copied and converted into new folder with same structure where I have subfolders containing the new mp3. The all need to be @320 bits quality.

Structure:
```
Musicfolder 
- Band A 
   - CD 1 
   - CD 2

- Band B
   - CD 1 
   - CD 2
```

I will guess this folder holds 3000+ songs and doing this one folder at a time will take too much time so I need a smart script or commands that will help me do this.

Otherwise if there is any program that will let me do this that might also be an option. I could go either way for the software option, linux or windows software. 

Is there a simple! :D comandline tool that will let me do this? And what will I need to type to get it all converted at once?

Pls help this is something I should have fixed by friday because I am having people over and I need all those flacs as mp3 before the party starts.:D

**Edited:**
As you will see below I have a pearl script that might work. Thing is I am not a pearl programmer so I do not excactly understand what parameters to change in order for the script to do what I need. If there are any pearl gurus here plas take a look and point me in the right direction.

---

### Post by cooperative on 2009-01-29
I did find a pearl script, but I do not understand what this does. Can someone pls walk me though this?

```

#!/usr/bin/perl
# simple driver to convert flac files to mp3
# just drives flac and lame, mainly to allow
# wildcards and to remember options so I don't 
# have to. Assumes flac and lame are on path.
#
# Created on May 22, 2004
# Copyright (c) 2004, Pat Farrell, All rights reserved.
# This code will be released with a suitable Open Source
# license, probably BSD-like.
# 
# make it handle arguments the way Windows users expect.
use File::DosGlob 'glob';
use Getopt::Long;
use File::Basename;

my $help;
my $outspec;
my $quality = 2;
my $otherLameOptions;

    usage() if ( $#ARGV < 0 ); 
    GetOptions('help|?' => \$help, 'output=s' => \$outspec, 'quality=i' => \$quality, 
	'lame=s' => \$otherLameOptions);
    usage() if $help;

while ($anArg = shift(@ARGV)) {
    $anArg =~ s/(\s)/\\\1/g;	# quote any spaces before we glob
    @argfile = glob ($anArg);
    foreach $aFile (@argfile) {
	($basename, $dir, $ext) = fileparse($aFile, '\..*?');
	if ($ext =~ /.flac$/i ) {
	    $needQuotes = ($aFile =~ m/\s/) ? "\"" : "";
	    $outfn = (($outspec) ? $outspec :  $dir) . $basename . ".mp3"; 
	    $cmd = "flac -dcs " . $needQuotes . $aFile . $needQuotes   
	        . " | lame --silent -q " . $quality . " --tt " . $needQuotes . $basename . $needQuotes
		. " --resample 44100 " . $otherLameOptions . " - " 
		. $needQuotes . $outfn . $needQuotes ;
   	    print "$cmd\n";
	    $retval = system($cmd);
	}
	else {
	    print "$aFile will be ignored\n";
	}
    }
} 
sub usage {
    print "convert flac files to mp3\n";
    print "Usage:\n   flac2mp3.pl [-output=path] [-quality=[0-9]] [-lame=[lame-options]] {files}\n";
    print "     quality is passed straight to lame,\n";
    print "        -q 0:  Highest quality, very slow\n";
    print "        -q 9:  Poor quality, but fast.\n";
    print "     lame-options is passed straight to lame, this is nice for -vbr or bit rate options\n";
    print "note, the output path has to end with the directory separator character.\n";
    print "   \\ on Windows, \/ on linux, etc.\n";
    exit;
}


```

Will this do what I intend? or do I need to tweak or do some changes for this script?

---

### Post by crys on 2009-01-30
Try this one-liner:

for i in *.flac; do flac -c -d "$i" | lame -V3 - "$i".mp3; done

This works for me for all *.flac in one directory. To do this in all subdirs you'll have to use something like "find" or so in the loop.

Hope that helps,
Chris

---

### Post by cooperative on 2009-01-30
Thx will try this as soon as I am done with work today. I need all of my music on a portabale mp3 player and it will not accept flacs so I must convert them.

Well I guess this is as good a time as any to dig into pearl :p

---

### Post by SushiR on 2009-01-30
#!/bin/sh
#
for i in `find /mnt/mucke/ -name *.ogg`; do flac -c -d "$i" | lame -V3 - "$i".mp3;
done

---

### Post by slope on 2009-02-04
I believe what you need is this called [flac 2 mp.pl]("http://robinbowes.com/filemgmt/viewcat.php?cid=4")

This is not my work nor did I have anything to do with this script other then I have seen it hard at work several times and I liked the idea. This is as far as I know the work of

**Mr: Robin Bowes**


```

About flac2mp3
==============

flac2mp3 is a pearl script that will search for flac files within
a directory hierarchy and convert them all to mp3 format, creating a
matching directory structure in the process.

I wrote it as I have a large collection of flac files but need to
convert them to mp3 format for use with my iPod.

There are a few programs that can do basic file format conversion
but I found that it was hard to detect which files were new in my
flac collection and to convert just those files. I also find I update
the metadata in my flac files fairly often (when I spot mistakes, etc.)
and needed  a way to update just the tags rather than running the whole
conversion process again.

flac2mp3 can do this.

It can take a directory structure like this:

lossless
  |
  +--Coldplay
  |    |
  |    +--Parachutes
  |         |
  |         +-- 01 - Don't Panic.flac
  |             02 - Shiver.flac
  +--The Chameleons
       |
       +Script of the Bridge
          |
          +-- 01 - Don't Fall.flac
              02 - Here Today.flac

And produce a directory structure like this:

lossy
  |
  +--Coldplay
  |    |
  |    +--Parachutes
  |         |
  |         +-- 01 - Don't Panic.mp3
  |             02 - Shiver.mp3
  +--The Chameleons
       |
       +Script of the Bridge
          |
          +-- 01 - Don't Fall.mp3
              02 - Here Today.mp3

The command to do this is:

  flac2mp3.pl /path/to/lossless /path/to/lossy

Now, suppose I notice that I've spelled "coldplay" wrongly. I simply
use a tag editor to correct the flac files then run flac2mp3 again
to update the tags in the mp3 files:

  flac2mp3.pl --tags-only /path/to/lossless /path/to/lossy

Command-line options can be seen by typing "flac2mp3.pl" with no options:

  Usage: ./flac2mp3.pl [--quiet] [--debug] [--tagsonly] [--force] <flacdir>
<mp3dir>
    --quiet         Disable informational output to stdout
    --debug         Enable debugging output. For developers only!
    --tagsonly      Don't do any transcoding - just update tags
    --force         Force transcoding and tag update even if not required

Installation
============

As of v0.2.6 all non-standard perl modules are supplied in the archive.
Installation should be as simple as extracting the archive into a 
directory of your choice.

For example, on linux:

 # cd ~/bin
 # tar zxvf flac2mp3-0.2.6.tar.gz

On Windows, you can use Winzip or other utility to unzip the file and
extract the archive.

Mailing lists
=============

The following mailing lists are available:

List address: flac2mp3-announce@robinbowes.com
Description:  Read-only list for announcements
To subscribe: flac2mp3-announce-subscribe@robinbowes.com

List address: flac2mp3-devel@robinbowes.com
Description:  Developer discussion
To subscribe: flac2mp3-devel-subscribe@robinbowes.com

List address: flac2mp3-general@robinbowes.com
Description:  General user discussion
To subscribe: flac2mp3-general-subscribe@robinbowes.com

Please report any issues to robin-flac2mp3@robinbowes.com

Robin Bowes
August 2005

```

Enjoy!

---

