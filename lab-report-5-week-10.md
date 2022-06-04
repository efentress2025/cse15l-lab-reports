# Lab Report 5, Week 10
Hello everyone, Erick Fentress here, and welcome to the last lab report of the quarter! It's crazy to think that we're already at the end. Anyways, for this lab report, we're gonna be looking at testing discrepancies between two implementations of "markdown parser" and see what potential bugs are causing these inconsistencies. Without further ado, let's get into our last lab report!

---

After testing many files (600+) on both my implementation of markdown parser and an instructor-provided implementation, inconsistencies were discovered in the output of these tests between implementations.
 
 The first inconsistency was found within the test file "[194.md](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/194.md)", which should have an expected output of:
 
 ![expect1](Lab_Report_5_Images\expect1.png)

 but instead produced these outputs within the implementations:

 ![diff1](Lab_Report_5_Images\diff1.PNG)

 Neither implementation is technically correct, though the instuctor-provided implementation at least has the line “url.”

The problem with my implementation is that it only checks for the closing parenthesis at the end of a line, and nowhere else within the file/line. This bug assumes that the closing parenthesis is always located at the end of a line, which is not always the case and leads to the wrong output.

![bug1](Lab_Report_5_Images\bug1.png)

---

The second inconsistency I wanted to investigate was found within the test file "[487.md](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/487.md)"

![]
