---
title: "ok a question..  pls don't laugh.."
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by areitze on 2006-05-29
what are binary files???  In a few places I see download for binary, like the new picasa for linux...  what are those???  sorry for the post if it bothers...  but wish to know...

Thx,
ARV.-

---

### Post by glotz on 2006-05-30
Binary files are files in format the computer understands. You *compile* a *source code* to *binary* to run it. Source code is human readable code written in some computer language.

See [http://en.wikipedia.org/wiki/Compiling](http://en.wikipedia.org/wiki/Compiling)

---

### Post by drachir on 2006-05-30
From Wikipedia, the free encyclopedia

A binary file is a computer file which may contain any type of data, encoded in binary form for computer storage and processing purposes; for example, computer document files containing formatted text. Many binary file formats contain parts that can be interpreted as text; binary files that contain only textual data - without, for example, any formatting information - are called plain text files. In ordinary usage they are typically contrasted with binary files, so that binary files are all files which do not contain merely plain text

Binary file formats
Binary files are usually thought of as being a sequence of bytes, which means the binary digits (bits) are grouped in eights. Binary files typically contain bytes that are intended to be interpreted as something other than text characters. Compiled computer programs are typical examples; indeed, compiled applications (object files) are sometimes referred to, particularly by programmers, as binaries. But binary files can also contain images, sounds, compressed versions of other files, etc. — in short, any type of file content whatsoever.

Some binary files contain headers, blocks of metadata used by a computer program to interpret the data in the file. For example, a GIF file can contain multiple images, and headers are used to identify and describe each block of image data. If a binary file does not contain any headers, it may be called a flat binary file.

The only dumb question is the one not asked. This is how we all learn

---

### Post by Ptero-4 on 2006-05-30
A binary file is the executable program itself. When you see mentions of binaries, it means a installer with the stuff needed to install the app you're downloading.

---

### Post by elamericano on 2006-05-30
Binary in that sense is usually a program you can run, but a binary file is any file that does not represent readable text. (e.g. compiled programs, pictures, music, etc.)

---

### Post by ssam on 2006-05-30
and the important point that nobody seems to have made yet, is that binary files only work on the platform they were compiled for. but the source can be recompiled for many platforms (as long as the source is writen in a portable way)

so x86 linux binaries will only work on x86 linux
powerpc linux binaries will only work on powerpc linux.
x86 windows binaries will only work on x86 windows

there are some clever hacks to break this rule. eg wine lets x86 some windows binaries run on x86 linux. qemu lets you run x86 linux binaries on powerpc (though you also need all the x86 libraries).

---

