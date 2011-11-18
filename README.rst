Operating System From Scratch
-----------------------------

Step 03: x86 Protect Mode
`````````````````````````

If our OS supports only one architecture, I'll choose x86.
You won't be surprised by this.
Now let's study how the cpu works and, most importantly, how x86 protect mode works.

We're going to write some code when learning protect mode.
Soon you'll find a 512-byte boot sector is too small for us.
My solution to this problem is to test our code in FreeDOS_:

1. compile the assembly code to COM format::

     $ nasm foo.asm -o foo.com

2. create a new floppy image (say ``pm.img``) and copy the COM file to it::

     $ sudo mount -o loop pm.img /mnt/floppy
     $ sudo cp foo.com /mnt/floppy/
     $ sudo umount /mnt/floppy

3. "insert" the new floppy into the virtual machine by adding a line in ``bochsrc``::

     floppya: 1_44=freedos.img, status=inserted
     floppyb: 1_44=pm.img, status=inserted

4. run FreeDos::

     $ bochs

5. run our code::

     A:\>B:\foo.com

You can try the instructions above in directory ``b``.
Remember to replace ``foo.asm`` with the true source file name and unzip the image files first.

`‹prev`_   `next›`_

.. _FreeDos: http://www.freedos.org/
.. _`‹prev`: https://github.com/yyu/osfs02
.. _`next›`: https://github.com/yyu/osfs04
