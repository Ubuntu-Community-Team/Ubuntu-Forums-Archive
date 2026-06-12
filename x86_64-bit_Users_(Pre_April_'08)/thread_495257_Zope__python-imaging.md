---
title: "Zope  python-imaging"
date: 2007-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Licicin on 2007-07-07
Hi i have a problem with the program below:

def code(self):
  image = Image.new('RGB', (48, 18), (255, 255, 255))
  font = ImageFont.load_default()
  draw = ImageDraw.Draw(image)
  draw.text((0, 0), 'test', font = font, fill = (0, 0, 0))
  image.save(sys.stdout,"PNG")

it works fine in python environment
but fails as Zope External method

What should be done besides apt-get install python-imaging ?

Thanks.

---

### Post by xzero1 on 2007-08-28
You might try posting in the correct forum.

---

