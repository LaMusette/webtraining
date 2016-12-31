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

So lets run through a dozen commands and see what they do ... you don't need to memorize any of this, 
just follow the examples, and you will get a good feel for how it all hangs together. Each command name
is deliberately mnemonic, so each time you use it, it will stick in your head, like riding a bicycle.

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

### ps, top, kill, who - Process control

Your Unix based system is what is traditionall called a "multi-user / multi-tasking" system, in that lots of different users can login at the same time, and run lots of different programs.

Try some of these commands, and look carefully at the output :

```
[my-name@localhost ~] $ <Hit ENTER to get back to the HOME dir)
[my-name@localhost ~] $ ps
[my-name@localhost ~] $ who
[my-name@localhost ~] $ who am i
[my-name@localhost ~] $ uname -a
```

There are a tonne of different ways of seeing what is running on the computer.

ps (Process Status), on its own does'nt tell you much, so try some of these common options, and
notice the difference :


Finally, there is the "top" command, which runs interactively to show what the machine is up to :
```
[my-name@localhost ~] $ top
```

Hit Q to get out.

Hit 1  to show a breakdown by CPU
Hit F  to change the sort-by field
Hit ?  to show all the options

There is also a "kill" command to tell a process to die. You can only KILL processes that you own, to prevent
normal users from doing anything too dangerous. 

We will look at this in more detail later, as process control becomes really important when dealing with 
web-server processes, proxy controllers, mail servers, and everything else related to controlling a web site.

But first, need to get to the point where you understand that "everything is a file" .. which includes of course
files themselves, but also directories, as well as processes, and network connections ... they are all files, and 
can be treated as files just like anything eles.

### mkdir, pwd

Back to the file system for now .. Try this, and watch carefully what happens with each command :

```
[my-name@localhost ~] $ <Hit ENTER to get back to the HOME dir)
[my-name@localhost ~] $ cd Documents
[my-name@localhost Documents] $ mkdir NewDir
.. this command Makes a new directory called NewDir

[my-name@localhost Documents] $ ls -ltr
... note that there is a new directory called NewDir, which is the most recent file in the current directory

[my-name@localhost Documents] $ cd NewDir
... changes directory to NewDir

[my-name@localhost NewDir] $ pwd 
... short for Present Working Directory

[my-name@localhost NewDir] $ ls
... its empty !!!
```

So, we just make a NEW directory inside the Documents directory, and then changed directory into the new 
one we just created.

At this stage, pull up your graphical FileManager program, and see visually what we just did. Navigate into 
the Documents folder, and then into the NewDir folder.

Whilst that is still up, Try this back in the terminal :

```
[my-name@localhost NewDir] $ mkdir AnotherOne
... note that a new folder appears in the graphical FileManager

[my-name@localhost NewDir] $ date > NewFile.txt
... note that a new file has just appeared in the graphickal FileManager
```

Click on the "NewFile.txt" that appears in the graphical FileManager .. what do you see in there ?

Can you guess how that happened, and think about what the > symbol might mean in the command above ?

... we will cover that weird symbol in a sec. At the moment, we have just created a deeper set of 
directory heirachies, which we need in order to play with the next concept.

### . and .. and ~ and /   Relative and Absolute path names

Path names = different ways of navigating around the directory heirachies.

Paths can be expressed as "Relative" paths, or as "Absolute" paths. What you are about to cover here 
is pretty straightforward, but it also applies exactly the same when dealing with navigation inside a 
web application. 

Web applications also use the exact same concept of Relative vs Absolute paths, but its much easier to 
grasp in terms of the Unix file system, so lets play in here, and see what happens.

Try this :

```
[my-name@localhost NewDir] $ cd   #-- get back to the home directory 
[my-name@localhost ~] $ pwd
[my-name@localhost ~] $ cd Documents
[my-name@localhost Documents] $ pwd
[my-name@localhost Documents] $ cd NewDir
[my-name@localhost NewDir] $ pwd
[my-name@localhost NewDir] $ cd
[my-name@localhost ~] $ 
```

