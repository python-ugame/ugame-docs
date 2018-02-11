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

.. note::
    Please remember to always "remove" or "unmount" the filesystem after
    copying or editing any files before unpluggin or hard-resetting the
    device (the automatic soft-reset is fine). If you don't, and a writing
    operation gets interrupted, you might accidentally corrupt your filesystem
    and have problems with the files afterwards. If that happens, see further
    down this page for troubleshooting options.

Writing Files
-------------

By default, the filesystem can be written to from your computer through the USB
port, but is read-only for your program. In order to be able to write to the
files, or create new ones, you first have to re-mount the filesystem as
read-write — this has to happen before the USB connection is made, so the code
that does that has to go into the special `boot.py` file. But since only one
thing can have write access to the filesystem, that means you will no longer be
able to write files through USB from your computer. `Detailed explanation is
available from Adafruit tutorials.
<https://learn.adafruit.com/cpu-temperature-logging-with-circuit-python/writing-to-the-filesystem>`_

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
check the console for any messages. `This Adafruit tutorial explains how to access the console.
<https://learn.adafruit.com/welcome-to-circuitpython/kattni-connecting-to-the-serial-console>`_


Other Considerations
--------------------

Generally speaking, µGame is a CircuitPython device, compatible with the
Adafruit M0 boards, and behaves exactly the same as those boards.


Troubleshooting
===============


Errors
------

If you have uploaded your program but it's not working, or works for some time
then abruptly stops, you have probably hit an error. To see what the error is
exactly, you need to access the serial console, as explained above, and then
you will see what the error is and on which line of your program.


Corrupted Filesystem
--------------------

It you unplug µGame from your computer while files are still being copied, it
can happen that the filesystem gets corrupted. When that happens, the surest
way to recover is to copy all the important files to a safe place on your
computer and format the filesystem on the µGame. To make that easy, there is
a special firmware that will do it for you.

First, you need to download the `format.uf2
<https://github.com/python-ugame/ugame-10-hardware/raw/master/firmware/format.uf2>`_
and `firmware.uf2
<https://github.com/python-ugame/ugame-10-hardware/raw/master/firmware/firmware.uf2>`_
files. Once you have them, connect your µGame to your computer, and press the
reset button twice, so that it switches into the bootloader mode. A disk called
`TRINKETBOOT` should appear, with some files on it. When it does, copy the
`format.uf2` file on it, and wait for the device to reset. Your flash is now
formatted. Now press reset twice again, and this time copy the `firmware.uf2`
file onto the disk, to get back to the CircuitPython firmware. When the device
resets, you should see a brand new empty `CIRCUITPY` disk.
