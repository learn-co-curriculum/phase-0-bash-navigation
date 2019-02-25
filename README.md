# CLI Essentials: Basic Commands in Bash

## Learning Goals

* Demonstrate how to navigate the CLI with Bash
* Demonstrate interacting with files and directories in the command line

## Introduction

Using the CLI (command line interface) might seem like a big challenge to first
time users who are afraid of making mistakes that could impact their computers
or files. Fear not! We'll step you through it.

There are two main command-line interfaces, or "shells", that many developers
use. On OSX or many Linux installations, the shell is known as `bash`. For users
on Windows-based systems, the command-line interface is called the "DOS Prompt"
or "Powershell," which uses different commands and syntax, but can often achieve
similar tasks. With the addition of the "Widows Subsystem for Linux" or "WSL,"
Windows users can launch a terminal emulator which runs, guess what, `bash`, just
like a Linux or OSX system! We'll document how to use the `bash` CLI in this
module.

## Demonstrate How to Navigate With `bash`

To sum up: `bash` is a text-based interpreter that provides a _command-line
interface_ for controlling your computer (or operating system).

> **ASIDE**: Bash is actually an acronym which stands for **B**ourne-**A**gain
> **SH**ell. As the word "again" suggests, there are _other_ shells, some of
> which came before `bash`. There are also shells that have come along _since_
> `bash`. Nevertheless most programmers use `bash` or something very similar.

Learning to navigate through your computer's file system is a great first step
to feeling "safe" using this tool. As you start to become familiar with the
shell and its potential, you'll quickly see that it's not a as unapproachable as
it might look when you see characters in TV shows and movies vigorously typing
away on their computers to "hack" systems.

