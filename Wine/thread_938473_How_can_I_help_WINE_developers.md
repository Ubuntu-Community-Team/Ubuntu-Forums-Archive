---
title: "How can I help WINE developers?"
date: 2008-10-04
forum: Wine
---

### Post by askyourpc.com on 2008-10-04
I am studying software engineering and would like to know how I could help further develop wine. Are there jobs for wine or Linux?

---

### Post by DoktorSeven on 2008-10-04
Generally Wine and other open-source projects allow you to contribute help but due to their open nature, there's generally few to no steady paying jobs to be had there.  Not sure if Wine has anything or not, but there are jobs at several Linux-related companies (I'm sure Canonical has something, for example).

[Here's how you'd contribute to Wine](http://www.winehq.org/site/contributing), for example.

---

### Post by asdfoo on 2008-10-05
> **askyourpc.com said:**
> I am studying software engineering and would like to know how I could help further develop wine. Are there jobs for wine or Linux?

Wine is mostly ANSI C, so you should be proficient in C if you want to fix bugs and knowledge of x86 assembly helps with investigating crashes and such.  The C Programming Language by K&R is _the_ canonical book when it comes to C.

[http://www.amazon.com/Programming-Language-Prentice-Hall-Software/dp/0131103628](http://www.amazon.com/Programming-Language-Prentice-Hall-Software/dp/0131103628)


If you have a good working knowledge of C then you can browse the Wine bug tracker for issues you'd like to investigate, if you think you've discovered cause of the problem them you write a testcase to reproduce the problem to test if it passes/fails on Windows.   Then you write the fix to make your testcase pass under Wine.

---

### Post by jim_24601 on 2008-10-06
There are a very few people paid to work full-time on Wine, yes, but I doubt there are any vacancies, and if there were I'd expect that you'd have to have been active in the Wine development scene for quite some time before being considered.

As a developer, you contribute to Wine by:
Finding an app that doesn't work, and making it work.
Finding a test that fails, and making it pass. (There's a big push on at the moment to get the test suite to pass cleanly on "normal" machines--when there's a huge buzz amongst the community at the news that TWO machines in the known world pass the test suite cleanly as opposed to just one, you know the suite has some problems.)
Finding a bug in the app database, and fixing it.

There are a few Huge Tasks, but you're unlikely to get very far attacking one of those straight off. What's holding Wine back more than anything is all the little incompatibilities--the quirks of Windows that are undocumented but that some app, somewhere, is bound to rely on.

When you have written your fix and thoroughly tested it, you submit a patch or a set of patches to the wine-patches mailing list and wait. If the patch is accepted it will appear on the wine-cvs mailing list and go into the next Wine version. It may attract comments on the development mailing list, in which case you are expected to address the comments and submit a revised patch.
A patch is more likely to be accepted if it:
Complies with the Wine coding guidelines. (Basically, no C++ comments, and follow the style of the code you're editing.)
Is small and limited in scope.
Is Obviously Correct. Unfortunately only Alexandre Julliard really knows what Obviously Correct means ;)
Includes a test case demonstrating the bug and that it was fixed.

Wine is written in C, so obviously you need to know C. More than a passing familiarity with the Windows API is also a plus. MSDN is helpful, but it's patchy, incomplete and often inaccurate if not flat wrong, so you've pretty much got to write a test program and run it on Windows if you want to know what's really going on anyway. The Wine codebase is large, badly organised and kludgy, not through any fault of the Wine team but because the API it's implementing is large, badly organised and kludgy. But when you get down to it, it's only code ;)

---

