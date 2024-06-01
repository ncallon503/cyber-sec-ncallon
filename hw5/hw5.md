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

Odin ID: 945912805
PSU ID: ncallon
PSU email: ncallon@pdx.edu
