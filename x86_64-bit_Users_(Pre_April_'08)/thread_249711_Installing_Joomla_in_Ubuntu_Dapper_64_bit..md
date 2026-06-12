---
title: "Installing Joomla in Ubuntu Dapper 64 bit."
date: 2006-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Extol11 on 2006-09-02
Hello! I have installed joomla in Suse 10.1 but it seems ubuntu won't accept the same commands I used in Suse. The problem I'm having is that I have to change the ownership of the configuration.php file. In Suse I used the following command:

> chown wwwrun configuration.php

And it would change the ownership so that joomla could write to it. In ubuntu it tells me the following:

[COLOR="Blue"]`wwwrun': invalid user[/COLOR]
I was explained that wwwrun is the account that the web server runs under. Does this work different in Ubuntu? 

I also have to "chown -r wwwrun" the following files: 

```
administrator/backups/	Unwriteable
administrator/components/	Unwriteable
administrator/modules/	Unwriteable
administrator/templates/	Unwriteable
cache/	Unwriteable
components/	Unwriteable
images/	Unwriteable
images/banners/	Unwriteable
images/stories/	Unwriteable
language/	Unwriteable
mambots/	Unwriteable
mambots/content/	Unwriteable
mambots/editors/	Unwriteable
mambots/editors-xtd/	Unwriteable
mambots/search/	Unwriteable
mambots/system/	Unwriteable
media/	Unwriteable
modules/	Unwriteable
templates/	Unwriteable
```

I don't think it'll work either so... can anyone help me on how to change the ownership so Joomla can write to them? 

And one last thing. When I go to the page for the setup of joomla it tells me this:

> Joomla! RG_EMULATION setting is `ON` instead of `OFF` in file globals.php
`ON` by default for compatibility reasons

What should I do about it? Leave it On? It says it is not recommended but then, I didn't have this problem with Suse so I don't know what to do.


Thanks in advanced.

---

### Post by Extol11 on 2006-09-03
Up up! Doesn't anybody know? I searched and only found topics in which people had already installed it and were dealing with post installation stuff.

---

### Post by juicemansam on 2006-09-03
It should be the user **www-data** and the group **www-data**.

---

### Post by Extol11 on 2006-09-04
Thanks a whole lot, man. And why does it change?

---

### Post by Extol11 on 2006-09-04
I forgot...

> Joomla! RG_EMULATION setting is `ON` instead of `OFF` in file globals.php
`ON` by default for compatibility reasons

Should I just continue installing joomla and leave that as it is?

---

### Post by juicemansam on 2006-09-05
It's not that the user changes, as much as what user the distribution chose for that particular service. Other distributions might use a user named **www**.

I'm not sure what RG_EMULATION, but from what I can tell its Register Globals Emulation. I don't see why you couldn't continue running Joomla, with or without register globals (either normal or emulated). Register globals were a standard method of using variables in PHP, but because of badly written php scripts, register globals were turned off by default in later php versions, which broke some php scripts. Joomla/Mambo have adpated since change and should work just as it should with and without register globals enabled on the server. Check out [PHP: Using Register Globals](http://www.php.net/manual/en/security.globals.php) document, it will give you the info you'll need to make the descition, which really is up to you, along with what you can have with your webhost.

---

