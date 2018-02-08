Limitations and Workarounds
***************************

The µGame is a very simple platform, and as such has certain limitations. The
one you are most likely to hit is the limited memory of the device. With 32kB
of RAM, and most of it taken by the interpreter, there is a limit of how large
your game can be. The limit is especially painful when it comes to graphics,
which tend to take up substantial amounts of memory. For example, you will only
be able to keep about two or three banks in memory at a time.

The second limitation is the speed of display refresh. With only 24MHz SPI
communication between the microcontroller and the display, there is a limit on
how many pixels you can update in a single frame — roughly ¼ of the screen. If
you try to update more, your game will start skipping frames and you will see a
tearing effect. This is fine if it happens from time to time, but it makes it
impossible to do things like full-screen scrolling.

Finally, you only have one sound channel, and the software can only play one
WAV file at a time. There is no mixing of multiple sounds and no way to have
a background music.

There are of course ways to cheat and overcome those limitations, but they are
a bit tricky, and don't work in all situations.


Save Banks
==========

Try to use as few banks of graphics as possible. You can put both grid tiles
and sprites in the same bank, if you have the room. Or tiles for several
different grids.


Rotate and Flip
===============

Sprites have a "rotation" parameter that you can change to rotate and flip the
image -- this way you don't have to have a separate graphic for every possible
orientation. It's for example common to do walking animation by just mirroring
the graphic of the walking person repeatedly, to make it seem like first one
and then the other foot is forward.


Palettes
========

Both grids and sprites let you use a different palette than the default one
assigned to a given bank. And since palettes are much smaller than banks, you
can have much more of them. Re-coloring the graphics lets you change the feel
of a level, distinguish between the player character and the enemies,
distinguish between different item types, etc. Since the magenta color is
always transparent, no matter where it appears in the palette, you can even
remove parts of the graphics by using a palette in which they are transparent.


Compiling
=========

The source code of your program is also taking up space, and as it grows, at
some point it will exceed the limits of the device. You can postpone that
moment a little by using a pre-compiled bytecode instead of plain-text source.
You can download the ``mpy-cross`` utility from `CircuitPython releases page
<https://github.com/adafruit/circuitpython/releases/tag/2.2.0>`_ and use it to
create a ``.mpy`` file that you can copy instead of the source, and that will
use less memory.


Unloading
=========

You can also save memory by explicitly removing the things you no longer need
from memory using the ``del`` statement. For example, you only need the data
and graphics for the current level, and as soon as the player goes to the next
one, you can replace that with the data for the new level. However, this won't
always work perfectly, because of memory fragmentation.
