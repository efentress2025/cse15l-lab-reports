# Lab Report 5, Week 10
Hello everyone, Erick Fentress here, and welcome to the last lab report of the quarter! It's crazy to think that we're already at the end. Anyways, for this lab report, we're gonna be looking at testing discrepancies between two implementations of "markdown parser" and see what potential bugs are causing these inconsistencies. Without further ado, let's get into our last lab report!

---

After testing many files (600+) on both my implementation of markdown parser and an instructor-provided implementation, inconsistencies were discovered in the output of these tests between implementations. These discrepancies were discovered by outputting the results of each test file passed into either implementations into two respective "results.txt" files and looking for differences within these files using vim's "vimdiff" application.
 
 The first inconsistency was found within the test file "[194.md](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/194.md)", which should have an expected output of:
 
 ![expect1](Lab_Report_5_Images\expect1.png)

 But instead produced these outputs within the implementations:

 ![diff1](Lab_Report_5_Images\diff1.PNG)

 Neither implementation is technically correct, though the instuctor-provided implementation at least has the line “url.”

The problem with my implementation is that it only checks for the closing parenthesis at the end of a line, and nowhere else within the file/line. This bug assumes that the closing parenthesis is always located at the end of a line, which is not always the case and leads to the wrong output.

![bug1](Lab_Report_5_Images\bug1.png)

---

The second inconsistency I wanted to investigate was found within the test file "[487.md](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/487.md)", which should have an expected output of:

![expected2](Lab_Report_5_Images\expect2.png)

But instead has this output within the two implementations:

![diff2](Lab_Report_5_Images\diff2.png)

Between both implementations, my implementation was incorrect.

The bug within my implementation is that it considers everything within a pair of closed parenthesis as a link, no matter the contents. Since the “/” character seems to invalidate a link’s url, including links that are adjacent to this character is incorrect because the links do not work. To fix this issue, links should be checked to see if they contain the “/” character. 

![bug2](Lab_Report_5_Images\bug2.png)

---

And that's all for this week! I still can't believe that the quarter's already over. I really enjoyed making these lab reports, and I hope you enjoyed reading them as well. That's all for now, everyone. I hope to see you all again very soon!