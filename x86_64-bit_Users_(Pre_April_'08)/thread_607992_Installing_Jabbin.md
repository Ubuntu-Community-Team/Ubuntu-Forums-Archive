---
title: "Installing Jabbin"
date: 2007-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by hellmet on 2007-11-09
Can somebody here help me install Jabbin on my 64 bit? 

Thanks!!

---

### Post by hellmet on 2007-11-12
uhm. Bump ?

---

### Post by hellmet on 2007-12-05
anyone? sry for the bumps..

---

### Post by Yellow Pasque on 2007-12-05
Ok, I saw your post about 2 hours ago when you made it and I set out to build jabbin. All I can say is, "Wow! That sucked."
...But it is doable.

First, let's get some packages:
```
sudo apt-get install build-essential libqca1c2 qca-dev qca-tls libqt3-headers libqt3-mt libqt3-mt-dev qt3-apps-dev qt3-dev-tools zlib1g zlib1g-dbg zlib1g-dev zlib-bin zlibc g++ g++-4.1 g++-4.1-multilib g++-multilib
```

Now you'll need to download and build speex, because the version that comes with jabbin prevents it from building. Get it here:
[http://downloads.us.xiph.org/releases/speex/speex-1.2beta2.tar.gz](http://downloads.us.xiph.org/releases/speex/speex-1.2beta2.tar.gz)
Download, extract, navigate to the folder you just extracted. Now run the old:
```
./configure
sudo make
sudo make install
```

Download and extract the jabbin source code. I used the latest release, beta2a
[http://downloads.sourceforge.net/jabbin/jabbin-2.0beta2a.tar.bz2?modtime=1156537602&big_mirror=0](http://downloads.sourceforge.net/jabbin/jabbin-2.0beta2a.tar.bz2?modtime=1156537602&big_mirror=0)
Now navigate to the base jabbin-2.0 directory in a terminal and do a:
```
chmod 755 *
./configure
```

Now you'll need to patch some files according to this:
[http://svn.mandriva.com/cgi-bin/viewvc.cgi/packages/cooker/jabbin/current/SOURCES/jabbin-fix_x86_64_build.patch?revision=84148](http://svn.mandriva.com/cgi-bin/viewvc.cgi/packages/cooker/jabbin/current/SOURCES/jabbin-fix_x86_64_build.patch?revision=84148)
It's not as bad as it looks. Just delete the lines that begin with a minus sign (-) and replace with the (+). The file names and line numbers are given, so use gedit and look at the line counter in the bottom-right. There's also a nifty way to automate it by using the patch command, but I'm not sure how off the top of my head.

Finally, you can do the sudo make and sudo make install for jabbin.

If you have any questions, don't hesitate to ask.

---

### Post by Yellow Pasque on 2007-12-05
I hope I got all of the packages listed you'll need. I frequently build software on my computer, so I had a lot of libraries already installed.

**EDIT:** When I was looking for other packages in Synaptic, I noticed that speex/libspeex is available as a pre-built deb. Personally, I'd build the latest version myself if I were you, as it looks like they've made some major improvements, but the pre-built is there to fall back on if you have trouble or are feeling truly lazy.

---

### Post by hellmet on 2007-12-08
Speex installation went fine. chmod and ./configure for jabbin went ok. But, 'sudo make' gives :  No targets specified and no makefile found.  Stop.
doing ./install.sh makes it do something. But, no Jabbin icon, and an Alt-F2 and jabbin doesn't work.
What ./install.sh does is it just fills up /usr/share/jabbin .. nothing else.

---

### Post by hellmet on 2007-12-08
Thank you so much for your patience..
Ok.. my bad. I didn't have libxss-dev , actually, ./configure spat out an error that I hadn't noticed.
Now that ran fine.

But,  sudo make spits out stuff that I don't understand.. Maybe you could help.
Maybe I'm missing something.
```
-I../iris/libidn -I../iris/include -I../iris/xmpp-core -I../iris/xmpp-im -I../iris/jabber -Ilibpsi/iconset -Ilibpsi/psiwidgets -Ilibpsi/psipng -I/usr/include/qt3 -I/usr/X11R6/include -I.ui/ -I. -Ioptions -I.moc/ -o .obj/qca-tls.o ../3party/qca/qca-tls.cpp
../3party/qca/qca-tls.cpp:25:24: error: openssl/sha.h: No such file or directory
../3party/qca/qca-tls.cpp:26:24: error: openssl/md5.h: No such file or directory
../3party/qca/qca-tls.cpp:27:24: error: openssl/evp.h: No such file or directory
../3party/qca/qca-tls.cpp:28:24: error: openssl/bio.h: No such file or directory
../3party/qca/qca-tls.cpp:29:24: error: openssl/pem.h: No such file or directory
../3party/qca/qca-tls.cpp:30:24: error: openssl/rsa.h: No such file or directory
../3party/qca/qca-tls.cpp:31:25: error: openssl/x509.h: No such file or directory
../3party/qca/qca-tls.cpp:32:27: error: openssl/x509v3.h: No such file or directory
../3party/qca/qca-tls.cpp:33:24: error: openssl/ssl.h: No such file or directory
../3party/qca/qca-tls.cpp:34:24: error: openssl/err.h: No such file or directory
../3party/qca/qca-tls.cpp:35:25: error: openssl/rand.h: No such file or directory
../3party/qca/qca-tls.cpp: In function &#8216;QByteArray lib_randomArray(int)&#8217;:
../3party/qca/qca-tls.cpp:43: error: &#8216;RAND_status&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:48: error: &#8216;RAND_seed&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:51: error: &#8216;RAND_bytes&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: At global scope:
../3party/qca/qca-tls.cpp:55: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp:55: error: ISO C++ forbids declaration of &#8216;EVP_CIPHER&#8217; with no type
../3party/qca/qca-tls.cpp: In function &#8216;bool lib_generateKeyIV(int)&#8217;:
../3party/qca/qca-tls.cpp:60: error: expected `;' before &#8216;type&#8217;
../3party/qca/qca-tls.cpp:60: warning: statement has no effect
../3party/qca/qca-tls.cpp:61: error: &#8216;keysize&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:62: error: &#8216;type&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:63: error: &#8216;key&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:64: error: &#8216;type&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:67: error: &#8216;iv&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:68: error: &#8216;type&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:71: error: &#8216;type&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:71: error: &#8216;EVP_sha1&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:71: error: &#8216;salt&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:71: error: &#8216;data&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:71: error: &#8216;EVP_BytesToKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:73: error: &#8216;key&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:75: error: &#8216;iv&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: At global scope:
../3party/qca/qca-tls.cpp:87: error: &#8216;BIO&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:87: error: &#8216;b&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:88: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
../3party/qca/qca-tls.cpp:133: error: &#8216;SHA_CTX&#8217; does not name a type
../3party/qca/qca-tls.cpp: In member function &#8216;virtual void SHA1Context::reset()&#8217;:
../3party/qca/qca-tls.cpp:118: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:118: error: &#8216;SHA1_Init&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual void SHA1Context::update(const char*, unsigned int)&#8217;:
../3party/qca/qca-tls.cpp:123: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:123: error: &#8216;SHA1_Update&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual void SHA1Context::final(QByteArray*)&#8217;:
../3party/qca/qca-tls.cpp:129: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:129: error: &#8216;SHA1_Final&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: At global scope:
../3party/qca/qca-tls.cpp:166: error: &#8216;MD5_CTX&#8217; does not name a type
../3party/qca/qca-tls.cpp: In member function &#8216;virtual void MD5Context::reset()&#8217;:
../3party/qca/qca-tls.cpp:151: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:151: error: &#8216;MD5_Init&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual void MD5Context::update(const char*, unsigned int)&#8217;:
../3party/qca/qca-tls.cpp:156: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:156: error: &#8216;MD5_Update&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual void MD5Context::final(QByteArray*)&#8217;:
../3party/qca/qca-tls.cpp:162: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:162: error: &#8216;MD5_Final&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: At global scope:
../3party/qca/qca-tls.cpp:193: error: ISO C++ forbids declaration of &#8216;EVP_CIPHER&#8217; with no type
../3party/qca/qca-tls.cpp:193: error: &#8216;EVP_CIPHER&#8217; declared as a &#8216;virtual&#8217; field
../3party/qca/qca-tls.cpp:193: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp:282: error: &#8216;EVP_CIPHER_CTX&#8217; does not name a type
../3party/qca/qca-tls.cpp:283: error: ISO C++ forbids declaration of &#8216;EVP_CIPHER&#8217; with no type
../3party/qca/qca-tls.cpp:283: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp: In constructor &#8216;EVPCipherContext::EVPCipherContext()&#8217;:
../3party/qca/qca-tls.cpp:174: error: &#8216;type&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In destructor &#8216;virtual EVPCipherContext::~EVPCipherContext()&#8217;:
../3party/qca/qca-tls.cpp:179: error: &#8216;type&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:180: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:180: error: &#8216;EVP_CIPHER_CTX_cleanup&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual int EVPCipherContext::keySize()&#8217;:
../3party/qca/qca-tls.cpp:195: error: &#8216;getType&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual int EVPCipherContext::blockSize()&#8217;:
../3party/qca/qca-tls.cpp:196: error: &#8216;getType&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool EVPCipherContext::generateKey(char*, int)&#8217;:
../3party/qca/qca-tls.cpp:201: error: &#8216;getType&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool EVPCipherContext::generateIV(char*)&#8217;:
../3party/qca/qca-tls.cpp:210: error: &#8216;getType&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool EVPCipherContext::setup(int, int, const char*, int, const char*, bool)&#8217;:
../3party/qca/qca-tls.cpp:220: error: &#8216;type&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:220: error: &#8216;getType&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:222: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:222: error: &#8216;EVP_CIPHER_CTX_init&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:225: error: &#8216;EVP_EncryptInit&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:228: error: &#8216;EVP_CIPHER_CTX_set_key_length&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:229: error: &#8216;EVP_EncryptInit&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:233: error: &#8216;EVP_DecryptInit&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:236: error: &#8216;EVP_CIPHER_CTX_set_key_length&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:237: error: &#8216;EVP_DecryptInit&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool EVPCipherContext::update(const char*, unsigned int)&#8217;:
../3party/qca/qca-tls.cpp:245: error: &#8216;type&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:248: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:248: error: &#8216;EVP_EncryptUpdate&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:252: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:252: error: &#8216;EVP_DecryptUpdate&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool EVPCipherContext::final(QByteArray*)&#8217;:
../3party/qca/qca-tls.cpp:263: error: &#8216;type&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:266: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:266: error: &#8216;EVP_EncryptFinal&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:270: error: &#8216;c&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:270: error: &#8216;EVP_DecryptFinal&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: At global scope:
../3party/qca/qca-tls.cpp:293: error: ISO C++ forbids declaration of &#8216;EVP_CIPHER&#8217; with no type
../3party/qca/qca-tls.cpp:293: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp:302: error: expected `;' before &#8216;}&#8217; token
../3party/qca/qca-tls.cpp:308: error: ISO C++ forbids declaration of &#8216;EVP_CIPHER&#8217; with no type
../3party/qca/qca-tls.cpp:308: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp:317: error: expected `;' before &#8216;}&#8217; token
../3party/qca/qca-tls.cpp:324: error: ISO C++ forbids declaration of &#8216;EVP_CIPHER&#8217; with no type
../3party/qca/qca-tls.cpp:324: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp:333: error: expected `;' before &#8216;}&#8217; token
../3party/qca/qca-tls.cpp:339: error: ISO C++ forbids declaration of &#8216;EVP_CIPHER&#8217; with no type
../3party/qca/qca-tls.cpp:339: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp:348: error: expected `;' before &#8216;}&#8217; token
../3party/qca/qca-tls.cpp:377: error: &#8216;RSA&#8217; has not been declared
../3party/qca/qca-tls.cpp:377: error: &#8216;RSA&#8217; has not been declared
../3party/qca/qca-tls.cpp:377: error: &#8216;RSA&#8217; has not been declared
../3party/qca/qca-tls.cpp:632: error: ISO C++ forbids declaration of &#8216;RSA&#8217; with no type
../3party/qca/qca-tls.cpp:632: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp: In constructor &#8216;RSAKeyContext::RSAKeyContext()&#8217;:
../3party/qca/qca-tls.cpp:356: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:357: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;void RSAKeyContext::reset()&#8217;:
../3party/qca/qca-tls.cpp:367: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:368: error: &#8216;RSA_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:371: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:372: error: &#8216;RSA_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;void RSAKeyContext::separate(int*, int**, int**)&#8217;:
../3party/qca/qca-tls.cpp:381: error: &#8216;i2d_RSAPublicKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:388: error: &#8216;d2i_RSAPublicKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:395: error: &#8216;i2d_RSAPrivateKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:402: error: &#8216;d2i_RSAPrivateKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool RSAKeyContext::isNull() const&#8217;:
../3party/qca/qca-tls.cpp:412: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:412: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool RSAKeyContext::havePublic() const&#8217;:
../3party/qca/qca-tls.cpp:419: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool RSAKeyContext::havePrivate() const&#8217;:
../3party/qca/qca-tls.cpp:424: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool RSAKeyContext::createFromDER(const char*, unsigned int)&#8217;:
../3party/qca/qca-tls.cpp:429: error: &#8216;RSA&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:429: error: &#8216;r&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:435: error: &#8216;d2i_RSAPrivateKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:443: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:443: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:450: error: &#8216;d2i_RSAPublicKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:463: error: &#8216;d2i_RSA_PUBKEY&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:468: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:469: error: &#8216;RSA_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:471: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool RSAKeyContext::createFromPEM(const char*, unsigned int)&#8217;:
../3party/qca/qca-tls.cpp:481: error: &#8216;BIO&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:481: error: &#8216;bi&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:484: error: &#8216;BIO_s_mem&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:484: error: &#8216;BIO_new&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:485: error: &#8216;BIO_write&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:486: error: &#8216;RSA&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:486: error: &#8216;r&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:486: error: &#8216;PEM_read_bio_RSAPrivateKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:487: error: &#8216;BIO_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:490: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:490: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:497: error: &#8216;PEM_read_bio_RSAPublicKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:500: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:501: error: &#8216;RSA_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:503: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool RSAKeyContext::createFromNative(void*)&#8217;:
../3party/qca/qca-tls.cpp:514: error: &#8216;RSA&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:514: error: expected primary-expression before &#8216;)&#8217; token
../3party/qca/qca-tls.cpp:514: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:514: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: At global scope:
../3party/qca/qca-tls.cpp:511: warning: unused parameter &#8216;in&#8217;
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool RSAKeyContext::generate(unsigned int)&#8217;:
../3party/qca/qca-tls.cpp:520: error: &#8216;RSA&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:520: error: &#8216;r&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:520: error: &#8216;RSA_F4&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:520: error: &#8216;RSA_generate_key&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:523: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:523: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:524: error: &#8216;RSA_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual QCA_RSAKeyContext* RSAKeyContext::clone() const&#8217;:
../3party/qca/qca-tls.cpp:532: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:534: error: &#8216;class RSAKeyContext&#8217; has no member named &#8216;pub&#8217;
../3party/qca/qca-tls.cpp:536: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:538: error: &#8216;class RSAKeyContext&#8217; has no member named &#8216;sec&#8217;
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool RSAKeyContext::toDER(QByteArray*, bool)&#8217;:
../3party/qca/qca-tls.cpp:545: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:546: error: &#8216;i2d_RSAPrivateKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:554: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:555: error: &#8216;i2d_RSAPublicKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool RSAKeyContext::toPEM(QByteArray*, bool)&#8217;:
../3party/qca/qca-tls.cpp:569: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:570: error: &#8216;BIO&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:570: error: &#8216;bo&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:570: error: &#8216;BIO_s_mem&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:570: error: &#8216;BIO_new&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:571: error: &#8216;PEM_write_bio_RSAPrivateKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:575: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:576: error: &#8216;BIO&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:576: error: &#8216;bo&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:576: error: &#8216;BIO_s_mem&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:576: error: &#8216;BIO_new&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:577: error: &#8216;PEM_write_bio_RSAPublicKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool RSAKeyContext::encrypt(const QByteArray&, QByteArray*, bool)&#8217;:
../3party/qca/qca-tls.cpp:588: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:591: error: &#8216;pub&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:591: error: &#8216;RSA_size&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:604: error: &#8216;RSA_PKCS1_OAEP_PADDING&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:604: error: &#8216;RSA_PKCS1_PADDING&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:604: error: &#8216;RSA_public_encrypt&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool RSAKeyContext::decrypt(const QByteArray&, QByteArray*, bool)&#8217;:
../3party/qca/qca-tls.cpp:615: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:618: error: &#8216;sec&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:618: error: &#8216;RSA_size&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:623: error: &#8216;RSA_PKCS1_OAEP_PADDING&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:623: error: &#8216;RSA_PKCS1_PADDING&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:623: error: &#8216;RSA_private_decrypt&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In function &#8216;QValueList<QCA_CertProperty> nameToProperties(X509_name_st*)&#8217;:
../3party/qca/qca-tls.cpp:639: error: &#8216;X509_NAME_entry_count&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:640: error: &#8216;X509_NAME_ENTRY&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:640: error: &#8216;ne&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:640: error: &#8216;X509_NAME_get_entry&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:643: error: &#8216;ASN1_OBJECT&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:643: error: &#8216;ao&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:643: error: &#8216;X509_NAME_ENTRY_get_object&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:644: error: &#8216;OBJ_obj2nid&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:645: error: &#8216;NID_undef&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:647: error: &#8216;OBJ_nid2sn&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:649: error: &#8216;ASN1_STRING&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:649: error: &#8216;as&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:649: error: &#8216;X509_NAME_ENTRY_get_data&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: At global scope:
../3party/qca/qca-tls.cpp:664: error: &#8216;ASN1_UTCTIME&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:664: error: expected primary-expression before &#8216;,&#8217; token
../3party/qca/qca-tls.cpp:664: error: expected primary-expression before &#8216;int&#8217;
../3party/qca/qca-tls.cpp:665: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
../3party/qca/qca-tls.cpp:857: error: &#8216;X509&#8217; has not been declared
../3party/qca/qca-tls.cpp:943: error: ISO C++ forbids declaration of &#8216;X509&#8217; with no type
../3party/qca/qca-tls.cpp:943: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp: In constructor &#8216;CertContext::CertContext()&#8217;:
../3party/qca/qca-tls.cpp:768: error: &#8216;x&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual QCA_CertContext* CertContext::clone() const&#8217;:
../3party/qca/qca-tls.cpp:779: error: &#8216;x&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:781: error: &#8216;class CertContext&#8217; has no member named &#8216;x&#8217;
../3party/qca/qca-tls.cpp: In member function &#8216;void CertContext::reset()&#8217;:
../3party/qca/qca-tls.cpp:788: error: &#8216;x&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:789: error: &#8216;X509_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool CertContext::isNull() const&#8217;:
../3party/qca/qca-tls.cpp:804: error: &#8216;x&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool CertContext::createFromDER(const char*, unsigned int)&#8217;:
../3party/qca/qca-tls.cpp:816: error: &#8216;X509&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:816: error: &#8216;t&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:816: error: &#8216;d2i_X509&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:822: error: &#8216;X509_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool CertContext::createFromPEM(const char*, unsigned int)&#8217;:
../3party/qca/qca-tls.cpp:828: error: &#8216;BIO&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:828: error: &#8216;bi&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:828: error: &#8216;BIO_s_mem&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:828: error: &#8216;BIO_new&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:829: error: &#8216;BIO_write&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:830: error: &#8216;X509&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:830: error: &#8216;t&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:830: error: &#8216;PEM_read_bio_X509&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:831: error: &#8216;BIO_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:835: error: &#8216;X509_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool CertContext::toDER(QByteArray*)&#8217;:
../3party/qca/qca-tls.cpp:841: error: &#8216;x&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:841: error: &#8216;i2d_X509&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool CertContext::toPEM(QByteArray*)&#8217;:
../3party/qca/qca-tls.cpp:851: error: &#8216;BIO&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:851: error: &#8216;bo&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:851: error: &#8216;BIO_s_mem&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:851: error: &#8216;BIO_new&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:852: error: &#8216;x&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:852: error: &#8216;PEM_write_bio_X509&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;void CertContext::fromX509(int*)&#8217;:
../3party/qca/qca-tls.cpp:860: error: request for member &#8216;references&#8217; in &#8216;* t&#8217;, which is of non-class type &#8216;int&#8217;
../3party/qca/qca-tls.cpp:861: error: &#8216;x&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:864: error: &#8216;ASN1_INTEGER&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:864: error: &#8216;ai&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:864: error: &#8216;X509_get_serialNumber&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:866: error: &#8216;i2s_ASN1_INTEGER&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:868: error: &#8216;OPENSSL_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:872: error: &#8216;X509_get_notBefore&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:873: error: &#8216;X509_get_notAfter&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:876: error: &#8216;X509_get_subject_name&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:877: error: &#8216;X509_get_issuer_name&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:879: error: &#8216;X509_NAME_oneline&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: At global scope:
../3party/qca/qca-tls.cpp:963: error: ISO C++ forbids declaration of &#8216;SSL&#8217; with no type
../3party/qca/qca-tls.cpp:963: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp:964: error: ISO C++ forbids declaration of &#8216;SSL_METHOD&#8217; with no type
../3party/qca/qca-tls.cpp:964: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp:965: error: ISO C++ forbids declaration of &#8216;SSL_CTX&#8217; with no type
../3party/qca/qca-tls.cpp:965: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp:966: error: ISO C++ forbids declaration of &#8216;BIO&#8217; with no type
../3party/qca/qca-tls.cpp:966: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../3party/qca/qca-tls.cpp: In constructor &#8216;TLSContext::TLSContext()&#8217;:
../3party/qca/qca-tls.cpp:974: error: &#8216;SSL_library_init&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:975: error: &#8216;SSL_load_error_strings&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:979: error: &#8216;ssl&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:980: error: &#8216;context&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual void TLSContext::reset()&#8217;:
../3party/qca/qca-tls.cpp:992: error: &#8216;ssl&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:993: error: &#8216;SSL_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:996: error: &#8216;context&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:997: error: &#8216;SSL_CTX_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool TLSContext::startClient(const QPtrList<QCA_CertContext>&, const QCA_CertContext&, const QCA_RSAKeyContext&)&#8217;:
../3party/qca/qca-tls.cpp:1026: error: &#8216;method&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1026: error: &#8216;SSLv23_client_method&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool TLSContext::startServer(const QPtrList<QCA_CertContext>&, const QCA_CertContext&, const QCA_RSAKeyContext&)&#8217;:
../3party/qca/qca-tls.cpp:1039: error: &#8216;method&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1039: error: &#8216;SSLv23_server_method&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;bool TLSContext::setup(const QPtrList<QCA_CertContext>&, const QCA_CertContext&, const QCA_RSAKeyContext&)&#8217;:
../3party/qca/qca-tls.cpp:1050: error: &#8216;context&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1050: error: &#8216;method&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1050: error: &#8216;SSL_CTX_new&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1058: error: &#8216;X509_STORE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1058: error: &#8216;store&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1058: error: &#8216;SSL_CTX_get_cert_store&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1061: error: &#8216;class CertContext&#8217; has no member named &#8216;x&#8217;
../3party/qca/qca-tls.cpp:1061: error: &#8216;X509_STORE_add_cert&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1064: error: &#8216;ssl&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1064: error: &#8216;SSL_new&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1069: error: &#8216;SSL_set_ssl_method&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1072: error: &#8216;rbio&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1072: error: &#8216;BIO_s_mem&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1072: error: &#8216;BIO_new&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1073: error: &#8216;wbio&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1076: error: &#8216;SSL_set_bio&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1082: error: &#8216;class CertContext&#8217; has no member named &#8216;x&#8217;
../3party/qca/qca-tls.cpp:1082: error: &#8216;SSL_use_certificate&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1086: error: &#8216;class RSAKeyContext&#8217; has no member named &#8216;sec&#8217;
../3party/qca/qca-tls.cpp:1086: error: &#8216;SSL_use_RSAPrivateKey&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual int TLSContext::handshake(const QByteArray&, QByteArray*)&#8217;:
../3party/qca/qca-tls.cpp:1098: error: &#8216;rbio&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1098: error: &#8216;BIO_write&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual int TLSContext::shutdown(const QByteArray&, QByteArray*)&#8217;:
../3party/qca/qca-tls.cpp:1147: error: &#8216;rbio&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1147: error: &#8216;BIO_write&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;void TLSContext::getCert()&#8217;:
../3party/qca/qca-tls.cpp:1171: error: &#8216;X509&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1171: error: &#8216;x&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1171: error: &#8216;ssl&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1171: error: &#8216;SSL_get_peer_certificate&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1174: error: &#8216;X509_free&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1175: error: &#8216;SSL_get_verify_result&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1176: error: &#8216;X509_V_OK&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool TLSContext::encode(const QByteArray&, QByteArray*, int*)&#8217;:
../3party/qca/qca-tls.cpp:1196: error: &#8216;ssl&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1196: error: &#8216;SSL_write&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1201: error: &#8216;SSL_get_error&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1202: error: &#8216;SSL_ERROR_WANT_READ&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1202: error: &#8216;SSL_ERROR_WANT_WRITE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1204: error: &#8216;SSL_ERROR_ZERO_RETURN&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual bool TLSContext::decode(const QByteArray&, QByteArray*, QByteArray*)&#8217;:
../3party/qca/qca-tls.cpp:1239: error: &#8216;rbio&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1239: error: &#8216;BIO_write&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1244: error: &#8216;ssl&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1244: error: &#8216;SSL_read&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1251: error: &#8216;SSL_get_error&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1252: error: &#8216;SSL_ERROR_WANT_READ&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1252: error: &#8216;SSL_ERROR_WANT_WRITE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1254: error: &#8216;SSL_ERROR_ZERO_RETURN&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;virtual QByteArray TLSContext::unprocessed()&#8217;:
../3party/qca/qca-tls.cpp:1272: error: &#8216;rbio&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1272: error: &#8216;BIO_pending&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1277: error: &#8216;BIO_read&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;QByteArray TLSContext::readOutgoing()&#8217;:
../3party/qca/qca-tls.cpp:1290: error: &#8216;wbio&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1290: error: &#8216;BIO_pending&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1295: error: &#8216;BIO_read&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;int TLSContext::doConnect()&#8217;:
../3party/qca/qca-tls.cpp:1307: error: &#8216;ssl&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1307: error: &#8216;SSL_connect&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1309: error: &#8216;SSL_get_error&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1310: error: &#8216;SSL_ERROR_WANT_CONNECT&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1310: error: &#8216;SSL_ERROR_WANT_READ&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1310: error: &#8216;SSL_ERROR_WANT_WRITE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;int TLSContext::doAccept()&#8217;:
../3party/qca/qca-tls.cpp:1322: error: &#8216;ssl&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1322: error: &#8216;SSL_accept&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1324: error: &#8216;SSL_get_error&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1325: error: &#8216;SSL_ERROR_WANT_CONNECT&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1325: error: &#8216;SSL_ERROR_WANT_READ&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1325: error: &#8216;SSL_ERROR_WANT_WRITE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;int TLSContext::doHandshake()&#8217;:
../3party/qca/qca-tls.cpp:1337: error: &#8216;ssl&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1337: error: &#8216;SSL_do_handshake&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1339: error: &#8216;SSL_get_error&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1340: error: &#8216;SSL_ERROR_WANT_READ&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1340: error: &#8216;SSL_ERROR_WANT_WRITE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;int TLSContext::doShutdown()&#8217;:
../3party/qca/qca-tls.cpp:1352: error: &#8216;ssl&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1352: error: &#8216;SSL_shutdown&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1358: error: &#8216;SSL_get_error&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1359: error: &#8216;SSL_ERROR_WANT_READ&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1359: error: &#8216;SSL_ERROR_WANT_WRITE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp: In member function &#8216;int TLSContext::resultToCV(int) const&#8217;:
../3party/qca/qca-tls.cpp:1380: error: &#8216;X509_V_ERR_CERT_REJECTED&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1383: error: &#8216;X509_V_ERR_CERT_UNTRUSTED&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1386: error: &#8216;X509_V_ERR_UNABLE_TO_VERIFY_LEAF_SIGNATURE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1387: error: &#8216;X509_V_ERR_CERT_SIGNATURE_FAILURE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1388: error: &#8216;X509_V_ERR_CRL_SIGNATURE_FAILURE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1389: error: &#8216;X509_V_ERR_UNABLE_TO_DECRYPT_CERT_SIGNATURE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1390: error: &#8216;X509_V_ERR_UNABLE_TO_DECRYPT_CRL_SIGNATURE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1393: error: &#8216;X509_V_ERR_INVALID_CA&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1394: error: &#8216;X509_V_ERR_UNABLE_TO_GET_ISSUER_CERT&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1395: error: &#8216;X509_V_ERR_UNABLE_TO_DECODE_ISSUER_PUBLIC_KEY&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1396: error: &#8216;X509_V_ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1399: error: &#8216;X509_V_ERR_INVALID_PURPOSE&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1402: error: &#8216;X509_V_ERR_DEPTH_ZERO_SELF_SIGNED_CERT&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1403: error: &#8216;X509_V_ERR_SELF_SIGNED_CERT_IN_CHAIN&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1406: error: &#8216;X509_V_ERR_CERT_REVOKED&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1409: error: &#8216;X509_V_ERR_PATH_LENGTH_EXCEEDED&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1412: error: &#8216;X509_V_ERR_CERT_NOT_YET_VALID&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1413: error: &#8216;X509_V_ERR_CERT_HAS_EXPIRED&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1414: error: &#8216;X509_V_ERR_CRL_NOT_YET_VALID&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1415: error: &#8216;X509_V_ERR_CRL_HAS_EXPIRED&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1416: error: &#8216;X509_V_ERR_ERROR_IN_CERT_NOT_BEFORE_FIELD&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1417: error: &#8216;X509_V_ERR_ERROR_IN_CERT_NOT_AFTER_FIELD&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1418: error: &#8216;X509_V_ERR_ERROR_IN_CRL_LAST_UPDATE_FIELD&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1419: error: &#8216;X509_V_ERR_ERROR_IN_CRL_NEXT_UPDATE_FIELD&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1422: error: &#8216;X509_V_ERR_APPLICATION_VERIFICATION&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1423: error: &#8216;X509_V_ERR_OUT_OF_MEM&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1424: error: &#8216;X509_V_ERR_UNABLE_TO_GET_CRL&#8217; was not declared in this scope
../3party/qca/qca-tls.cpp:1425: error: &#8216;X509_V_ERR_CERT_CHAIN_TOO_LONG&#8217; was not declared in this scope
make[1]: *** [.obj/qca-tls.o] Error 1
make[1]: Leaving directory `/home/sanju/Desktop/jabbin-2.0beta2a/src'
make: *** [sub-src] Error 2

```

---

### Post by Yellow Pasque on 2007-12-09
Looks like it's spitting out errors about openssl. You probably need another package or two.
```
sudo apt-get install libssl0.9.8 libssl-dev
```

---

### Post by hellmet on 2007-12-09
Excellent. That worked. Thank you so much. But, I'm not able to get voice working on it though. Call connects and disconnects in a few seconds, without voice reaching either of the persons. But, ofcourse, that is out of scope of this thread.
Thanks so much for your patience once again.

---

### Post by Yellow Pasque on 2007-12-10
Darn. I was afraid of that. :(

> Thanks so much for your patience once again.
Yw.

---

### Post by rykel on 2008-06-22
Hi all,

I tested a Virtual Number for my country (from GTalk2VoIP) which called me on GoogleTalk/Jabbin successfully.

I tried the same procedure on OpenWengo but there was no way to "accept" the voicecall and start talking away.

btw, I installed the latest DEBIAN version of Jabbin on Ubuntu Hardy, because the Ubuntu deb insisted that I have libssl0.9.7 instead of the current 0.9.8 which is already on my system.

Does anyone know how we can merge Jabbin into OpenWengo? (since OpenWengo can already handle the IM side of GoogleTalk) Or, is there a way to "accept incoming calls" from OpenWengo, since the dialog has already appeared?

---