In the above example, we changed directory one step at a time, to get to the /home/yourname/Documents/NewDir directory. In each case, the name of the directory that we entered ... just the name .. we call the "Relative Path".

At each stage, after running the "pwd" (Present Working Directory) command, you can see the full path name of the
directory that we are in. This full path name is called the "Absolute Path".

... so lets try again with some extra tricks. Don't forget to use the TAB key to auto-complete, as that can help.

```
[my-name@localhost ~] $ pwd
[my-name@localhost ~] $ cd Documents/NewDir
[my-name@localhost NewDir] $ pwd
[my-name@localhost NewDir] $ cd
[my-name@localhost ~] $ 
```

hmmm ... we can jump straight to the NewDir with a single command. Note though that "Documents/NewDir" is still 
a "Relative Path", since it is relative to the HOME directory.

Lets try now with some "Absolute Paths"

```
[my-name@localhost ~] $ pwd
[my-name@localhost ~] $ cd /
[my-name@localhost /] $ pwd
... /  this is the ROOT system directory, which is like the Root branch of the tree that is your entire filesystem

[my-name@localhost NewDir] $ cd ~/Documents/NewPath
... this is an absolute path, since the shell expands the "~" symbol to mean your HOME directory

[my-name@localhost NewDir] $ pwd
... all good, that is what we expect

[my-name@localhost NewDir] $ cd ~/Documents
[my-name@localhost Documents] $ pwd
... absolute path to your Documents directory

[my-name@localhost Documents] $ cd ~
[my-name@localhost ~] $ pwd
[my-name@localhost ~] $ cd ~/Documents/NewDir
[my-name@localhost NewDir $ pwd
[my-name@localhost NewDir $ cd ..
[my-name@localhost Documents $ 
```

OK, starting to make sense.  Relative Paths mean "go from the current directory", whereas Absolute Paths mean 
"go to this path, regardless of where we currently are".

Now, whats up with that last one ?  What does "cd .." mean ? Is it a Relative Path, or an Absolute Path ?

Try it a few times, and see what happens. Just keep going "cd .." and see where you end up.

When you get stuck, "cd <ENTER>" to get back to the home directory.

### cat - Show contents of a file

It gets boring just moving around looking at lists of files.

Lets have a look at the contents of a file, how do we do that ?

Try this :

```
[my-name@localhost ~] $ pwd
[my-name@localhost ~] $ cd Documents/NewDir
[my-name@localhost NewDir] $ ls -l
[my-name@localhost NewDir] $ cat NewFile.txt
```

Interesting ... The "cat" command shows whats in that file that we created with the date command, it should
match up with what you already saw in the graphical file manager.

"cat" is short for "conCATenate", which makes no sense at all at this stage. Please persist, as the name will
become clear in a sec. Its actually important, so hang in there.

Lets try that again :

```
[my-name@localhost NewDir] $ date
[my-name@localhost NewDir] $ date > NewFile.txt
[my-name@localhost NewDir] $ cat NewFile.txt
```

Oh Noes !! We overwrote the "NewFile.txt" file with a fresh new copy of the date, and we have lost 
all of the data in the old file. Be super careful when using the > symbol.

The "date" command (obviously), displays the current date and time. Putting the > symbol after 
the command literally means "redirect the output" into the file called NewFile.txt.

Pretty simple ... or not ?  Lets ponder on that for a moment, and think about what it means.

So, we know that there is a command called "date" that prints the current date. Somebody wrote a program,
told it to print the date to the screen, and called it "date".
How does it then know when to NOT print to the screen, but instead open up a file and put the
date in there ?

Did the person who wrote the "date" program have to consider this and include it as an option,
or is there something else going on here, and whats it got to do with cats ?.

"Everything is a file" after all, right, so what are we missing ?

Here is what is really going on  (read this bit twice):

