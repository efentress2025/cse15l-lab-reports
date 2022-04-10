# Lab Report 1, Week 2
![image1](Lab_Report_1_Images\code.PNG)

Greetings, future students! (and future self!) This is my tutorial for how to log into your course-specific account on the “ieng6” server. While it seems formidable at first, it isn’t too bad once you break down the process. Without further ado, here are the details:

1. **Install VScode:** If you haven't already, make sure you install the program [Visual Studio Code](https://code.visualstudio.com/download) onto your computer. It is a streamlined code editor that is stylish and effective. Once you install the program, opening it up for the first time should produce a screen similar to this.
![image2](Lab_Report_1_Images\VScode_startup.png)

2. **Remotely Connecting:** To connect to the "ieng6" server, you will utilize a program called OpenSSH, which allows your computer to connect to other computers using specific accounts. If you are on Windows, make sure you have OpenSSH by downloading it [here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse). Once you have OpenSSH installed, look for your course-specific account in this index [here.](https://sdacs.ucsd.edu/~icc/index.php) Now you have everything you need to connect to a server in VScode.

    To begin the connection process, open up a new terminal in VScode and type in the command "`ssh cs15lsp22[insert letters of your course-specific account]@ieng6.ucsd.edu`". If this is the first time you are connecting to this server, you will likely get a message saying "`The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established`", followed by your RSA key fingerprint and the message "`Are you sure you want to continue connecting (yes/no/[fingerprint])?`"; say yes.

    After saying yes, the server will ask for your password. Provide your password, and you should then see something like this after you finish logging in.

    ![image3](Lab_Report_1_Images\ssh_login_complete.png)

3. **Trying Some Commands:** Now that you are logged in, try running some commands in the server to see what kinds of results they produce. Some commands to try are: "`cd ~`", "`cd`", "`ls -lat`", "`ls -a`", "`cat /home/linux/ieng6/cs15lsp22/public/hello.txt`", etc. Here is a demonstration of the command "`ls -lat`", which displays all the files in a directory (public and hidden) and provides various details on them (their size, permissions, etc.)

    ![image4](Lab_Report_1_Images\ssh_trying_commands.png)

4. **Moving Files with `scp`:** "scp" is a command standing for "secure copy" that allows you to securely copy a file from your client device to a server device and vice versa. To practice this command, create a file called `WhereAmI.java` and copy it over to "ieng6" using the command "`scp WhereAmI.java cs15lsp22[account letters]@ieng6.ucsd.edu:~/`". You will be prompted for your password, and then the copy will complete. To verify that your file was copied to the server, log into the server and use the command "`ls`" to list the files in your home directory.

    ![image5](Lab_Report_1_Images\ssh_scp.png)

5. **Setting an SSH Key:** You've probably noticed that every time you connect to "ieng6" using `ssh`, you have to input your password to access the sever. This can be very tedious and time-consuming. In order to streamline the login process, you can use something called `ssh keys` in place of your password to login to the server. `ssh keys` work by using a program called `ssh-keygen` to create a pair of files, a public key and a private key, and store the public key in a location of the server and the private key in a location of the client; when you log in, the keys are used in place of your password to verify your identity.

    To generate a pair of keys, open a VScode terminal on your client device (not when you are signed in to ieng6) and type the command "`ssh-keygen`" into the terminal. The `ssh-keygen` program will create an RSA key pair and will then ask you to enter the file directory in which to save the key files. Within the save directory line (in parenthesis before the colon) a directory resembling `/Users/<user-name>/.ssh/id_rsa` should be present; copy this exact directory and save your file in this location. The program will then ask you for a passphrase; leave this field empty. Your key pair will then be completely finished generating, and the public (`id_rsa.pub`) and private (`id_rsa`) keys will be stored in the `.ssh` directory on your computer.

    The last thing you need to do is copy the public key from your client device to the server device. In order to do this, you need to log into the ieng6 server (still using your password), make a new directory called `.ssh` using the command "`mkdir .ssh`", log out of the server, copy the public key from your client device to the server device using the command "`scp /Users/<user-name>/.ssh/id_rsa.pub cs15lsp22[username letters]@ieng6.ucsd.edu:~/.ssh/authorized_keys`". Once you do this, you should be able to log into the ieng6 without a password, like this:
    
    ![image6](Lab_Report_1_Images\ssh_key_login.png)

6. **Optimizing Remote Running:** Now that you can access "ieng6" without password verification, you are capable of running chains of commands between the client and the server more fluidly than you could before. For example - using semicolons to seperate multiple commands on the same line and using double quotes to run commands in the remote server - you can transfer and run files all in a single line, like this: 

    ![image7](Lab_Report_1_Images\ssh_optimized_commands.png)


And that's it, everyone! That's how you connect to "ieng6" using your course-specific account, as well as how you transfer files to and from a remote server, and how you generate a pair of public and private keys. I hope this tutorial was helpful, and I'll see you again very soon!