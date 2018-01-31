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
