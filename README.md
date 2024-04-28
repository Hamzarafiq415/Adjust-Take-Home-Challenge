# Solution to the Junior_Platform_Engineer_Challenge

## Initial Step
Hi, thank you for considering me for the next step and providing me with this exciting challenge "Junior_Platform_Engineer_Challenge.pdf"
The file contains instructions, random strings, and questions. Here's my attempt!

## Initial Step
- Firstly, I installed the "poppler-utils" using this command "sudo yum install poppler-utils" because I wanted to use pdftotext command as the file I have to create is "file.txt" from pdf.
- Seconldy, the pdf contains so much content other than random strings so I had to specify my starting point and ending point to only copy random strings in "file.txt".
- I used "awk" as its a powerful tool used for manipulating data and generating reports.
- Starting point is set after "Unset" as its header for my random strings and for the ending point I specified the last string mentioned in the document "Rwn8MLTbiQU05Py5kDvlM0j2zl76B1" because there's no other word specified there.
- After this, I got some output but it had page numbers(with the format 1/4, 2/4) in between, so to remove that I used the command:' !/^[0-9]+\/[0-9]+$/ ' This pattern matches lines that contain page numbers in the format x/y, where x and y are numeric page numbers. Lines matching this pattern are excluded to be part of file.txt.
- Lastly, I made sure there's no empty lines in the document so I used:' && NF '  This condition ensures that the line is not empty before printing.

## Final Command:
pdftotext -layout Junior_Platform_Engineer_Challenge.pdf - | awk '/Unset/{p=1; next} p && !/^[0-9]+\/[0-9]+$/ && NF {print; if ($0 ~ "Rwn8MLTbiQU05Py5kDvlM0j2zl76B1") exit}' > file.txt

## Output:
Now, I have created file.txt with all the random strings given in pdf document.

###############
### TASK!!! ###
###############

## Question 1: How many lines in this file?

Command: wc -l file.txt 
Output: 98

Explanation: It's a simple command which counts number of lines in a file. To make sure it doesnt count empty lines, I already removed empty lines while creating the file.txt.

## Question 2: How many “Z” Characters in this file?

Command: grep -o 'Z' file.txt | wc -l
Output: 44

Explanation: To count all occurrences of the character "Z" in the file, including multiple occurrences on the same line, we can use grep with the -o option to output each match on a separate line. After that, we can count the total number of matches using wc -l.

## Question 3: Find on which line is “Junior”, “Platform” and “Engineer”, not case sensitive.

Command: grep -niE 'Junior|Platform|Engineer' file.txt
Output:
28:      COJILxEOhBRPlatFormjc00OhTT6ve
65:      x7t2vMJunior0qcMHQtnVGhlggfnry
88:      7B6nmS3lLJaEngineeR28pzseTejdm

Explanation: I used "-ni" to perform a case-insensitive search and print the line numbers of matching lines, "E" to interpret the pattern as an extended regular expression, and pattern we are searching for, which matches any of the words "Junior", "Platform", or "Engineer".

## Question 4: Change “Junior” to “Senior”.

Command: sed -i 's/Junior/Senior/g' file.txt

Command to verfiy: grep -niE 'Senior|Platform|Engineer' file.txt 
Output: 
28:      COJILxEOhBRPlatFormjc00OhTT6ve
65:      x7t2vMSenior0qcMHQtnVGhlggfnry
88:      7B6nmS3lLJaEngineeR28pzseTejdm

Explanation: 'sed' is a stream editor for filtering and transforming text, 'i' for editing the file in place, 's/Junior/Senior/g' is a command in sed: 's: Indicates substitution', 'Junior: The pattern to search for', 'Senior: The replacement text', and 'g: Replace all occurrences on each line'.

**If you have any questions, please ask me**

 

