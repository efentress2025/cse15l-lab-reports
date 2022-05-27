# Lab Report 4, Week 8
Hello everybody. Erick Fentress here! Welcome to yet another lab report by yours truly. Today, we are going to observe how two different implementations of the program "markdown parser" run when they are presented with three different test files. Without further ado, let's jump straight into things.

---

First of all, the implementions I will be using for this demonstration are my own implementation and another implementation created by some of my peers:

* [My implementation](https://github.com/notweezer123/markdown-parse)
* [Peer implementation](https://github.com/YoavGutmanUCSD/markdown-parser-2)

As I stated in the introduction, for each of these implementations I will be running three tests on them to see if they return correct behavior.

---
**snippet-1.md**

The first test file I have contains several links with backticks surrounding them:

![image1](Lab_Report_4_Images\snippet-1.PNG)
![image1Test](Lab_Report_4_Images\snip1Test.PNG)

This is the expected output:

![image1Expect](Lab_Report_4_Images\snip1Expect.png)

Executing this test on my implementation caused this error:

![test1ErrormyImp](Lab_Report_4_Images\test1ErrorMyImp.png)

Executing this test on my peers' implementation caused this error:

![test1ErrorPeerImp](Lab_Report_4_Images\test1ErrorPeerImp.png)

In regards to making my implementation work for tests like this that have code with backticks, I could check to see if the index before or after an open bracket contains a backtick (if so, don't include its link), and also I could create a while-loop within my code that decrements backwards starting from the last index of the current line I am parsing. The code will check if the current index contains a closed parenthesis character; if it does, execute the rest of the function as normal; if not, skip to the next line of the file. I will also include a “replace()” method call that will replace any backtick characters in my “stringToAdd” with empty strings.

---
**snippet-2.md**

The second test I have contains nested parentheses, brackets, and escaped brackets:

![image2](Lab_Report_4_Images\snippet-2.PNG)
![image2Test](Lab_Report_4_Images\snip2Test.png)

This is the expected output:

![image2Expect](Lab_Report_4_Images\snip2Expect.png)

Executing this test on my implementation caused this error:

![test2ErrorMyImp](Lab_Report_4_Images\test2ErrorMyImp.png)

Executing this test on my peers' implementation caused this error:

![test2ErrorPeerImp](Lab_Report_4_Images\test2ErrorPeerImp.png)

To make my implementation work for files that have nested parentheses, brackets, etc., I could simply add some replace() method calls that replaces these characters in my “stringToAdd” with empty strings. Also, to make sure my program doesn't grab a link that is right after a nested link in brackets, I could check to see if there is a closed parenthesis located two indexes before a link's open parenthesis. If there is, this link is not valid.

---
**snippet-3.md**

The third test I have contains newlines in brackets and parentheses:

![image3](Lab_Report_4_Images\snippet-3.PNG)
![image3Test](Lab_Report_4_Images\snip3Test.png)

This is the expected output:

![image3Expect](Lab_Report_4_Images\snip3Expect.png)

Executing this test on my implementation caused this error:

![test3ErrorMyImp](Lab_Report_4_Images\test3ErrorMyImp.png)

Executing this test on my peers' implementation caused this error:

![test3ErrorPeerImp](Lab_Report_4_Images\test3ErrorPeerImp.png)

To make my implementation work for files that contain newlines in brackets and parentheses, I would have to completely rewrite my getLinks() method. Instead of parsing each individual line of the file for a link, I would have to parse the entire file (as one big string) and utilize alternative methods - such as checking to see if an open parenthesis is followed by a new line or not - to parse the links.

---

And that's it for this week's lab! I hoped you learned a bit about parsing links through this analysis, and I will see you all very soon. Goodbye!