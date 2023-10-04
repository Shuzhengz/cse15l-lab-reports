# Lab Report 1

## cd

### No Argument
`[zsz@fedora ~]$ cd`

Working directory: home (`~` or `/home/zsz/`)

There is no argument passed in, so the command will cd into nothing

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
