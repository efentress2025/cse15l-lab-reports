# Lab Report 2, Week 4
Greetings. Welcome back to another lab report by your resident coder, Erick Fentress. For this report, I will be showcasing how me and my lab partners fixed bugs present within a parsing program we were provided. Without further ado, let's do this!

So, first of all, our group had some trouble initially trying to debug the errors produced by our test inputs, so were stumped as to what sort of changes to make to the "MarkdownParser" program we were given. Eventually, we were able to resolve all of the bugs we were experiencing with one simple and effective fix:

![image1](Lab_Report_2_Images\code_fix1.PNG)

We split up our markdown file into an array of strings (using new lines as a delimiter) and used a conditional statement on each element to see if any open parenthesis were present in the element. If they were, then we searched for the open parenthesis using the "indexOf();" command, and searched for the closed parenthesis by returning the character present at the end of the line, which was the closing parenthesis (assuming that each link was followed by a new line). This change fixed the issues we were having with our input files; though this  change was the only fix we comitted to our respository, so there are no other screenshots to report our code differences.

Nevertheless, I will provide the failure-inducing inputs and explain the relationship between them and the bugs and symptoms they create:

---

[**test-file3.md**](https://github.com/notweezer123/markdown-parser/blob/main/test-file3.md)

![image2](Lab_Report_2_Images\test-file3_error.PNG)

This file caused the initial program to produce the above symptom (i.e. a StringIndexOutOfBounds exception). This symptom was caused by a bug in the program wherein if there was no closing parenthesis (or opening parenthesis), the index of the closing parenthesis would be -1 (the value that is returned if a character that is being looked for doesn't exist in a string). This -1 index would cause the program to attempt create a substring from indices 0 to -1, creating an StringIndexOutOfBoundsException and crashing the program.

---

[**test-file4.md**](https://github.com/notweezer123/markdown-parser/blob/main/test-file4.md)

![image3](Lab_Report_2_Images\test-file4_error.PNG)

This input caused the program to produce a symptom in the form of an "OutOfMemory" error. This error was caused by a bug in the program where the "currentIndex" variable would perpetually be 13 - creating an infinite loop. This happens because the currentIndex variable is used to find a new pair of brackets in the file, and since there are none, -1 will be returned everytime - causing the program to loop through the same line of text over and over again.

---

***UPDATE:***

In the process of further testing the program, I ran into some errors that required me to make changes to the code:

![image4](Lab_Report_2_Images\code_fix2.PNG)

While the code was executing fine on my lab partners' MacOS coding software, I was encountering bugs on my windows implementation, so I made some changes to make sure I produced the same results on both OSs. What I did was add conditional statements that checked whether the current string "s" was the last line in the "lines" array, since my program did not format the links correctly if it was. The other additions to the code have to do with my next failure-inducing input: 

[**test-file5.md**](https://github.com/notweezer123/markdown-parser/blob/main/test-file5.md)


![image5](Lab_Report_2_Images\test_file5_error.PNG)

This input produced a symptom in the form of an array with a link containing unnecessary white spaces. This incorrect output was caused by a bug in the program where a substring of everything within the parenthesis - white space or otherwise - would be created. To rectify this, I used the "replaceAll()" command to get rid of the white spaces in the substring.

---

I hope this was a good explaination of the symptoms and bugs produced by these inputs. That is all for this lab report. I hope you enjoyed reading and I will see you very soon!
