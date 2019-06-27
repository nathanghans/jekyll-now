nexti didn't really help. Trying to take a deeper dive.

(gdb) run
Starting program: /home/nate/booksrc/char_array2 

Breakpoint 4, main () at char_array2.c:4
4	int main() {

So break main puts us at main+8

(gdb) i r rip
rip            0x5555555546b2	0x5555555546b2 <main+8>

What is that instruction?

(gdb) x/i $rip
=> 0x5555555546b2 <main+8>:	mov    rax,QWORD PTR fs:0x28

Ok. so what is in "QWORD PTR fs:0x28"?
(gdb) print qword ptr fs:0x28
No symbol "qword" in current context.
(gdb) print "qword ptr fs:0x28"
$1 = "qword ptr fs:0x28"

hmm, that doesn't help.

GOOGLE!!!!

https://stackoverflow.com/questions/10325713/why-does-this-memory-address-fs0x28-fs0x28-have-a-random-value

Ok. so FS points to structures defined by the OS or thread. So it's loading a structure of somekind. Maybe the char structure?? Maybe main itself? RAX - accumulator register. Hmm. let's keep going

(gdb) nexti
0x00005555555546bb	4	int main() {

What is the next instruction.
(gdb) x/i $rip
=> 0x5555555546bb <main+17>:	mov    QWORD PTR [rbp-0x8],rax

QWORD is a 8 byte value

Back to the previous instruction - what is  stored in rax? 
(gdb) x/x $rax
0x3224da24a6e8e700:	Cannot access memory at address 0x3224da24a6e8e700

Something protected. Ok.

What is it writing over?

(gdb) x/x $rbp
0x7fffffffdfc0:	0x55554710
(gdb) x/x $rbp -8
0x7fffffffdfb8:	0x00000000
(gdb) x/2x $rbp -8
0x7fffffffdfb8:	0x00000000	0x00000000
(gdb) x/3x $rbp -8
0x7fffffffdfb8:	0x00000000	0x00000000	0x55554710

8 bytes of 0s and then 0x55554710

Move on.

(gdb) nexti
0x00005555555546bf	4	int main() {

What is the next instruction:
(gdb) x/i $rip
=> 0x5555555546bf <main+21>:	xor    eax,eax

xor something to itself will equaly 0. Ok?

What was in rax? Can I see it now?

(gdb) x/x $rax
0x3224da24a6e8e700:	Cannot access memory at address 0x3224da24a6e8e700

Nope.

Ok. Let's see what it moved into rbp - 0x8
(gdb) x/3x $rbp -8
0x7fffffffdfb8:	0xa6e8e700	0x3224da24	0x55554710

0x55554710 is RBP itself.(base pointer)

This: 0xa6e8e700	0x3224da24
What is that in string?



(gdb) x/s $rbp -8
0x7fffffffdfb8:	""

What does that look like in other formats?

(gdb) x/2xw $rbp -8
0x7fffffffdfb8:	0xa6e8e700	0x3224da24
(gdb) x/6xb $rbp -8
0x7fffffffdfb8:	0x00	0xe7	0xe8	0xa6	0x24	0xda
(gdb) x/6ub $rbp -8
0x7fffffffdfb8:	0	231	232	166	36	218
(gdb) x/6cb $rbp -8
0x7fffffffdfb8:	0 '\000'	-25 '\347'	-24 '\350'	-90 '\246'	36 '$'	-38 '\332'
(gdb) x/s $rbp -8
0x7fffffffdfb8:	""
(gdb) x/2s $rbp -8
0x7fffffffdfb8:	""
0x7fffffffdfb9:	"\347\350\246$\332$2\020GUUUU"
(gdb) x/s $rbp -8
0x7fffffffdfb8:	""
(gdb) x/s $rbp -7
0x7fffffffdfb9:	"\347\350\246$\332$2\020GUUUU"
(gdb) x/s $rbp -9
0x7fffffffdfb7:	""
(gdb) x/s $rbp -10
0x7fffffffdfb6:	""
(gdb) x/s $rbp -16
0x7fffffffdfb0:	"\240\340\377\377\377\177"
(gdb) x/s $rbp -12
0x7fffffffdfb4:	"\377\177"
(gdb) x/s $rbp -11
0x7fffffffdfb5:	"\177"
(gdb) x/s $rbp -10
0x7fffffffdfb6:	""
(gdb) x/2s $rbp -10
0x7fffffffdfb6:	""
0x7fffffffdfb7:	""
(gdb) x/3s $rbp -10
0x7fffffffdfb6:	""
0x7fffffffdfb7:	""
0x7fffffffdfb8:	""
(gdb) x/5s $rbp -10
0x7fffffffdfb6:	""
0x7fffffffdfb7:	""
0x7fffffffdfb8:	""
0x7fffffffdfb9:	"\347\350\246$\332$2\020GUUUU"
0x7fffffffdfc7:	""
(gdb) x/x $rbp -8
0x7fffffffdfb8:	0x00
(gdb) x/xw $rbp -8
0x7fffffffdfb8:	0xa6e8e700
(gdb) x/xw $rbp -8
0x7fffffffdfb8:	0xa6e8e700

I ran this a separate time and this is what it showed:

(gdb) x/2xw $rbp -8
0x7fffffffdfb8:	0x75780d00	0xa3680de7

so the bytes changes each time. Ok. Good to know. Not sure what it means. let's move on.

let's not. hold up.

x/2xw shows 2 sets of 4 bytes

x/2s shows us a string. 

So running off of command "x/5s $rbp -10":

0x7fffffffdfb6:	""                                      <====notice this is 6, then 7 then 8. they are all filling one byte. Until....
0x7fffffffdfb7:	""
0x7fffffffdfb8:	""                                      <=========this is where RBP-8 points.
0x7fffffffdfb9:	"\347\350\246$\332$2\020GUUUU"          <=======================================================================here. Then this is fc7-fb9=14 bytes(https://www.calculator.net/hex-calculator.html?number1=fc7&c2op=-&number2=fb9&calctype=op&x=83&y=22)
0x7fffffffdfc7:	""




In my second run this is what x/8s $rbp -8 looks like:

(gdb) x/2s $rbp -8
0x7fffffffdfb8:	""
0x7fffffffdfb9:	"\rxu\347\rh\243\020GUUUU"             <=================This is also 14 bytes. $rbp itself is at "0x7fffffffdfc0" So that would be.... after \243. So rax was "\rxu\347\rh\243" but in the last instance it was ""\347\350\246$\332$2"


ok now lets move on.

What problem am I trying to solve. trying to understand what every little detail is is not helping.

So let's set out some goals. 

Where does it define the 20 character array?
Where does it pull "hello world from"?
Where does it print str_a?


So let's start with this one:

Where does it define the 20 character array?

my guess is this line from "disass main":
=> 0x00005555555546c1 <+23>:	lea    rax,[rbp-0x20]

Let's see what htis looks like BEFORE main+23 is run:

(gdb) i r rip
rip            0x5555555546c1	0x5555555546c1 <main+23>


(gdb) x/x $rbp -32
0x7fffffffeb30:	0x55554710



(gdb) x/x $rbp
0x7fffffffeb50:	0x55554710




(gdb) x/x $rbp - 32
0x7fffffffeb30:	0x55554710


Same string

(gdb) x/s $rbp - 32
0x7fffffffeb30:	"\020GUUUU"



(gdb) x/9xw $rbp - 32
0x7fffffffdfa0:	0x55554710	0x00005555	0x555545a0	0x00005555
0x7fffffffdfb0:	0xffffe0a0	0x00007fff	0xe7d6bc00	0x69540be2
0x7fffffffdfc0:	0x55554710

RBP is still: 0x55554710 the base of the stack is this address.

(gdb) x/x $rbp-32
0x7fffffffdfa0:	0x55554710

Hmm RBP-32 is the same address.
(gdb) x/x $rbp
0x7fffffffdfc0:	0x55554710

same string
(gdb) x/s $rbp
0x7fffffffdfc0:	"\020GUUUU"
(gdb) x/s $rbp -32
0x7fffffffdfa0:	"\020GUUUU"

0x7fffffffdfa0 is RBP-32
0x7fffffffdfc0 is RBP
So we only need to look at 9 bytes to see RBP AND RBP-32:

(gdb) x/9xw $rbp -32
0x7fffffffdfa0:	0x55554710	0x00005555	0x555545a0	0x00005555
0x7fffffffdfb0:	0xffffe0a0	0x00007fff	0xe7d6bc00	0x69540be2
0x7fffffffdfc0:	0x55554710


My guess is this is loading hte stack pointer into memroy before it goes off to strcpy function so it can find it again. without being able to follow the program into strcpy i can't confirm. hmmm.

lets see if we can fix that or find it in the book one of the two

OK - let's ignore strcpy on other function.s

following this to see if this helps shakes some concepts into place: https://www.recurse.com/blog/7-understanding-c-by-learning-assembly

The part on registers is amazing. BP - base pointer - base of the stack frame. SP - top of the stack frame. 

He also explains the function prologue. 

Registers are 64 bits aka 8 bytes

Interesting how he examines the variables from the program - definitely a tool to be used later.

rip and pc mean same thing. cool.

/* static.c */
#include <stdio.h>
int natural_generator()
{
        int a = 1;
        static int b = -1;
        b += 1;
        return a + b;
}

int main()
{
        printf("%d\n", natural_generator());
        printf("%d\n", natural_generator());
        printf("%d\n", natural_generator());

        return 0;
}

that was a good read. 

very interesting now how can we use it ?? 

let's start with char_array.c

   0x00000000000006aa <+0>:	push   rbp
   0x00000000000006ab <+1>:	mov    rbp,rsp
   0x00000000000006ae <+4>:	sub    rsp,0x20
   0x00000000000006b2 <+8>:	mov    rax,QWORD PTR fs:0x28
   0x00000000000006bb <+17>:	mov    QWORD PTR [rbp-0x8],rax
   0x00000000000006bf <+21>:	xor    eax,eax
   0x00000000000006c1 <+23>:	mov    BYTE PTR [rbp-0x20],0x48
   0x00000000000006c5 <+27>:	mov    BYTE PTR [rbp-0x1f],0x65
   0x00000000000006c9 <+31>:	mov    BYTE PTR [rbp-0x1e],0x6c
   0x00000000000006cd <+35>:	mov    BYTE PTR [rbp-0x1d],0x6c
   0x00000000000006d1 <+39>:	mov    BYTE PTR [rbp-0x1c],0x6f
   0x00000000000006d5 <+43>:	mov    BYTE PTR [rbp-0x1b],0x2c
   0x00000000000006d9 <+47>:	mov    BYTE PTR [rbp-0x1a],0x20
   0x00000000000006dd <+51>:	mov    BYTE PTR [rbp-0x19],0x77
   0x00000000000006e1 <+55>:	mov    BYTE PTR [rbp-0x18],0x6f
   0x00000000000006e5 <+59>:	mov    BYTE PTR [rbp-0x17],0x72
   0x00000000000006e9 <+63>:	mov    BYTE PTR [rbp-0x16],0x6c
   0x00000000000006ed <+67>:	mov    BYTE PTR [rbp-0x15],0x64
   0x00000000000006f1 <+71>:	mov    BYTE PTR [rbp-0x14],0x21
   0x00000000000006f5 <+75>:	mov    BYTE PTR [rbp-0x13],0xa
   0x00000000000006f9 <+79>:	mov    BYTE PTR [rbp-0x12],0x0
   0x00000000000006fd <+83>:	lea    rax,[rbp-0x20]
   0x0000000000000701 <+87>:	mov    rdi,rax
   0x0000000000000704 <+90>:	mov    eax,0x0
   0x0000000000000709 <+95>:	call   0x580 <printf@plt>
   0x000000000000070e <+100>:	mov    eax,0x0
   0x0000000000000713 <+105>:	mov    rdx,QWORD PTR [rbp-0x8]
   0x0000000000000717 <+109>:	xor    rdx,QWORD PTR fs:0x28
   0x0000000000000720 <+118>:	je     0x727 <main+125>
   0x0000000000000722 <+120>:	call   0x570 <__stack_chk_fail@plt>
   0x0000000000000727 <+125>:	leave  
   0x0000000000000728 <+126>:	ret    
End of assembler dump.


You can spot it almost instantly. moving into byte ptr

*****************display/i $pc**************
******x $register or x &var
**********gcc -g -o file c-file
************** gdb -q

word - 2 bytes(h)
dword - 4 bytes(w)
qword - 8 bytes(g)

The 'int' data type is		 4 bytes
The 'unsigned int' data type is	 4 bytes
The 'short int' data type is	 2 bytes
The 'long int' data type is	 8 bytes
The 'long long int' data type is 8 bytes
The 'float' data type is	 4 bytes
The 'char' data type is		 1 bytes


created this to see the assembler create variables of various sizes for the various types:

1	int main() 
2	{
3	int a = 1;
4	unsigned int b = -1;
5	short int c = 1;
6	long int d = 1;
7	long long int e = 1;
8	float f = 1;
9	char g = '1';
10	}


28   0x00000000000005fe <+4>:	mov    DWORD PTR [rbp-0x1c],0x1
24   0x0000000000000605 <+11>:	mov    DWORD PTR [rbp-0x18],0xffffffff
30   0x000000000000060c <+18>:	mov    WORD PTR [rbp-0x1e],0x1
16   0x0000000000000612 <+24>:	mov    QWORD PTR [rbp-0x10],0x1
8   0x000000000000061a <+32>:	mov    QWORD PTR [rbp-0x8],0x1
x    0x0000000000000622 <+40>:	movss  xmm0,DWORD PTR [rip+0x9a]        # 0x6c4
   0x000000000000062a <+48>:	movss  DWORD PTR [rbp-0x14],xmm0
   0x000000000000062f <+53>:	mov    BYTE PTR [rbp-0x1f],0x31
   0x0000000000000633 <+57>:	mov    eax,0x0
   0x0000000000000638 <+62>:	pop    rbp
   0x0000000000000639 <+63>:	ret    
