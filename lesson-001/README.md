# Lesson 001 - The Unix Shell

In this lesson, we are going to cover the bare basics of using the Unix Shell (terminal)

## Why ?

- Because "the web" is one big Unix system
- Because in Unix, everything is a file
- Because the Shell provides the simplest, fastest and most unrestricted way to deal with files

## Lets begin

To begin, fire up your terminal program, and lets step through some commands, and explain 
whats going on as you type away.

The first thing that you will notice is a "command prompt", which will tell you a few basic 
things about where you are, who you are logged in as, and what special powers you are allowed.

Confusing thing is that this command prompt is entirely customizable, so different setups will be 
slightly different in each case.

eg, it might look something like this : 

`[my-name@localhost ~] $ `

In that case, it shows that you are logged in to the machine "my-hostname", using the account "my-name"
and are currently in the home directory for that user (which is referred to as ~)

Each time you type something in, and hit ENTER, the shell runs the command.  Simple.

In the following examples, we will assume that the prompt looks exactly like the one above, so you 
just need to type in the keys that follow the "$" symbol, and hit ENTER to run the command.

So lets run through a dozen commands and see what they do ...

## Commands in no particular order :

### cd  Change Directory

```
[my-name@localhost ~] $ cd
```

cd stands for "Change Directory", you can use this to change your "current directory" to
anywhere in the filesystem.

Try this :

```
[my-name@localhost ~] $ cd Documents
[my-name@localhost Documents] $
```

The command reads "Change Directory to the 'Documents' Directory"

The resulting command prompt now changes to show you where you are in that Directory.

If you get lost in the system, you can always type :
```
[my-name@localhost SomeDirectoryDeepInTheSystem] $ cd
```
To get straight back to the your "HOME" directory

### ls  LiSt

The "ls" command allows you to view a list of files in the current directory.

Try this :

```
[my-name@localhost ~] $        #-- puts you back in the HOME directory 
[my-name@localhost ~] $ cd Documents
[my-name@localhost Documents] $ ls
```

That displays a list of the files in the Documents directory.  Nice.


### Bash command completion

Typing in long filenames can be a pain, so most command shells include some tools 
to auto-complete the names of files and directories to save you some typing. These 
tools are tied to the TAB key by default 

(but be aware, that everything is configurable, so its not always the same key on every machine)

Try this again :

```
[my-name@localhost ~] $        #-- puts you back in the HOME directory 
[my-name@localhost ~] $ cd Do<Hit the TAB key>
... auto changes to :
[my-name@localhost ~] $ cd Documents
[my-name@localhost Documents] $ ls
```

The list of files looks pretty boring like that, what else can we do ?

Try these, and figure out what the extra command might mean in each case  :

```
[my-name@localhost Documents] $ ls
[my-name@localhost Documents] $ ls -l
[my-name@localhost Documents] $ ls -s
[my-name@localhost Documents] $ ls -lt
[my-name@localhost Documents] $ ls -ltr
[my-name@localhost Documents] $ ls -m
```

Each letter on the command options (command options = set of characters with a - minus in front of them)
changes the behaviour of the command.

Can you guess the difference between :
ls -lt  and ls -ltr ??

Now, try this :

```
[my-name@localhost Documents] $ ls --help
```

--help is a special option that applies to pretty much every command on a modern Linux or Mac system, which ...
you guessed it, shows all the available command line options.

Have a play - try out using the --help option every time you discover a new command, and see what the options are.

On original Unix / BSD systems, the "help" option is pre-dated by the "man pages" .. on these original systems,
documentation for each command is accessed by the "man" command (which is short for MANual), and these man 
pages are an optional install for modern Linux systems.


### "Hidden" files

Get back into the HOME directory, and try these :


```
[my-name@localhost ~] $ <Hit ENTER to get back to the HOME dir)
[my-name@localhost ~] $ ls
[my-name@localhost ~] $ ls -a
```

What happened there ?

-a means "show all", so you can see that there are significantly MORE folders/files in the home directory
than are reported by a vanilla "ls" command.

By convention, any file or folder / directory who's name begins with "." (dot), will not be displayed when 
listing files.  Programs can then use these "dotfiles" to store config data on a per-user basis, without
polluting the view of that directory.

### Folder / Directory ?  whats the difference ??

None.  Its another convention.

The real name is "directory", which goes back many many decades to the mainframe era and the first heirachical
file systems.

Apple started calling directories "folders" when the first Mac came out in the early 1980s, in an attempt
to simplify computers by referring to computer things in terms of a "desktop metaphor". In the case 
of the Mac, each directory was displayed on the "desktop" as a graphical manilla "folder" that you could click to open ... and the name has stuck ever since.

Call them directories, because that is what they are.

### ps, top, kill - Process control

### mkdir MaKe DIRectory

### pwd  Present Working Directory

### . and .. and ~

### cat  conCATenate a file

### date  Show the Date

### > Redirect

### cp  CoPy a file


### df  Disk Full

### du  Disk Usage

### echo  

### $ENV  Environment variables

### $PATH  Program search path

### ping   PING another machine

### |  Pipes

### nano - a simple text editor

### Shell Scripts

### My First Shell Script

### chmod - CHange MODe

### Bash setup and environment variables

### More Dates and Times

### Journey Into unsafe waters - the / filesystem

### A quick look at 