```
When you type in "date" on the command prompt, the Shell looks for a file called "date", loads it up as a new
process (which will appear in the process list with the ps command), and then execute the program. The "date"
program looks up some other files, formats the date, and just outputs it, and then closes.

Where this "output" goes, it doesnt care ... it just "outputs" it to what is called "STDOUT", which is short for "Standard Output". 

STDOUT is also file ... but a file that lives in memory only, it is never stored on disk. 
Each running PROCESS on the system has its own separate concept of STDOUT.

What the shell is doing when it runs the "date" command, is reading its output (the STDOUT file attached to
the "date" PROCESS), and then ... unless told otherwise, it streams the output it to the screen.

The > redirect symbol, is interpreted by the Shell itself - not the "date" program, and it is the shell that
opens the "NewFile.txt" file, and redirects the STDOUT from the "date" command into that file. 

Its just plumbing. This is the simplest example, and everything from here on follows the exact same
interaction.  A process takes some input, does some fiddling, and generates some output.  

The output from one process or file can become the input of another process or file.

What the "cat" command does, is open a file, and then conCATenate that file onto its own STDOUT.

Which STDOUT are we talking about now ?  It concatenates the file to the Shell's STDOUT.

How does that get on the screen ?  Does the Shell write to the screen ?  Well, no. The Shell in 
this case is being executed by the Terminal Program. The Terminal program takes input from the 
keyboard, and sends it to the shell. The Shell outputs everything to its own STDOUT .. which the
terminal program is reading ... and outputting that to the screen.
```

This is the simplest, but also the most complex interaction. Once you get this, you get all of it.

A web server with an SQL database, serving up pretty pictures, videos, and animated buttons with
interactive gradients on a user's web browser ... is pretty much exactly the same interaction as 
the one above.

Processes with outputs connecting to the inputs of other processes. Everything is a file. 

Everything that a Unix computer does is never simpler than this, but its also never more complicated
than this either.  Don't expect that to answer everything just yet, but keep it in mind, and ponder
on that whenever you do anything from here on.

Move the mouse and observe the pointer drift over the screen ... think about what that means
in terms of inputs and outputs and files.


### > Redirect

Lets do a bit more with redirects, whilst that bit above bits about files and terminals and STDOUT sinks in.

Try this : 

(HINT: Hitting the UP arrow in the shell allows you to automatically recall previous commands)

```
[my-name@localhost ~] $ cd ~/Documents/NewDir
[my-name@localhost NewDir] $ date
[my-name@localhost NewDir] $ date > NewFile.txt
[my-name@localhost NewDir] $ cat NewFile.txt
... OK, thats what we expect
```

and then try this :

```
[my-name@localhost NewDir] $ date > NewFile.txt
[my-name@localhost NewDir] $ cat NewFile.txt
... OK, thats what we expect, again

[my-name@localhost NewDir] $ date >> NewFile.txt
[my-name@localhost NewDir] $ cat NewFile.txt
... OK, thats different

[my-name@localhost NewDir] $ date >> NewFile.txt
[my-name@localhost NewDir] $ date >> NewFile.txt
[my-name@localhost NewDir] $ date >> NewFile.txt
[my-name@localhost NewDir] $ cat NewFile.txt
... how many dates do you have now ?

[my-name@localhost NewDir] $ ls -l >> NewFile.txt
[my-name@localhost NewDir] $ cat NewFile.txt

[my-name@localhost NewDir] $ ls -l .. >> NewFile.txt
[my-name@localhost NewDir] $ cat NewFile.txt

... how many lines are in that file now ?

[my-name@localhost NewDir] $ wc -l NewFile.txt
... wc (short for Word Count), the -l option tells it to report lines only
```

So, from that we can work out that > redirects the output into a file, overwritting it.

And >> appends the output onto the end of a file.

### More magic tricks |

The "|" symbol is called the "Pipe" operator.

It literally connects a pipe between 2 different programs that run at the same time.

Try this :

```
[my-name@localhost NewDir] $ wc -l NewFile.txt
... OK, we know that one now

[my-name@localhost NewDir] $ cat NewFile.txt | wc -l
... Its the same ???
```

What happened here ?

