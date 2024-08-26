# SSH Frequently Asked Questions

This is a helper file that tries to go over the widely encountered problems when cloning, forking, or setting up an
ssh key for the first time.

## 1) Git works, but I get a message that I don't have permission ((Windows)
 قيت يعمل لكن يظهر لي رسالة انه ليس لدي صلاحية لنسخ المشروع

### What is the problem?
I generated an ssh key. Also, I added my public key to GitHub. However, I still cannot clone my repository. 

### Steps taken:

1. Opened the command prompt (cmd).
2. I copied the git clone command for my repository from GitHub.
3. I pasted the command in cmd and hit Enter.

### The result I get:
```sh
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

### The Solution:
Your private key is not added to you ssh agent. There could be many ways on how this could go wrong. However, the steps below are a general solution that should work if followed carefully.

1. Make sure the key identified is within the default path ("C:\Users\<username>\.ssh") and if possible the default name (id_rsa).
2. Make sure the ssh agent is working and the private key you have is added to the agent. This post (https://stackoverflow.com/a/40720527/3504748) has a very detailed steps on how to fix the not working agent and add your private ssh key. I recommend following the steps from the "Update 2019" explanation.
3. Once you finished all the steps in the post given in step #2, I recommend restarting your PC before trying to clone again.

## 2) I downloaded git and installed it, but it doesn't work (windows)
 اذا كنت محمل قيت لكن قيت لا يعمل

### What is the problem?
I downloaded git (from https://git-scm.com/download/win) and installed it. However, I cannot run `git` from the command line.

### Steps Taken:
1. Opened the command prompt (cmd).
2. I typed `git` then hit Enter.
### The result I get:
```sh
'git' is not recognized as an internal or external command,
operable program or batch file.
```

### The Solution:
You have to add git to your PATH environment variable.

See the detailed steps in this answer to know how (https://stackoverflow.com/a/4493004/3504748).

## 3) How do I know which private key I'm using and how can I stop it (Windows and Mac)? 
كيف اعرف اي برايفت كي انا استخدم وكيف اوقف استخدامه

### To check what private key is curenlty used
```sh
ssh-add -L
```


### To clear the used ssh keys (THIS IS NOT DELETING THE KEY):
```sh
ssh-add -D
```

## 4) How to clone my project directly from PyCharm rather than using CMD or Terminal? 
كيف اسوي كلون لمشروعي من PyCharm مباشرة بدال ما استخدم CMD او Terminal

Assuming everything works in you machine as expected (e.g., ssh works). 
To be able to copy/clone you project using PyCharm is easy.

1. Open PyCharm.
2. From the application screen, click on "Get from VCS".
3. For the "Version Control" choose "Git".
4. Add you repository link to the URL field. E.g., "git@github.com:quit315/project-0-hello.git".
5. Choose where you want the project to be saved.
6. Click in "Clone"
