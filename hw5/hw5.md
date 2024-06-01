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

I see two cmps, and I know that 0x1 is 1 in decimal so that the first input should be 1. The second one seems to use eax which is changing in a loop I assume, so we will find out what it is for each iteration.

![image 14](image-13.png)

Odin ID: 945912805
PSU ID: ncallon
PSU email: ncallon@pdx.edu
