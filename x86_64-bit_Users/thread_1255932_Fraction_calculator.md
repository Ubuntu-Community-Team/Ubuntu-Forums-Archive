---
title: "Fraction calculator"
date: 2009-09-02
forum: x86 64-bit Users
---

### Post by acidblue on 2009-09-02
Looking for a calculator in the repos that does fractions.
Any one know of one ?

All the ones i installed don't seem to do fractions.

---

### Post by bear24rw on 2009-09-02
what do you mean "does fractions"

---

### Post by prshah on 2009-09-02
Both the regular calculator (Applications-Accessories-Calculator) and command line calculator (apcalc) handle fraction input, but the result is always in decimals.

For the regular calculator, you have to switch to advanced mode (View-Advanced) to reveal the "frac"(tion) button; a typical calculation/result will be ```
Frac(3/4)+Frac(3/4)=1.5
```

The same with apcalc (command line calculator)```
sudo apt-get install apcalc
calc 3/4+3/4
          1.5

```

---

### Post by Slim Odds on 2009-09-02
speedcrunch is nice

---

### Post by acidblue on 2009-09-02
Aha! the FRAC function.
It was hidden under the advanced/scientific mode.
Is there a way to get a fraction result other than the decimal?
Or am i stuck with decimal?

---

### Post by Slim Odds on 2009-09-02
There is no need for the "FRAC" function in that example.

Frac(4/2) = 0

---

