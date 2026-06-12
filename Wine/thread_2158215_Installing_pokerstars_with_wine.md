---
title: "Installing pokerstars with wine"
date: 2013-06-28
forum: Wine
---

### Post by Kennethvp on 2013-06-28
Hi Linix community

I am new to linux and therefor I have a rookie question i hope someone will be kind enough to answer:D

I have installed the program called "wine" from software center and downloaded pokerstars program.

Afterwards I want to follow the recormendations presented here:

[http://www.all-about-poker.com/poker-software/linux-wine/pokerstars.php](http://www.all-about-poker.com/poker-software/linux-wine/pokerstars.php)

The first step works fine but then they say:


[LIST=1]
[*]Copy the PokerStars setup file to your Wine directory
[/LIST]
 			 			
:~> cp /home/user/PokerStarsInstall.exe /home/user/.wine

When i do this i get the following messages:

kenneth@ubuntu:~$ cd .wine
[email]kenneth@ubuntu:~/.wine[/email]$ cp /home/kenneth/pokerstarsInstall.exe /home/kenneth/.wine
cp: cannot stat `/home/kenneth/pokerstarsInstall.exe': No such file or directory
[email]kenneth@ubuntu:~/.wine[/email]$ 

Can someone please tell me what i am doing wrong here?

(Sorry for my bad english - I am dane)

---

### Post by Impavidus on 2013-06-28
Watch the capitals. Linux is case sensitive.

Also, are you sure you downloaded the setup file to your home directory?

BTW, your english is OK. I've seen much worse here.

---

### Post by Kennethvp on 2013-06-28
Hi

It has nothing to do with case sensitive letters. Just tried it.

I think I have downloaded PokerStarsInstallDK.exe in /home/kenneth/Downloads

I cant see where i have downloaded wine? I can just see i have it from Ubuntu Software Center.

In "Dash Home" i found it as an application but not as a file & folders like pokerstars - could this be it?

Or can you search for the location?

---

### Post by Impavidus on 2013-06-28
If you installed wine from the software centre it should be properly installed. It's somewhere in your system (in /usr to be precise) and right where it ought to be.

Now, in the terminal (note that you can do this without terminal, but giving terminal instructions is clearer):```
#Make sure you are in your home directory (you should be there by default)
cd
#Create the .wine directory if it's not there yet
mkdir .wine
#Go to the .wine directory
cd .wine
#Copy the installer there
cp ~/Downloads/PokerStarsInstallDK.exe .
#Start setup
wine ./PokerStarsInstallDK.exe

```Watch the spaces and tilde (~).

---

### Post by Kennethvp on 2013-06-28
I think I have the wine directory because when i type: 
cd .wine
I get:
kenneth@ubuntu:~$ cd .wine
But when i then type:

cp ~/Downloads/PokerStarsInstallDK.exe

I get the following message:

[email]kenneth@ubuntu:~/.wine[/email]$ cp ~/Downloads/PokerStarsInstallDK.exe
cp: missing destination file operand after `/home/kenneth/Downloads/PokerStarsInstallDK.exe'
Try `cp --help' for more information.

When i type: cp --help

I get:

[email]kenneth@ubuntu:~/.wine[/email]$ cp --help
Usage: cp [OPTION]... [-T] SOURCE DEST
  or:  cp [OPTION]... SOURCE... DIRECTORY
  or:  cp [OPTION]... -t DIRECTORY SOURCE...
Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.

Mandatory arguments to long options are mandatory for short options too.
  -a, --archive                same as -dR --preserve=all
      --attributes-only        don't copy the file data, just the attributes
      --backup[=CONTROL]       make a backup of each existing destination file
  -b                           like --backup but does not accept an argument
      --copy-contents          copy contents of special files when recursive
  -d                           same as --no-dereference --preserve=links
  -f, --force                  if an existing destination file cannot be
                                 opened, remove it and try again (redundant if
                                 the -n option is used)
  -i, --interactive            prompt before overwrite (overrides a previous -n
                                  option)
  -H                           follow command-line symbolic links in SOURCE
  -l, --link                   hard link files instead of copying
  -L, --dereference            always follow symbolic links in SOURCE
  -n, --no-clobber             do not overwrite an existing file (overrides
                                 a previous -i option)
  -P, --no-dereference         never follow symbolic links in SOURCE
  -p                           same as --preserve=mode,ownership,timestamps
      --preserve[=ATTR_LIST]   preserve the specified attributes (default:
                                 mode,ownership,timestamps), if possible
                                 additional attributes: context, links, xattr,
                                 all
      --no-preserve=ATTR_LIST  don't preserve the specified attributes
      --parents                use full source file name under DIRECTORY
  -R, -r, --recursive          copy directories recursively
      --reflink[=WHEN]         control clone/CoW copies. See below
      --remove-destination     remove each existing destination file before
                                 attempting to open it (contrast with --force)
      --sparse=WHEN            control creation of sparse files. See below
      --strip-trailing-slashes  remove any trailing slashes from each SOURCE
                                 argument
  -s, --symbolic-link          make symbolic links instead of copying
  -S, --suffix=SUFFIX          override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory    treat DEST as a normal file
  -u, --update                 copy only when the SOURCE file is newer
                                 than the destination file or when the
                                 destination file is missing
  -v, --verbose                explain what is being done
  -x, --one-file-system        stay on this file system
      --help     display this help and exit
      --version  output version information and exit

By default, sparse SOURCE files are detected by a crude heuristic and the
corresponding DEST file is made sparse as well.  That is the behaviour
selected by --sparse=auto.  Specify --sparse=always to create a sparse DEST
file whenever the SOURCE file contains a long enough sequence of zero bytes.
Use --sparse=never to inhibit creation of sparse files.

When --reflink[=always] is specified, perform a lightweight copy, where the
data blocks are copied only when modified.  If this is not possible the copy
fails, or if --reflink=auto is specified, fall back to a standard copy.

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

As a special case, cp makes a backup of SOURCE when the force and backup
options are given and SOURCE and DEST are the same name for an existing,
regular file.

Report cp bugs to [email]bug-coreutils@gnu.org[/email]
GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
General help using GNU software: <http://www.gnu.org/gethelp/>
For complete documentation, run: info coreutils 'cp invocation'

---

### Post by Mark Phelps on 2013-06-28
> But when i then type:

cp ~/Downloads/PokerStarsInstallDK.exe

That's a "copy" command -- as in copy [from] [to]

All you provided was the [from], you provided no [to]  (the destination)

What is it you're really trying to do such that you are using this command?

---

### Post by Frogs Hair on 2013-06-28
Moved to Wine sub-forum.

---

### Post by Kennethvp on 2013-06-28
ohh i see

I am trying to Copy the PokerStars setup file to my Wine directory

What must i write as command then?

---

