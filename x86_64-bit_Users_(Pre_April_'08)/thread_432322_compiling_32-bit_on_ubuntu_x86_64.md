---
title: "compiling 32-bit on ubuntu x86_64"
date: 2007-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by wtruong on 2007-05-03
I'm trying to compile this program for my comp sci class on my 64 bit ubuntu.  When I try to compile with the Makefile it says: 

g++ -m32 -Wall -ansi -g -o timetest3.out timetest3.o BTree.o BTreeNode.o InternalNode.o LeafNode.o
/usr/bin/ld: warning: i386:x86-64 architecture of input file `BTree.o' is incompatible with i386 output
/usr/bin/ld: warning: i386:x86-64 architecture of input file `LeafNode.o' is incompatible with i386 output
BTree.o: In function `BTree::insert(int)':
/home/wtruong/ecs110/p3/BTree.cpp:20: undefined reference to `operator new(unsigned long)'
BTree.o: In function `BTree':
/home/wtruong/ecs110/p3/BTree.cpp:10: undefined reference to `operator new(unsigned long)'
/home/wtruong/ecs110/p3/BTree.cpp:10: undefined reference to `operator new(unsigned long)'
BTree.o: In function `Vector':
/home/wtruong/ecs110/p3/vector.h:19: undefined reference to `operator new[](unsigned long)'
LeafNode.o: In function `LeafNode':
/home/wtruong/ecs110/p3/LeafNode.cpp:12: undefined reference to `operator new[](unsigned long)'
LeafNode.o: In function `LeafNode::split(int, int)':
/home/wtruong/ecs110/p3/LeafNode.cpp:214: undefined reference to `operator new(unsigned long)'
LeafNode.o: In function `LeafNode':
/home/wtruong/ecs110/p3/LeafNode.cpp:12: undefined reference to `operator new[](unsigned long)'
collect2: ld returned 1 exit status
make: *** [timetest3.out] Error 1


do i need any flags to force a 32bit compile??  thanks in advance

---

### Post by dfreer on 2007-05-03
hmmm. I'm not quite sure, but it seems like from the error messages that the *.o files or of the wrong ELF class. are these libraries in the same way as the libraries in /usr/lib/? If so, you probably need to get 32-bit versions of these. And the other errors simply look like syntax errors.
Of course I prolly have completely misunderstood the problem as I have limited programming experience :D

---

### Post by RAOF on 2007-05-04
It looks like both BTree.o and LeafNode.o have been compiled to x86-64 object code, not i386.  You're already passing the right flags (-m32) to that part of the compile.  The problem is almost certainly earlier, when you're building BTree.o & LeafNode.o

---

### Post by wtruong on 2007-05-04
ahh yeah thanks, i removed the object files and remade it and it worked.

---

### Post by Ledah on 2007-05-13
I have a general question about that. How could I compile a 32Bit programme insread of the 64Bit one? I alreday read about the option "-m32" (here and in other threads), but where must it included? Is there a little how to?

---

