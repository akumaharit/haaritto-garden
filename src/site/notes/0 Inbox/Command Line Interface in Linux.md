---
{"dg-publish":true,"permalink":"/0-inbox/command-line-interface-in-linux/","created":"2024-01-04T22:11:04.398+07:00","updated":"2025-09-14T20:30:35.883+07:00"}
---


## Summary Table for common terminology

| Type    | Term      | Key Role                                                                                                                                                                                | Example        | Runs On              |
| ------- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | -------------------- |
| OS      | **Linux** | Unix-like, open source                                                                                                                                                                  | Ubuntu, Debian | PC, servers          |
| OS      | **Unix**  | Original OS design<br>Unix inspired Linux                                                                                                                                               | AIX, Solaris   | Servers, mainframes  |
| Program | **Shell** | Interprets commands                                                                                                                                                                     | Bash, Zsh      | Linux/Unix/WSL/macOS |
| Tool    | **WSL**   | Runs Linux on Windows<br>The shell here RUN INSIDE LINUXX!!!!                                                                                                                           | Ubuntu on WSL  | Windows              |
|         | MINGW64   | MINGW64 is not the shell — <br>it’s the Windows-native environment <br>that bash runs in, bringing along Linux-like commands.<br><br>The shell here, RUN INSIDE WINDOW (Not real Linux) | MINGW64        | Windows              |

## Shell
- is a program where user can type in the command, make it read the command and run the command (or other programs)
- Shell's advantage is all about having high action-to-keystroke ratio. It can automate repetitive task.
- most popular UNIX shell is **Bash** -> and it is default shell on most modern implementation of UNIX
- Git Bash is a software that enable user to use a Bash like interface when interacting with Git
- What you see in terminal such as `harit@HaritASUS` is your username and hostname.
## Commands

![Basic Shell Syntax.png](/img/user/3%20Resources/Attachment/Basic%20Shell%20Syntax.png)
option = flags or switches (especially if the option take no argument)
argument can sometimes be called parameter
there is also `--` which is long option
for the option, capitalization is very important!

## Opening VSCode in Linux
In WSL2, use `vscode` to launch VSCode in WSL2 
Please use `vscode ~` to launch code in home directory.
Use `wget` to download file to that directory, use `unzip` to unzip the zip (You have to `sudo apt install unzip` first before unzipping the zip file.)

## Basic Commands

> [!Tip] Home is not the same as the root directory.

![Linux File System Illustration.png](/img/user/3%20Resources/Attachment/Linux%20File%20System%20Illustration.png)

- Use `cd ..` to browser to the **parent** directory (GO BACK).
	- `. `mean current directory
	- `/` **when in front of a file or directory name it mean root directory,** but in other cases such as when it is *inside* a path, it is just a separator.
- Use `cd -` to go back to the directory you are in previously
- `cd` without argument will return you to the **home** directory
- `~` mean home directory so `cd ~` will travel you to home directory (same as `cd` with no argument)
	- ex. ls ~ will list files and directories in the home directory
- Absolute Directory -> specify a location starting from **ROOT** location, the Root Directory is the topmost directory when illustrated the filesystem as a tree.
	- File system refer to the part of OS the manage files and directories
- Relative Directory -> specify a location starting from current location
- `ls -F` will append indicator * / = > @
- `ls -a`
	- will show all hidden file including entries start with .
- `ls -R`
	- will list all subdirectories
- `clear`
- `pwd` to print working directory (to find out where we are)
- `man ls`
	- will open manual for ls
	- B + Spacebar -> skip up and down by a full page
	- / following a pattern you want to search
	- if multiple hits were found -> N and shift+N to browse the hits
	- q to quit the man pages



## Files

- use `mkdir` to create directory
	- `-p` to create nested subdirectories in single operation `ex: mkdir -p folder1 folder2`
	- this will force `mkdir` to create necessary intermediate directories to archive the commands
- use `touch` to create file (blank file)
- `rm` to remove file
	- use `-i` to enable interactive mode
	- use `-r` to remove directory
- use `mv` to move or rename file
	- ps. use `-i` to enable interactive mode -> making it ask for the confirmation before replacing already existed file/destination, **because by default it won't ask!**
	- you can use it to move multiple files via `mv file1.txt file2.txt target_directory/` same goes for the `cp`, when specifying multiple files, the shell expect directory as the final argument.
- `cp` to copy directory
	- use -r (recursive option) to copy a directory and all of its contents
- `*` and `?` is a wildcard.
- `nano file.txt` to create a text file.
 
## Pipes and Filter
- use `wc` to word count
- `>` allow you to redirect the command's output instead of printing to the screen ex. `wc -l *.pdb > lengths.txt`
	- `>>` also redirect but append instead of overwriting the file
- `cat`
- `less`
	- space (forward) b (backward) q (quit)
- `head`
	- to print just a head (few) line of the text
	- use `-n` to specify number of line to print
- `tail`
- `|` is called, pipe operator, It tells the shell that we want to use the output of the command on the left as the input to the command on the right.
- `cut` to spilt text into columns
	- -d specify delimiter ( default = tab )
	- -f specify column we wanted to extract
- `cut -d, -f 2 animals.csv | sort | uniq -c` can be used to spilt line into column, sort and count unique
	- sort is required here, or it won't count unique properly
![Redirects and Pipes of different commands: "wc -l *.pdb" will direct theoutput to the shell. "wc -l *.pdb > lengths" will direct output to the file"lengths". "wc -l *.pdb | sort -n | head -n 1" will build a pipeline where theoutput of the "wc" command is the input to the "sort" command, the output ofthe "sort" command is the input to the "head" command and the output of the"head" command is directed to the shell|600](https://swcarpentry.github.io/shell-novice/fig/redirects-and-pipes.svg)