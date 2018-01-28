Usage Manual
************

Filesystem
==========

In order to start programming your µGame, connect it to any USB port of your
computer using a micro-USB cable. Unless you are running Windows 7, you won't
need any special drivers (`the drivers for Windows 7 are available at Adafruit
<https://learn.adafruit.com/welcome-to-circuitpython/installing-circuitpython#windows-7-drivers>`_). As soon as you connect your device, you should see a new
disk driver labeled "CIRCUITPY" appear. If you browse it, you will either see
some demo program already there, or just an empty disk.

You can put any files on that disk, but a few of them have a special meaning.
A file called `main.py` will be executed every time the device is powered on or
restarted. Any other `.py` and `.mpy` files that you save there will become
available to be imported from `main.py` and used as libraries or programs.

You will also want to save some `.bmp` and `.wav` files to be used by your
game, and possibly also some text files with level definitions and the like.

Finally, you will probably find a `boot_out.txt` file appearing on that disk
every time the device is restarted — it contains diagnostic information about
the device and the firmware on it.

By default, the filesystem can be written to from your computer through the USB
port, but is read-only for your program. In order to be able to write to the
files, or create new ones, you first have to re-mount the filesystem as
read-write — this has to happen before the USB connection is made, so the code
that does that has to go into the special `boot.py` file. But since only one
thing can have write access to the filesystem, that means you will no longer be
able to write files through USB from your computer. `Detailed explanation is
available from Adafruit
tutorials.<https://learn.adafruit.com/cpu-temperature-logging-with-circuit-python/writing-to-the-filesystem>`_

If you want to be able to save the player's progress, you can also use a small
area of non-volatile memory available for that purpose through the `nvm`
module.


Console
=======

You also have access to an interactive Python console (also called REPL) over
the USB connection. You can use it to experiment with Python commands and
explore the device, but it's also very useful for debugging, as you can see
everything your program prints in there, and also the text of any exceptions
raised. If your program doesn't work and you don't know why, it's best to first
check the console for any messages. `This Adafruit tutorial explains how to access the console.<https://learn.adafruit.com/welcome-to-circuitpython/kattni-connecting-to-the-serial-console>`_


Other Considerations
====================

Generally speaking, µGame is a CircuitPython device, compatible with the
Adafruit M0 boards, and behaves exactly the same as those boards.
