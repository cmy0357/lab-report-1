# How to log into ieng6

> ***Step 1: Installing VSCode***
* Go to [VSCode Website](https://code.visualstudio.com), and install the corresponding version of it on your computer. Once installed, your should be able to see the following window:
![lab1 p2](https://user-images.githubusercontent.com/103284526/162543209-1327f18c-3aaa-4a4f-8c5b-afba968e666e.jpg)

***

> ***Step 2: Remotely connecting***
* If you are on Windows, first follow this [link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) to install OpenSSH.
* Then, find your CSE 15L account using this [link](https://sdacs.ucsd.edu/~icc/index.php).
* Next, open a terminal in VSCode and type the following command: (replace `zz` with your account name)  
    `$ ssh cs15lsp22zz@ieng6.ucsd.edu`
* Press enter, and then type `yes`and press enter again.
* After that, type in your password, and you will see something look like this in your terminal:
![lab1 p3](https://user-images.githubusercontent.com/103284526/162588310-1fb0e4cb-f7af-4578-a7b1-1aa315f17558.jpg)

---

> ***Step 3: Try some commands***
* After you log in to the remote server, you can try running some commands and see how they work. Here's a list of useful commmands you might want to try:
  - `cd`
  - `ls`
  - `pwd`
  - `mkdir`
  - `cp`
  - `cat`
* Here's an example of output you would get when running the commands:
![lab1 p4](https://user-images.githubusercontent.com/103284526/162588854-5c148fdb-394b-4b39-a7dd-d86b96e087bf.jpg)

---

> ***Step 4: Moving files with `scp`***
* First, create a file called `WhereAmI.java` and copy the following into the file:

`class WhereAmI {`  
  `public static void main(String[] args) {`  
    `System.out.println(System.getProperty("os.name"));`  
    `System.out.println(System.getProperty("user.name"));`  
    `System.out.println(System.getProperty("user.home"));`  
    `System.out.println(System.getProperty("user.dir"));`  
  `}`  
`}`  
* Then, open a new terminal and run the following command:  
`scp WhereAmI.java cs15lsp22zz@ieng6.ucsd.edu:~/`
* Enter the password, and then log into the remote server again as we did in step 2.
* Enter `ls`, and you will be able to run it with `javac` and `java`. Here's an example of output:
![lab1 p5](https://user-images.githubusercontent.com/103284526/162589674-1a86c0e2-f553-4bdf-abf6-915f1bfedd0a.jpg)

---

> ***Step 5: Setting an SSH key***
* On your computer, run the command `$ ssh-keygen`, and you will see the following output:
![lr1a](https://user-images.githubusercontent.com/103284526/162590148-99bd0648-4dc1-4553-9b48-a7602a72dcc2.jpg)
* Press enter once, and it will ask you for passphrase. We will skip the passphrase for this step, so you just need to press enter two more times, and you will see the following output:
![lr1b](https://user-images.githubusercontent.com/103284526/162590259-2cdadb98-00ca-4d0d-9224-5549976602cd.jpg)
* If you are on Windows, here's an additional step you need to follow, use this [link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation).
* Next, log into remote server using the command `$ ssh cs15lsp22zz@ieng6.ucsd.edu` and enter your password.
* Run the command `mkdir .ssh`, and then logout by entering `exit`.
* Once you logout, run the command `$ scp /Users/<user-name>/.ssh/id_rsa.pub cs15lsp22zz@ieng6.ucsd.edu:~/.ssh/authorized_keys`. (Don't forget to change the `<user-name>` and `zz` with your own username)
* After completing these steps, you will be able to run `ssh` or `scp` on your computer without entering the password. Here's an example of successfully logging in without password:
![lab1 p6](https://user-images.githubusercontent.com/103284526/162590640-14ede2f5-5ca9-40d7-88d6-f2307ee6c855.jpg)

---

> ***Step 6: Optimizing Remote Running***
* Edit `WhereAmI.java` on your computer and save it.
* Copy the file to the remote server by running the command:  
  `scp WhereAmI.java cs15lsp22zz@ieng6.ucsd.edu:~/`
* Log into the remote server using `ssh`.
* Run the file using the command:  
  `ls; javac WhereAmI.java; java WhereAmI`
* Once you complete these steps, you will see the edit you made from your computer showing up on the remote server. Here's an example for that:
![lab1 p7](https://user-images.githubusercontent.com/103284526/162590941-3d806ca6-4086-4d1c-9065-2512b23a9816.jpg)
