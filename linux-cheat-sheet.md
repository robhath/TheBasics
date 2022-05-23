# Linux Commands Cheat Sheet

The Linux command line is a text-based operating system. 
+ To run an operating system command, or an application, type its name  (often an abbreviation) at
  the prompt, followed by parameters (as needed), then hit ENTER. 
+ Parameters are separated from commands, and from one another, by SPACE characters. 
+ Some parameters represent options that change the way the command works. These parameters usually
  begin with one or two dashes, followed by one or more letters, or maybe an entire word (e.g. `ls -la').
+ Some parameters represent files or directories--a "path"--which is a hierarchical sequence of 
  directory names, separated by `/`, ending with a file name. A path can also contain wildcard 
  characters to indicate all files or directories that match a pattern. E.g. `foo.txt`, `/home/fred/documents`, 
  `/home/fred/documents/linux-cheat-sheet.md`, `src/docs/*.xml`. 


## Directories:
```bash
    pwd                  # print the current working directory

    cd <path>            # change to a directory
    cd ~                 #   go to your home directory, e.g. /home/fred
    cd ..                #   go to the directory one level up

    mkdir <path>         # make a directory (create it)

    rmdir <path>         # remove a directory (delete it; it must be empty)
```


## Files:
```bash
    ls                   # list the files in the current directory
    ls -al               #   list all files using long format
    ls -tl               #   list files in time order using long format
    ls <path>            #   list the file or the files in the specified path

    rm <path>            # remove the file (delete it)
    rm -r <path>         #   recursively remove files (i.e. include sub-directories)
    rm -fr <path>        #   recursively remove by force (don't ask for permission!) DANGER!

    cp <from> <to>       # copy a file
    cp -r <path> <path>  #   copy recursively (i.e. all files in the directory and its sub-directories)

    mv <from> <to>       # move a file (i.e. rename, or cut/paste)
```
Notes: 
+ files that have names beginning with `.` are hidden by default (but the `-a` parameter shows them)
+ long display format includes: 
  ```
  permissions  links  owner-name  owner-group  file-size  time-last-modified  file/directory-name
  -rwxr-xr-x   1      fred        amazon       1063       May  2 19:18        build-info.xml
  ```
+ wildcards are allowed in paths:
  ```
  ?        # matches a single character
  *        # matches zero or more characters 
  ```
+ you can escape spaces, or other problem characters, with a backslash `\`, e.g. `ls my\ document.txt`


## View file contents:
```bash
    cat <file>           # concatenate the file to stdout (i.e. display the file's contents on your screen)

    more <file>          # display the file's contents one page at a time

    less <file>          # less is more but with extra capabilities
```


## Change file permissions and owners:
```bash
    chmod <mode> <path>  # change mode, i.e. grant or remove file permissions where:
                         #   <mode> is [ugoa][-+=][rwx]    i.e. for...
                         #      (u) user, (g) group, (o) others, (a) all
                         #      (-) remove, (+) add, (=) add and remove unmentioned
                         #      (r) read, (w) write, (x) execute/search permissions

    chmod a+x foo.sh     # allow all (everyone) to execute the 'foo.sh' script
    chmod g=r bar.txt    # allow group members to read but not write or 

    chown <user> <file>  # change the owner of the file to the specified user
```


## Get more information:
```bash
    man <command>        # show the manual page for the command

    which <command>      # where is that command located (if anywhere)?

    ps                   # show running processes

    history              # show the commands you have entered so far

    whoami               # what's my username? (use for occasional amnesia)

    printenv             # print (display) all environment variables

    echo <something>     # just print that 'something' right back at ya, but...
    echo $SHELL          #   echo will substitute the value of an environment variable
```

## Keystrokes:
+ CTRL-A   : moves the cursor to the beginning of the command line
+ CTRL-C   : stops a running command
+ CTRL-E   : moves the cursor to the end of the command line
+ TAB      : auto-completes a path
+ CTRL-L   : clears the screen
+ CTRL-Q   : resumes ouput to the screen
+ CTRL-S   : stops output to the screen
+ UP-ARROW : go to previous command in your history


## Streams- *stdin* (`<`), *stdout* (`>`), *stderr* (`2>`)
  A stream allows you to transfer data (text) to/from files/commands. For example:
  ```bash
      ls -la > dir.txt   # redirect output of the ls command (stdout) to the file 'dir.txt'
                         #   the file will be created or overwritten if it already exists
      
      ls -la >> dir.txt  # same, except the file will be appended to if it already exists

      ls nada 2> err.txt # redirect error output of the ls command (stderr) to the file
                         #   'error.txt' (assumes the file 'nada' doesn't exist)

      myscript < foo.txt # redirect the contents of 'foo.txt' as if were keyboard input
                         #   (stdin) to myscript (assumes myscript accepts keyboard input)
  ```

## Additional commands:
```bash
    diff <file1> <file2> # compare the contents of the files line by line and show any differences

    grep <regex> <path>  # looks for instances of text that matches the regular expression (<regex>) 
                         #   in the file(s) indicated by the path
    grep foobar *        # looks for the term 'foobar' in all files in the current directory
    ls -la | grep foobar # pipe ('|') the output of the ls command to grep and print any entries
                         #   that contain the term 'foobar'

    ssh <destination>    # log in to a remote host (destination)

    sudo <cmd> <params>  # superuser do ... (i.e. escalate my permissions to admin to do something)
                         #   you will be prompted for your (admin) password

    tar -xzvf <tarfile>        # extract and decompress files from the tarfile to the current directory
    tar -czvf <tarfile> <path> # create the tarfile from the compressed files in the path

    unzip <zipfile>      # decompress the files in the zipfile and put them in the current directory
    unzip f.zip -d foo   # decompress the files in 'f.zip' and put them in the directory 'foo'

    zip <zipfile> <path> # compress file(s) given by the path and place them in the zipfile
```

