---
title: "Hardy: can't use ./ or sh to run programs"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by ziggyw00t on 2008-04-25
I'm using Hardy 64 bit and everything was working fine in gusty 64 bit. Now when I try to run program.sh or executable files that worked before I get various errors. Take ut2004 for example (unreal tournament 2004):

ziggy@heroinhardy64:/media/CLOSET/GAMES/UT2K4$ ./ut2004
exec: 50: ./ut2004-bin: not found
exec: 50: ./ut2004-bin: not found

or stepmania

ziggy@heroinhardy64:~/StepMania-3.9$ ./stepmania
bash: ./stepmania: No such file or directory

ziggy@heroinhardy64:~/StepMania-3.9$ sh stepmania
stepmania: 3: cannot open Of]P^.gjE&#65533;gb: No such file
CH&#65533;: not foundRdz&#65533;*&#65533;b&#65533;=
stepmania: 3: q77C9&#65533;: not found
stepmania: 3: K2&#65533;.Ub_S^AY&#65533;6&#65533;T&#65533;;N]&#65533;Xj_Y\&#65533;&#65533;V&#65533;Mk&#65533;P08P&#65533;X&#65533;e,8)@&#65533;_&#65533;F[??N?&#65533;_3a&#65533;d&#65533;G&#65533;2F: not found
stepmania: 2: Syntax error: word unexpected (expecting ")")

I'm not a total newb and I'm completely dumbfounded. Please help. Thanks.

---

### Post by no1wantdthisname on 2008-04-26
Try bash instead of sh.

---

### Post by ziggyw00t on 2008-04-26
ziggy@heroinhardy64:~/StepMania-3.9$ bash stepmania
stepmania: stepmania: cannot execute binary file

Nope. :mad:

---

### Post by Pancetilla on 2008-04-26
Are they still executable (green coloured)?

If they're not sudo chmod +x them.

sudo chmod +x program.sh

Or maybe you're trying to execute 32 bits only programs. In that case, make sure you've got ia-lib32 package installed. Maybe it was removed when upgrading for some reason.

---

### Post by Cappy on 2008-04-26
```
chmod +x stepmania
./stepmania
```

stepmania does not run with "sh" or "bash", it's not a script.

> 
ziggy@heroinhardy64:/media/CLOSET/GAMES/UT2K4$ ./ut2004
exec: 50: ./ut2004-bin: not found
exec: 50: ./ut2004-bin: not found


indicates that the script can not find ut2004-bin (which is in the ./System directory). Either the path to the System directory is changed or it uses a variable that you lost. Post the script "ut2004" and I'll do it.

---

### Post by ziggyw00t on 2008-04-26
#!/bin/sh
#
# ut2004 startup script
#

# Function to find the real directory a program resides in.
# Feb. 17, 2000 - Sam Lantinga, Loki Entertainment Software
FindPath()
{
    fullpath="`echo $1 | grep /`"
    if [ "$fullpath" = "" ]; then
        oIFS="$IFS"
        IFS=:
        for path in $PATH
        do if [ -x "$path/$1" ]; then
               if [ "$path" = "" ]; then
                   path="."
               fi
               fullpath="$path/$1"
               break
           fi
        done
        IFS="$oIFS"
    fi
    if [ "$fullpath" = "" ]; then
        fullpath="$1"
    fi

    # Is the sed/ls magic portable?
    if [ -L "$fullpath" ]; then
        #fullpath="`ls -l "$fullpath" | awk '{print $11}'`"
        fullpath=`ls -l "$fullpath" |sed -e 's/.* -> //' |sed -e 's/\*//'`
    fi
    dirname $fullpath
}

# Set the home if not already set.
if [ "${UT2004_DATA_PATH}" = "" ]; then
    UT2004_DATA_PATH="`FindPath $0`/System"
fi

LD_LIBRARY_PATH=.:${UT2004_DATA_PATH}:${LD_LIBRARY_PATH}
export LD_LIBRARY_PATH

# Let's boogie!
if [ -x "${UT2004_DATA_PATH}/ut2004-bin" ]
then
	cd "${UT2004_DATA_PATH}/"
	exec "./ut2004-bin" $*
fi
echo "Couldn't run UT2004 (ut2004-bin). Is UT2004_DATA_PATH set?"
exit 1

# end of ut2004 ...

###################################################################

I'm thinking I need the 32 bit libraries for stepmania. I'll post back when I know what's going on for sure.

---

### Post by Cappy on 2008-04-26
```
sudo apt-get install ia32-libs
```

---

### Post by ziggyw00t on 2008-04-26
I have ia32-libs installed. Now I'm getting somewhere:

ziggy@heroin64:~/Desktop/StepMania-3.9$ ./amd64-wrapper.sh
./stepmania: error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory
ziggy@heroin64:~/Desktop/StepMania-3.9$ ./stepmania
./stepmania: error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory

amd64-wrapper.sh is for running the 32bit program in a 64bit environment. It worked great in gusty but now I get the above error about missing the libvorbisfile which is installed. 

Somewhere else I read that I may need to make a symlink  so it can find the file. How do I do that?

---

### Post by Cappy on 2008-04-26
Install getlibs from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

and use
```
getlibs ~/Desktop/StepMania-3.9/stepmania
```

Also, can you check to see if ut2004 is giving a different error now?

---

### Post by ziggyw00t on 2008-04-26
Both stepmania and ut2004 are working now! I've given you thanks!

I found the post about getlibs and tried it before but it just sat and didn't do anything...I tried it again and it worked. Who knows.

---

