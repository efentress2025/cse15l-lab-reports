# Lab Report 1, Week 2
![image1](Lab_Report_1_Images\code.PNG)

Greetings, future students! (and future self!) This is my tutorial for how to log into your course-specific account on the “ieng6” server. While it seems formidable at first, it isn’t too bad once you break down the process. Without further ado, here are the details:

1. **Install VScode:** If you haven't already, make sure you install the program [Visual Studio Code](https://code.visualstudio.com/download) onto your computer. It is a streamlined code editor that is stylish and effective. Once you install the program, opening it up for the first time should produce a screen similar to this.
![image2](Lab_Report_1_Images\VScode_startup.png)

2. **Remotely Connecting:** To connect to the "ieng6" server, you will utilize a program called OpenSSH, which allows your computer to connect to other computers using specific accounts. If you are on Windows, make sure you have OpenSSH by downloading it [here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse). Once you have OpenSSH installed, look for your course-specific account in this index [here.](https://sdacs.ucsd.edu/~icc/index.php) Now you have everything you need to connect to a server in VScode.

    To begin the connection process, open up a new terminal in VScode and type in the command "ssh cs15lsp22[insert letters of your course-specific account]@ieng6.ucsd.edu". If this is the first time you are connecting to this server, you will likely get a message saying "The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established", followed by your RSA key fingerprint and the message "Are you sure you want to continue connecting (yes/no/[fingerprint])?"; say yes.

    After saying yes, the server will ask for your password. Provide your password, and you should then see something like this after you finish logging in.
    ![image3](Lab_Report_1_Images\ssh_login_complete.png)
