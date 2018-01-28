Bouncing Ball Tutorial
**********************

To learn how to write games for µGame, it's best to start with a practical
example. We will try to make a simple demo, showing on the screen a moving
ball, bouncing off the screen edges. It's very simple, but demonstrates some
of the most important concepts that you will need to know.

Clean Slate
===========

We don't want anything to interfere in our tutorial, so lets start with making
sure that everybody is starting with the same state. There are probably some
files on your µGame right now — perhaps a demo program it came with, perhaps
the remnants of earlier experimentation. Please copy those files somewhere safe
on your computer, and then delete all the files from the `CIRCUITPY` drive.

The Main File
=============

Now, create a file called `main.py`, and open it in a text editor. This is
going to be where we put all the code. Later on, with more complex projects,
you will be probably using multiple Python files, but for now everything will
go into `main.py`.

Please also open a serial console, as described in the usage manual, so that
you can see all the messages and errors.

Now type the first few lines of the program, and save it::

    import ugame
    import stage

Once you hit "save", you should see in the console that the board restarts and
runs your program. For now there should be no effect of running it, it just
imports the two libraries that we are going to use later. If you made a mistake
somewhere, however, you will see an error printed on the console, telling you
the line number where the error is. Correct it and save again, and the board
will restart again and run your code.

Banks
=====

All the graphics used in µGame is organized into so-called "banks": sets of 16
images, 16×16 pixels each, with a 16-color palette. You probably noticed that
we like the number 16 — it really simplifies a lot of things.

For our bouncing ball demo, we are only going to use a single bank, because we
only need 5 images: one for the background, and four for the animated ball. The
bank we are going to use looks like this:

.. image:: images/ball.bmp

Now please right-click on that image, select "save as", and save it onto your
`CIRCUITPY` disk as `ball.bmp`, next to the `main.py` file. This way we will be
able to load it into memory and use in our demo.
