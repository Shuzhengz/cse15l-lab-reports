# Lab Report 1

## cd

### No Argument
`[zsz@fedora ~]$ cd`

Working directory: home (`~` or `/home/zsz/`)

There is no argument passed in, so the command will cd into nothing. However, if
the working directory is not home, then it will change the working directory to
home.

Not an error, it did what it's told to do, which is nothing

### Path to directory

```
[zsz@fedora ~]$ cd Documents/
[zsz@fedora Documents]$
```
Working directory: home (`~` or `/home/zsz/`)

The command `cd` is to go into the `Documents` directory, and it did go into that
directory, as seen on the second line of the terminal output

There is no error

### Path to file

```
[zsz@fedora Documents]$ cd temp.md
bash: cd: temp.md: Not a directory
```

Working directory: `~/Documents/`

The command tries to `cd` into the temp.md document, but since `cd` means 
"change directory", and temp.md is not a directory, the command errors out and returns 
the error message on the second line


## ls

### No Argument

```
[zsz@fedora /]$ ls
afs  boot  etc   lib    lost+found  mnt  proc  run   srv  tmp  var
bin  dev   home  lib64  media       opt  root  sbin  sys  usr
```

Working directory: root (`/`)

The command lists all files and directories in the current working directory, 
there is no error

### Path to directory

```
[zsz@fedora /]$ ls home
zsz
```

Working directory: root (`/`)

The command lists all files and directories in the directory passed in the
argument, which is home, and it lists my user directory, which is the only
thing in this directory, so it did not error out

### Path to file

```
[zsz@fedora Documents]$ ls temp.md 
temp.md
```

Working directory: `~/Documents/`

The command lists the file passed in as the argument, `temp.md`, which it does, 
and is not an error.


## cat

### No Argument:

```
[zsz@fedora ~]$ cat

```

Working directory: home (`~`)

Since there is no argument passed in, it does not know what file to run on, so 
it just returns a blank line and is stuck there. If anything is passed into that
blank line, it just returns it in a new line, but still does not terminate the
program unless the user terminates it with `Ctrl` + `C` keyboard shortcut. This
is probably not an error since the program does not terminate automatically

### Path to Directory

```
[zsz@fedora ~]$ cat Documents/
cat: Documents/: Is a directory
```
Working directory: home (`~`)

Since `cat` is intended to be used on files, it errors out and tells you that
you cannot use `cat` on a directory before self-terminating

### Path to File

```
[zsz@fedora Documents]$ cat temp.md 
temp file
```

Working directory: `~/Documents/`

Running `cat` on the file returns the string contained in the file, which is
just _temp file_, as intended
