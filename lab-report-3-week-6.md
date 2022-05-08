# Lab Report 3, Week 6
Hello, once again, everyone. Welcome back to another lab  report by Erick Fentress! Today, we will be looking at some tricks that streamline the process of logging into and pushing changes from a remote server's repository, as well as facilitating the copying of files to-and-from the server's repository. Without further delay, let's get right into things!

---

**1. Streamlining ssh Configuration**

In order to log into the "ieng6" server without having to append my username to the end of the "``ssh ieng6@[username]``" command, I made a "config" file in my local ".ssh" directory with information about the host I want to connect to, my login credentials, and my login keygen file.

![image1](Lab_Report_3_Images\configFile.PNG)

After making this file, I am able to login to the "ieng6" server effortlessly.

![image2](Lab_Report_3_Images\sshLoginNoUser.PNG)

To demonstrate this further, here is a ``scp`` command done into the "ieng6" server with no credentials required.

![image3](Lab_Report_3_Images\scpWithConfig.PNG)

---

**2. Setup Github Access from ieng6**

In order to push changes from the "ieng6" repository to the origin repository, I generated a public and private key pair within the ieng6 server and connected it to my Github account:

*Public key*
![Image4](Lab_Report_3_Images\pubGithubKey.PNG)

*Private key (id_rsa_github)*
![Image5](Lab_Report_3_Images\pubPrivieng6Key.PNG)

After making this connection, I was able to push committed changes directly from within the ieng6 server to the origin:

![Image6](Lab_Report_3_Images\gitPush.PNG)

[(Link to the ieng6 commit)](https://github.com/notweezer123/cse15l-lab-reports/commit/f5ba7d45a60e0ef3911e6cab42ae36632c8ec9a1)

---

**3. Copy whole directories with scp -r**

By utilizing the command ``scp -r``, which stands for "secure copy recursive", I am able to copy all of the files within a specified directory within having to tediously copy each and every one of them with single commands.

![image7](Lab_Report_3_Images\copyLine.PNG)

![image8](Lab_Report_3_Images\testLine.PNG)

To illustrate how useful this command is, here is an example of a one-line command that both copies over the files from the repository "markdown-parse" to ieng6 and runs it on the server:

![image9](Lab_Report_3_Images\oneLine.PNG)

---

That's everything for this report. I hope you learned a lot about these various tools I've utilized, and I will see you very soon!