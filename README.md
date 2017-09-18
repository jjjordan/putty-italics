# Putty italics patch

This repository contains a patch that enables italics in the Windows version
of PuTTY.  Italics text was specified in ECMA-48 *in 1976*, yet terminal
emulator support for it has only caught on somewhat recently.  Support
exists in many libvte-based terminals, but to date it's not even on the
[PuTTY wishlist](https://www.chiark.greenend.org.uk/~sgtatham/putty/wishlist/).

I'd like to eventually submit this patch upstream, however, it would likely
require implementations for the other operating systems, and some fairly
thorough testing before it would be accepted...

## Screenshots

### With italics

![With Italics](https://raw.githubusercontent.com/jjjordan/putty-italics/master/screenshots/with-italics.png)
*The [JOE Editor](https://sf.net/p/joe-editor) with the Zenburn color scheme*

### Without italics

![No Italics](https://raw.githubusercontent.com/jjjordan/putty-italics/master/screenshots/no-italics.png)

### Font support

The patch is a bit picky about which fonts it will allow.  Many monospaced
fonts do not have a native italics face, and instead rely on the Operating
System to apply a linear transformation for an "Oblique" face.  They wind up
overhanging the next glyph and cause generally bad artifacts during
painting.  For this reason, the patch rejects any font without a true
Italics face.

These fonts, however, are known to work:

* [Anonymous Pro](https://www.marksimonson.com/fonts/view/anonymous-pro)
* Consolas
* Courier New
* [Hack](http://sourcefoundry.org/hack/)
* [Operator Mono](https://www.typography.com/fonts/operator/overview/)
* [Ubuntu Mono](http://font.ubuntu.com/)

