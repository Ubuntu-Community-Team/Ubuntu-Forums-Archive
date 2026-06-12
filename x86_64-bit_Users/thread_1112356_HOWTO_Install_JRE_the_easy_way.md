---
title: "HOWTO Install JRE the easy way"
date: 2009-03-31
forum: x86 64-bit Users
---

### Post by loomsen on 2009-03-31
Hey folks.

Just thought I could share this.

So, I'm starting with this after everyone of us grabbed the x86_64 binary and saved it to a common folder, like i.e. /opt/java64 (This will be used as default)

> 
[color=red]docter[/opt/java64][/color] ls 
jre-6u13-linux-x64.bin
jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.bin
jre1.6.0_14
[color=red]docter[/opt/java64] [/color]

So, after downloading one of the above images and making it executable, a factual execution will install it into our current workdir (most likely to $pwd/jre1.6.0_14/). 
Now, lets grab java-common and equivs (we'll need the 2nd one in order to achieve our goals)

Aptitude search says it's:
> 
[color=red]docter[/opt/java64][/color]aptitude search java-common
p   java-common                     - Base of all Java packages   


```
sudo aptitude install java-common equivs
```

In fact it ships dummy packages you may use and build .debs out of to easily install java to your system, besides some docs, manuals and examples.

Here's a shot of what we are actually interested in:
[[img]http://www.ubuntu-pics.de/thumb/11784/screenshot_033_jcgYyN.png[/img]](http://www.ubuntu-pics.de/bild/11784/screenshot_033_jcgYyN.png)

If you aren't already in your installations PARENT directory, move there (in my case cd /opt/java64) and:
```

cp /usr/share/doc/java-common/dummy-packages/*.control . 

```
[color=green] Notice the dot at the end of the line.[/color]

Now, our directory should look sth like this:
> 
[color=red]docter[/opt/java64][/color] ls
java-compiler-dummy.control
java-virtual-machine-dummy.control
java1-runtime-dummy.control
java2-compiler-dummy.control
java2-runtime-dummy.control
jre-6u13-linux-x64.bin
jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.bin*
jre1.6.0_14/
[color=red]docter[/opt/java64][/color]


In your current WD, create a script with this in it:
```

#!/bin/bash

for fn in *.control
	 do equivs-build $fn
done

```

Name it foo_bar.sh. Save it, and make it executable with
```
chmod +x foo_bar.sh
```
Then type
```
./foo_bar.sh 
```
and let the magic happen :)

After some output, and a note that the pkges have been created in our current WD, you should see:
> 
[color=red]docter[/opt/java64][/color]ls
foo_bar.sh*
java-compiler-dummy.control
java-compiler-dummy_1.0_all.deb
java-virtual-machine-dummy.control
java-virtual-machine-dummy_1.0_all.deb
java1-runtime-dummy.control
java1-runtime-dummy_1.0_all.deb
java2-compiler-dummy.control
java2-compiler-dummy_1.0_all.deb
java2-runtime-dummy.control
java2-runtime-dummy_1.0_all.deb
jre-6u13-linux-x64.bin
jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.bin*
jre1.6.0_14/
[color=red]docter[/opt/java64][/color]


```
sudo dpkg -i *.deb
```
...to install them. :)

Enjoy

---

### Post by stchman on 2009-04-01
I just install openjdk.

---

### Post by loomsen on 2009-04-01
I don't need a DK, RE and I'm fine. And I somehow prefer suns JRE over OpenJDK JRE...

---

### Post by Yellow Pasque on 2009-04-02
Since you're running Jaunty/9.04, why didn't you just:
```
sudo apt-get install sun-java6-plugin
```
:confused:

---

### Post by loomsen on 2009-04-02
Humm, good point... I thought reading your post... But then I tried, it would get me 35MB, 150+MB for the source, creating even more dependencies. I'm not a fan of them tho, so I try and keep my PC with lowest possible dependencies.

And I use some partitions throughout multiple OS and installations. issueing dpkg -i *.deb is definetely advantageous facing a download of hunders of megabyte i dont want.

Guess that's why.

---