!["Ghost in the Shell"](https://media.giphy.com/media/fsoCk5kgOcYMM/source.gif)

### Identify My Logged-In Username

Let's start simply. Let's ask the computer who I am logged in as:

```bash
$ whoami
```

 < probably need screen shot>

The `whoami` command lets you see which user account you're logged in to from a
terminal window. This might seem obvious, especially if you're logged in on your
personal computer, but it's not always clear which account you're running
commands as. Unix machines have multiple accounts by default (though you may not
have seen them yet). Some of those accounts have superpowers and it's possible
to really mess up your computer when you're acting as them. Sometimes before
doing something drastic we like to run a quick `whoami` to make sure we're doing
what we want to do.

### Identifying the Current Working Directory" With `pwd` ("print working directory")

The files on a computer are arranged in what is called a _hierarchical directory structure_. 
This means that they are organized in a tree-like pattern of directories (called
folders in other systems), which may contain files and other directories. The
first directory in the file system is called the _root directory_. The root
directory contains files and subdirectories, which contain more files and
subdirectories and so on.

Most graphical environments today include a file manager program to view and
manipulate the contents of the file system that may look like this:

<KG: image of file system tree;>

Since a command line interface cannot provide graphic pictures of the file
system structure, it represents it differently. Think of the file system tree as
a big room with furniture and doors to other rooms, and you are standing in it.
At any given moment, you are located in a single directory (or "room") called the "working
directory."  From that directory, you can files it contains ("the furniture in the room") and the pathway to its
parent directory and the pathways to its subdirectories.

With your terminal program open, type in `pwd` and hit return/enter to find the
name of the working directory.

```bash
$ pwd
```

**Note:** *Any time you see the* `$` *character, you shouldn't type it in. This
is just a standard way to represent a bash prompt. Yours may or may not be a*
`$`.

You should see some output describing the directory you are currently in.
The `pwd` command stands for "**p**rint **w**orking **d**irectory". When you
first set up your computer, the operating system created a directory under
the "User" directory that was named the same as your `whoami` result:

`/Users/[your user name]`

Some unix interfaces will create your directory under `/home` e.g.:

`/home/[your user name]`

We call this directory your "home" directory. Whenever you open a terminal
session (new window, new terminal tab, launching the program for the first time
after a reboot), you will be placed in your home directory. Said another way
your working directory will be, by default, set to your home diretory &mdash;
that's what makes ityour home!

That output is describing a location on your computer.

<insert screenshots showing navigating from / to Users to kellyegreene with
Finder> <insert screenshot of pwd>

<pic of pwd>

`/User/kellyegreene` means that I am currently working within a directory
`/Users` on the root (or top-most containing directory) on my machine. Within that `/Users` directory, a directory
exists named `kellyegreene`. That's my home directory. 

We passed over it quickly, but the top-most directory, that contains all the folders
and sub-folders on the machine is called the "root" directory.

<pre>
/                                <-- "the root directory"
  etc
  var
  tmp
  Users
    kellyegreene
    myannoyingbrother
    grandma
</pre>

As a shortcut instead of typing `/home/[your login name]`,
`bash` lets us type `~` as a shortcut. We'll be working with this shortcut later
on.

Try typing this in the command line:

```bash
$ cd ..
$ pwd
```

You "moved up" one level of nesting, so you should now see that you are one
level up from where you were and one level closer to the "root" directory.
In your terminal you might see by using `pwd`:

`/Users`

You should be able to make a guess about what `cd` does, but we'll explain it
right now!

### Change Directories Using `cd`

In the previous example, the `cd` command stands for "**c**hange **d**irectory".
The `..` represents the directory _above_ the working directory.

These are three default placeholders for your file system:

- `~` Your **home** directory (already mentioned)
- `.` The **current** directory
- `..` The directory in which your current directory is contained—referred to as
  the "**parent**" directory.

If you try this command:

```bash
$ cd .
$ pwd
```

You should see you are still in the same directory. If you `cd ~` you'll hop
back to your home directory. You can supply any path to
the `cd` command to navigate to that location.

### Paths in Shell

The path supplied to the `cd` command can be either *absolute* or *relative*
paths. An absolute path is a path that always gets you to the same folder. You
can recognize them because they start with `/`. For example
`/Users/kellyegreene`, is an absolute path.

A relative path is a path **relative** to the working directory of the user or
application, so the full absolute path will not have to be given. They start
with the name of a directory or a file. For example `kellyegreene/Documents`, is
a relative path.

If I were in my home directory `/Users/kellyegreene` and said `cd
mixtapes/the-masked-rapper-vol-1`, it would work! If I were in
`/Users/annoyingbrother` and said `cd mixtapes/the-masked-rapper-vol-1`, `bash`
would return an error because that sub-directory doesn't exist there – because
I, Kellye Greene, am the Masked Rapper while my brother can't rhyme.

Relative paths exist to make it simpler to move around. Real life is like this
too. If someone asks if you want to go get a slice of pizza they're probably
thinking within a few blocks or miles of where you're currently located –
somewhere close _relatively_ speaking.

"Oh yeah, let's go west on 18th street, cross 6th avenue and go to the place on
the corner."

What would surprise the heck out of them would be if you gave them absolute
coordinates; and it would be _even more_ surprising if that location were far
away:

"Oh yeah, let's go to 41.890221 and -87.633904!" Latitude and longitude give
_absolute_ directions based on the Equator and Prime Meridian. They're not
commonly used by humans to make decisions on where to get lunch (even if
it points to one of our favorite pizzerias in Chicago).

Paths use `/` to denote levels.

So far we've been finding out where we are in the filesystem "tree," how about
we find out what's in these directories (besides other directories)?

## Conclusion

As we keep exploring and working with the command line, we will start to unlock
and understand its full potential! Adopting the terminal for command-related
interactions can allow us to become more productive users-—we work on multiple
projects, tasks, and easily switch contexts and folders. It's also the root (pardon
the pun) of all computing systems. While syntax might vary between operating systems, the
functions that we are given through terminal applications are the same.

## Resources

- [Lifehacker on the Command Line](http://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything)
- [Environment Variables](http://cbednarski.com/articles/understanding-environment-variables-and-the-unix-path/)
- [Built-in Shell Commands](https://www.gnu.org/software/bash/manual/html_node/Bash-Builtins.html) *Very useful*
- [15 Useful Bash Commands](http://www.thegeekstuff.com/2010/08/bash-shell-builtin-commands/)
- [The One True Path](http://blog.seldomatt.com/blog/2012/10/08/bash-and-the-one-true-path/)
- [More on paths - Wikipedia](http://en.wikipedia.org/wiki/Path_\(computing\))
