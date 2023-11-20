# Lab Report 4

## Step 4 and 5

### SSH into `ieng6`

Using the command to log into `ieng6`

```
ssh cs15lfa23qe@ieng6.ucsd.edu
```

Key pressed: `<s><s><h><space><ctrl-shift-v><enter>`, this pastes the command into the terminal
and runs it, and it logs in without password since I have the key set up

```
Hello cs15lfa23qe, you are currently logged into ieng6-202.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   21:05:01   23  22.26,  22.41,  22.27
ieng6-202   21:05:01   21  1.56,   1.21,   1.14
ieng6-203   21:05:01   22  4.11,   4.19,   4.24

 
Sat Nov 18, 2023  9:07pm - Prepping cs15lfa23
```

### Cloning Lab 7 repository with ssh key:

```
git clone git@github.com:Shuzhengz/lab7.git
```

Key pressed: `<g><i><t><space><c><l><o><n><e><space><ctrl-shift-v><enter>`, this pastes the
command into the terminal and runs it, which clones the repository with the ssh key that is
already set up on my `ieng6` insteance.

![cloning with ssh](images/Screenshot%20from%202023-11-19%2021-29-23.png)

## Step 6

`cd` into the directory with command `cd lab7/`

Keys pressed: `<c><d><space><l><a><tab><enter>`, this enters the directory

Run the tests with the script by running the `.sh` file:

```
bash test.sh
```

Keys pressed: `<b><a><s><h><space><t><e><tab><enter>`

![run test](images/Screenshot%20from%202023-11-19%2021-33-45.png)

This runs the tests for the program. We can see that there is 1 failure in the 2 tests that were 
run, and the location for the exception.