The second command, "cat NewFile.txt" conCATenates the contents of NewFile.txt to STDOUT, and the Pipe 
symbol "|" tells the shell to connect that STDOUT to the input of the WordCount command.

In order for this to work, the Shell fires up BOTH processes, and connects the output of one to the input
of the other. They both run at the same time in this case.

The input of each PROCESS is referred to as the STDIN, or "Standard Input".  The STDIN for any process
is usually the keyboard (when run from a terminal), but it can be any source ... such as a file, 
another process, or a network connection.

Compare these 2 commands : 

```
[my-name@localhost NewDir] $ wc -l NewFile.txt
[my-name@localhost NewDir] $ wc -l < NewFile.txt
... Its the same ???
```

The < operator tells the shell to Redirect the STDIN for the process from a file.

Is there any major difference between these 2 commands and how they run ?

Yes, absolutely.

In the first instance, the WordCount program is executed, and it reads through it's command
line arguments to get a list of files to process. The WordCount program is responsible for opening each file,
and reading its input from that file.

In the second instance, the WordCount program is executed, and it sees NO filenames on it's command
line arguments, so it reads input line by line from STDIN and reports on what it saw there. The Shell
is responsible for opening the file and concatenating it to the STDIN of the WordCount process.

### Shell Tricks

Lets push the shell a bit further now.

The Shell not only takes commands and runs them, with redirection and piping tricks, but it is also 
a simple programming language in itself.

What we are going to do now, is write a simple little one-line script to get the Shell to do some 
heavy lifting for us.

Try this :

```
[my-name@localhost NewDir] $ seq 1 100
... The seq (short for SEQuence) command generates a sequence of numbers for us automatically

... now type the following in, word for word, don't forget the backticks "`" which are in the
top left corner of a normal keyboard :

[my-name@localhost NewDir] $ for i in `seq 1 100`; do echo The Number is $i; done

... Putting something in backticks ` means "run this command, and substitute the output inline"
    in other words, its short hand for typing all the numbers from 1 to 100

... if that worked, then do something useful with this new construct

[my-name@localhost NewDir] $ for i in `seq 1 100`; do date >> NewFile.txt; done

... what did that do ?

[my-name@localhost NewDir] $ cat NewFile.txt
```

Looks like it added 100 new dates to the end of our ever growing date collection.

Oh - and BTW, you just wrote "a program". You are now officially a programmer.

Not terribly useful on its own, but this is a small taster for what you can do with the Shell,
and from there, other programmable environments.

Any actions that are repetitive or predictable sequences can be easily automated. The Shell is 
an ideal tool to get used to this concept, because the same extensibility applies when doing
anything web related. 

In web terms, a lot of web page content is generated from mixing templates and data together, and
its always a case of writing short loops and logic like this to generate the output rather than 
typing things in a million times over for every combination.

This also applies to simple "non data" type of things in web pages, such as CSS colors for example. 
Within CSS, you can specify a base color for a site, and then have the computer automatically calculate
various tints and shades of that base color to create a complimentary palette, rather than 
manually come up with a palette. If you change the base color for the whole site - in 1 place - then all
the complimentary tints and shades adjust automatically.

On that note, always think about ways to talk to the computer in general terms rather than lots of 
specific and repetitive ways.

### grep it to grok it, more or less

Files can get very large very quickly.

Here are some useful tools to view file contents that you should get to know.

Try This :

```
[my-name@localhost NewDir] $ ls -ltr
[my-name@localhost NewDir] $ more NewFile.txt

... The "more" program is an original Unix utility to paginate long output into page-sized chunks that can
    be interactively scrolled. Hit Q to get out of it.

[my-name@localhost NewDir] $ less NewFile.txt

... The "less" program behaves similarly to "more". They are the same but different, less being developed
    in more recent years to bypass some old fashioned licencing from the original Unix variant.

    Unix / Linux etc - there are lots of programs like this that have names which are puns on some original
    utility. Many variations of the same program can be found side by side like this. Exersize for the 
    reader to find more.

    eg: The orignal "yacc" program which is used to build new compiler languages
    (yacc = yet another compiler compiler), has a modern variant called "bison".
    The list is endless.

[my-name@localhost NewDir] $ date

... What day of the week is it ?  Lets say its Saturday, adjust your input accordingly for the following commands

[my-name@localhost NewDir] $ grep Sat NewFile.txt

... Shows a list of dates from that file that contain the word "Sat", for Saturday

[my-name@localhost NewDir] $ grep sat NewFile.txt

... Thats no good. Grep is case-sensitive, its looking for Sat, not sat

[my-name@localhost NewDir] $ grep -i sat NewFile.txt

... -i means case insensitive match, which finds both Sat and sat

```

