# Lab Report 1

## cd

### No Argument:
`[zsz@fedora ~]$ cd`

Working directory: home (`~` or `/home/zsz/`)

There is no argument passed in, so the command will cd into nothing

Not an error, it did what it's told to do, which is nothing

### Path to directory:

```
[zsz@fedora ~]$ cd Documents/
[zsz@fedora Documents]$
```
Working directory: home (`~` or `/home/zsz/`)

The command is to go into the `Documents` directory, and it did go into that
directory, as seen on the second line of the terminal output

There is no error

### Path to file:

```
[zsz@fedora Documents]$ cd temp.md
bash: cd: temp.md: Not a directory
```

Working directory: `~/Documents/`

The command tries to cd into the temp.md document, but since cd means "change 
directory", and temp.md is not a directory, the command errors out and returns 
the error message on the second line


