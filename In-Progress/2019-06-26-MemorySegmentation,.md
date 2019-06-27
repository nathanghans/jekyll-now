Page 69

Memory Segmentation

Step 2 says "Adds the byte length of the instruction to EIP"

What does that mean - what byte length?

Here is a good SO on the topic: https://stackoverflow.com/questions/18802352/program-proccessing

Using the book, let's go back to page 25 - the start of section 0x253 Assembly Language

There are 2 lines:

8048375: 89 e5      mov   ebp,esp
8048377: 89 ec 08   mov   esp,0x8

You see how line 8048375 has 2 bytes? "89" is one byte and "e5" is another byte.

Notice how 8048377 is 2 more than 8048375? 2 is the byte length of the instruction at 8048375.

Another example:

Flip to page 26

804838b:    83 7d fc 09     cmp   DWORD PTR [ebp-4],0x9
804838f:    7e 02           jle   8048393 <main+0x1f>
8048391:    eb 13           jmp   80483a6 <main+0x32>

804838b is 4 bytes.

804838f is 4 more than 804838b

804838f is 2 bytes

8048391 is 2 more than 8048391.

I hope this has become as clear to you as it is to me.

If you are curious how to get the format of the code like on page 25 and 26 - refer to the objdump on page 22(i recommend running objdump without "grep" at least once - it is a trip)