Grep has a tonne of options to find things ... including what are called "Regular Expressions".
RE (Regular Expressions) are a type of query language used to perform horribly complex searches on
vast amounts of text data.

Its generally simple, but can get ridiculous pretty quickly. Stick to simple.

Nobody in the history of Computer Science has ever become fully 100% fluent in Regular Expressions, but 
thats fine, you just need to be able to recognize them when you see them, and know how to look up ansvers
to your own RE questions on Google or StackOverflow when you need to use them.

RE parsing is built into Javascript and all Web Browsers, (and its even found its way into CSS as well),
so its something that is hard to avoid on the web.


Lets have a look at some things while we are here to hook some of this together.

Try this, using the UP arrow to save typing :

```
[my-name@localhost NewDir] $ ps
... There should be at least 1 program called bash running under your account

[my-name@localhost NewDir] $ ps | grep bash
... There they are.  Lets get the first line from that list

[my-name@localhost NewDir] $ ps | grep bash | head -n 1
... The head command gets the first N lines of the input - in this case, we just want the 1st line

... Now we want to get the first field from that line
[my-name@localhost NewDir] $ ps | grep bash | head -n 1 | cut -d' ' -f 1
... The cut command cuts a line into parts, in this case we split fields by spaces, and get the first field, 
    which is the process number.

... Now, lets look for something interesting with that process number.

[my-name@localhost NewDir] $ cd /proc
[my-name@localhost proc] $ ls

... Lots of numbers. One per running process in fact.

[my-name@localhost proc] $ cd <the-number of your bash process>
[my-name@localhost some-big-number] $ ls
... All the things

[my-name@localhost some-big-number] $ cat status
... status info on your bash process
```

Your current bash process ... is a file.


### cp  CoPy a file

Try this :

```
[my-name@localhost 515151] $ cd ~/Documents/NewDir
[my-name@localhost NewDir] $ ls -ltr
[my-name@localhost NewDir] $ cp NewFile.txt NewFile2.txt
[my-name@localhost NewDir] $ ls -ltr
```

cp is used to CoPy a file.

cp has a few options.

Try this :

```
[my-name@localhost NewDir] $ cd ~/Documents
[my-name@localhost Documents] $ cp NewDir NewDir2
... fail - NewDir is a directory, not a file

[my-name@localhost Documents] $ cp -r NewDir NewDir2
... thats better

[my-name@localhost Documents] $ cp --help
... lots of options, not many useful options
```

While we are here, lets have a look at something interesting.

### df  Disk Full

Try this :

```
[my-name@localhost NewDir] $ df
```

df shows all your mounted drives, and how much space is being used


### du  Disk Usage

Try this :

```
[my-name@localhost NewDir] $ cd
[my-name@localhost ~] $ du -x -sk *
```

du is short for Disk Usage

-x means span this filesystem only
-s does a summary of each parameter
-k converts all numbers to Kilobytes

and then this :

```
[my-name@localhost ~] $ du -x -sk * | sort -n
```

Pipes the output of the disk usage to the sort program, -n means numeric, so it sorts it in order of size
for each directory.


### echo  

### $ENV  Environment variables

### $PATH  Program search path

### ping   PING another machine

Try this :

```
$ ping google.com
```

### chmod - CHange MODe


### Bash setup and environment variables



### More Dates and Times

Try these :

cal
cal 2017







