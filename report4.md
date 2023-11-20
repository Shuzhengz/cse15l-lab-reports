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

## Step 7

To edit the file with `vim`

Key pressed: `<v><i><m><space><L><tab><.><tab><enter>`, this runs vim on the `ListExamples.java`
file.

![vim](images/Screenshot%20from%202023-11-19%2021-45-32.png)

Navigate to the error code in vim by typing out the number in normal mode, we already know that
it is on line 44

Key pressed: `<:><4><4><enter>`. This navigates the crusor to the start of line 44

![vim](images/Screenshot%20from%202023-11-19%2021-50-33.png)

To change the index from 1 to 2, navigate to the end of the word `index1`

Key pressed: `(hold)<shift><right>(release hold)<left>`. Holding down the shift key will navigate
by word instead of by columns

Then I entered edit mode and changed `index1` to `index2`

Key pressed:`<i><backspace><2><ctrl-c>`. `<i>` enters edit mode and `<ctrl-c>` exits into normal
mode

![vim](images/Screenshot%20from%202023-11-19%2021-56-09.png)

Then we can save and leave vim using `<:><w><q>`. `<:>` allows you to enter commands, `<w>` writes
the file to disk, and `<q>` quits vim

![command line](images/Screenshot%20from%202023-11-19%2021-58-13.png)

## Step 8

To run the tests, we run the script again

Keys pressed: `<b><a><s><h><space><t><e><tab><enter>`

![test 2](images/Screenshot%20from%202023-11-19%2022-01-56.png)

This time there is no test that failed, and the program is fixed

## Step 9

First see the changes to be added using `git status`

Key pressed:`<g><i><t><space><s><t><a><t><tab><enter>`

![git status](images/Screenshot%20from%202023-11-19%2022-05-26.png)

We can then add and commit the changes using

```
git commit -a -m "fix merge bug"
```

Key pressed: `<g><i><t><space><c><o><m><tab><-><a><space><-><m><space>`, this uses the `commit` 
command for `git` with flags `a` that adds all changes, and `m` that adds a message

Then we add the message with `<"><f><i><x><space><m><e><r><g><e><space><b><u><g><"><enter>`, which
also executes the command

![commit](images/Screenshot%20from%202023-11-19%2022-10-12.png)

Then push the changes to the fork by running

```
git push origin main
```

Where `origin` is the remote (default remote is origin) and `main` is the branch

Key pressed: `<g><i><t><space><p><u><s><tab><o><tab><m><tab><enter>`

![git push](images/Screenshot%20from%202023-11-19%2022-12-56.png)
