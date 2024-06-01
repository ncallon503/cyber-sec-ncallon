# Nathan Callon, 6/1/2024, Intro to Security, Homework 4

## Running the bomb with gdb + gef for the first time:

![image 1](image.png)

Stepping through with next after b main:

![image 2](image-1.png)

Found initialize_bomb() function:

![image 3](image-2.png)

Bomb blown up, going to use objdump and string to generate text files I can use:

![image 4](image-3.png)

objdump:

![image 5](image-4.png)

strings:

![image 6](image-5.png)

Found the text when phases are defused, including a secret stage:

![image 7](image-6.png)

![image 8](image-7.png)

Attempting different interesting strings I found in the string.txt, but not working:

![image 9](image-8.png)

Think I finally found a clue! About to test it:

![image 10](image-9.png)

Worked!! Phase 1 done.

"Public speaking is very easy."

![image 11](image-10.png)

I notice a read_six_numbers function and explode_bomb functions for phase_2.

![image 12](image-11.png)

With read_six_numbers, I'm testing first with "1 2 3 4 5 6" just to see what the assembly will do with the numbers I put, and so I can check the registers.

![image 13](image-12.png)

I see two cmps, and I know that 0x1 is 1 in decimal so that the first input should be 1. The second one seems to use esi+ebx\*4 and eax which are changing in a loop I assume, so we will find out what it is for each iteration.

![image 14](image-13.png)

I look at the first compare (that's not the obvious 0x1) using the "until \*0x08048b7e" command at the address and I use "i r" to see eax is 0x2, or 2 in decimal.

![image 15](image-14.png)

I use the same until agin, and now I see 0x6, or 6. Now I am trying "1 2 6 4 5 6".

![image 16](image-15.png)

I repeat and I see 0x18 (24), and add this so I now I have "1 2 6 24 5 6".

![image 17](image-16.png)

Now found 0x78, which is 120.

![image 18](image-17.png)

Found 0x2d0, which is 720.

Now input "1 2 6 24 120 720", and wallah! It worked.

![image 19](image-18.png)

For phase_3, the first thing I notice is many different cmps followed by explode_bomb. I notice the first compare uses 0x80497de for eax.

![image 20](image-19.png)

It seems the input wants an integer, then a character, then an integer:

![image 21](image-20.png)

To get further into the code, I use the pattern "1 a 1", aka int char int, to see where it takes me now.

I see that the first value after the lea assembly line to be compared is 0xd6 or 214.

![image 22](image-21.png)

I now try this with "1 a 214", as 1 worked for the first digit.

I see that bl is the final compare, and I use "until \*0x8048c8f" to be able to see bl in the latest context, which despite giving weird errors shows me the value "0x62".

![image 23](image-22.png)

I know that this is a character, so if we use a ASCII table to see 0x62, and we go to the ASCII table and see which character this corresponds to:

![image 24](image-23.png)

So I am now trying "1 b 214":

And it works!

![image 25](image-24.png)

I set a breakpoint at phase_4, and I start out by seeing the same sscan format checker I saw in phase_3:

![image 26](image-25.png)

Odin ID: 945912805
PSU ID: ncallon
PSU email: ncallon@pdx.edu
