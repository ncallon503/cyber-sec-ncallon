# Homework 2 Feedback Sheet

### Student

**ODIN: ncallon**

## Grade (97/100)

- [] Downloaded Linux textbooks
- [x] Completed THM Linux Funadmentals Room Part 1
- [x] Completed THM Linux Modules Room 
##### grep tasks
- [x] All lines that contain the word “password” (case-sensitive)
- [x] All lines that contain “password” (case-insensitive)
- [x] All lines that end with exactly 3 numerical digits - WITH an anchor
- [] All lines that end with exactly 3 numerical digits - WITHOUT an anchor
- [] All lines that contain exactly 3 numerical digits, in any position (do not have to be adjacent, just 3 total)
##### sed tasks
- [x] Task 5.1
- [x] Task 5.2
- [x] Task 5.3
##### objdump, nm, readelf on /bin/ls
- [x] Task 6, question 1 for all three tools
- [x] Task 6, question 2 for all three tools
- [x] Task 6, question 3 for all three tools
##### virtual environment
- [x] Virtual Environment shell function
##### awk, cut, grep
- [x] Task 8, question 1
- [x] Task 8, question 2 
- [x] Task 8, question 3 
- [x] Task 8, question 4


## Comments
Good work! 

-1 No documentation of textbook downloads

-2 Missing without-an-anchor regex. Regex to find all lines that contain exactly three digits in any postion - wrong behavior
The with vs without anchor commands can be done like this:
with an anchor `grep -P '(?<!\d)\d{3}(?!\d)$'`
without an anchor `grep -P '(?<!\d)\d{3}(?!\d)\Z`
They should return the same wc since they perform the same task
All lines that contain exactly 3 numerical digits, in any position (do not have to be adjacent, just 3 total) `grep -P '^(.*\d.*){3}$'`
