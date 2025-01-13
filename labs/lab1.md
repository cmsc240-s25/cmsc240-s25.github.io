---
layout: default
permalink: lab/1
---

# Lab 1: Unix/Linux Preliminaries

* Work through the exercises below and add your answers to the `README.md` file in GitHub repository for this lab.
* Use the GitHub classroom link below to create your repository.
* Github Classroom Link: [https://classroom.github.com/a/RVNRm5b-](https://classroom.github.com/a/RVNRm5b-)


### Objectives

The goal of this lab is to gain exposure to the Unix/Linux environment and the commands available on the terminal command line interface (CLI). 


### Table of Contents

* [Unix/Linux](#unix)
    * [Exercise 1](#exercise_1)
    * [Exercise 2](#exercise_2)
    * [Exercise 3](#exercise_3)
    * [Exercise 4](#exercise_4)
* [Manual pages](#manual)
    * [Exercise 5](#exercise_5)
    * [Exercise 6](#exercise_6)
    * [Exercise 7](#exercise_7)
    * [Exercise 8](#exercise_8)


---

# Unix/Linux <a class="anchor" id="unix"></a>

On our course web page [schedule](https://cmsc240-s24.github.io/schedule.html), follow the link to the Unix tutorials reading (tutorial URL is https://users.cs.duke.edu/~alvy/courses/unixtut/). This tutorial can be used to help you while working on this lab. Please complete the exercises below by following the directions and answering directly in this README.md file. You must save your work, commit, and push the changes to your GitHub classroom repository. For all the following exercises, you should use cs01 - cs06.richmond.edu.  You can access the terminals by typing `ssh usernam@cs01.richmond.edu`, where `username` is your UR netid. Or use the terminal in a remotely connected VSCode window.

 
## Exercise 1: <a class="anchor" id="exercise_1"></a>

- Run the following to see who is logged on the system with you
```Shell
who
``` 
- Next, redirect the output of the `who` command to a file
```Shell
who > users.txt
```
- Let's see what is in the file by con`cat`enating the file to the terminal window.
```Shell
cat users.txt
```
- Now let's sort the file by redirecting the file to the `sort` command. Notice the direction of the redirect has changed from above from redirecting the output to redirecting an input.
```Shell
sort < users.txt
```
- We could instead sort users directly from the `who` command output.  This is accomplished by piping the output from the `who` command into the input of the `sort` command.
```Shell
who | sort
```
<br />

- **What is the difference between using `>` and `|` after a command?** 


___

<br />
<br />


## Exercise 2: <a class="anchor" id="exercise_2"></a>
- Change directory into the system binaries folder `/bin` by running the following command.
```Shell
cd /bin
```
- Now list all of the files in this folder.
```Shell
ls
```
- Next, list only the files that start with z like this.
```Shell
ls z*
```
- Finally, list all the files that start with z and end with p.
```Shell
ls z*p
```

<br />

- **What is the purpose of `*` in specifying items at the command prompt?**

___

<br />
<br />


## Exercise 3: <a class="anchor" id="exercise_3"></a>
- Change directory into your home directory.
```Shell
cd ~
```
- Let's create a new text file.
```Shell
touch secret.txt
```
- Next, list the access control parameters for the new file. 
```Shell
ls -l secret.txt
```
- Take note of the ten characters on the left `-rw-r-----`.  The first character denotes whether this is a file or directory. If it was a directory it would be a `d`, files are `-`. The next 9 characters tell us the access control permissions.  The first 3 characters are the user permissions, the next 3 characters are the group permissions, and the last three characters are the permissions for everyone else.

- Now we will use the change modes command to change the access control list for the file. We will set the user (the owner of the file) to have full read/write/execute permissions, the group to have no permissions, and all others to have no permissions.
```Shell
chmod u=rwx,g=,o= secret.txt
```
- Again list the access control parameters for the file and note the difference.
```Shell
ls -l secret.txt
```
- Now give the group read/write permissions
```Shell
chmod g=rw secret.txt
```
- Again list the access control parameters for the file and note the difference.
```Shell
ls -l secret.txt
```
- Now give everyone else (other) read permissions.
```Shell
chmod o=r secret.txt
```
- Again list the access control parameters for the file and note the difference.
```Shell
ls -l secret.txt
```
- Read this [tutorial](https://users.cs.duke.edu/~alvy/courses/unixtut/unix5.html) for assistance. Or consult the manual page for `chmod` by typing `man chmod`.
<br />

- **What command would you need to run on a file called `secret.txt` in order to make it so no one other than the owner could read or write it?**



___

<br />
<br />


## Exercise 4: <a class="anchor" id="exercise_4"></a>
- The sleep command will run for the number of seconds specified. Try it.
```Shell
sleep 10
```
- Wait for the previous command to complete.  Then run the same command but this time as a background process using the `&`.
```Shell
sleep 10 &
```
- While sleep is running in the background run the `jobs` command to see if it is still running. 
```Shell
jobs
```
- While sleep is running in the background run the `ps` command to get a list of your current running processes. 
```Shell
ps
```

<br />

- **What does `&` do when you place it at the end of a command?**


___


# Manual Pages <a class="anchor" id="man"></a>

The `man` pages are online documentation that explains how to execute and use the various programs installed on Unix systems. They usually start with an overview and then give information about the many flags each program can be invoked with. In the exercises below, explain what the following commands do in general and then explain what happens when the specified flag is added.

## Exercise 5: <a class="anchor" id="exercise_5"></a>

```Shell
man grep
```

- **What does `grep -n` do in general and with the specified flag?**


___

<br />
<br />

## Exercise 6: <a class="anchor" id="exercise_6"></a>

```Shell
man head
```

- **What does `head -n 10` do in general and with the specified flag?**


___

<br />
<br />

## Exercise 7: <a class="anchor" id="exercise_7"></a>

```Shell
man diff
```

- **What does `diff -w` do in general and with the specified flag?**


___

<br />
<br />

## Exercise 8: <a class="anchor" id="exercise_8"></a>

```Shell
man gzip
```

- **What does `gzip -v` do in general and with the specified flag?**


___

<br />
<br />