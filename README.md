# CLI Navigation

## Learning Goals

- Demonstrate How to Navigate from the CLI
- Identify your "home directory"
- Identify your logged-in username with `whoami`
- Identify the "current working directory" with `pwd` ("print working directory")
- Navigate directories using `cd`

## Introduction

Using the CLI (command line interface) might seem like a big challenge to
first-time users who are afraid of making mistakes that could break their
computers or ruin their files. Fear not! We'll step you through it.

Unix-like operating systems like MacOS, Linux, and Windows Subsystem for Linux
(WSL) all have a command-line interface, or "shell" application. While there are
several different shell applications, like `zsh` (the default for MacOS) and
`bash` (the default for Ubuntu in WSL), all these shell applications share a set
of common commands which developers are familiar with. In this section, we'll
cover some of the most common commands used by developers.

To follow along, go ahead and launch your terminal (the Terminal application for
MacOS and Ubuntu for WSL).

## Demonstrate How to Navigate with a Command-Line Interface

To review: a **shell** is a text-based interpreter that provides a _command-line
interface_ for controlling your computer. As a developer, you will use **shell
commands** to move around in your project directories to accomplish
different tasks (e.g., creating, renaming, moving or copying files or folders).
Programmers call this activity: _navigating_. In the CLI we imagine that we're
"traveling" to different places. We'll use metaphors like "go into the folder"
or "go up one folder" or "visit the location at such-and-such _path_."

When navigating through a directory, it often helps if we picture the file
structure as a tree. With this visualization, we can refer to "moving up" or
"moving down" between directory levels, and keep better track of not only where
our files are but where we are among our files. Here's an example:

!["Directory tree structure diagram"](https://curriculum-content.s3.amazonaws.com/cli-essentials/bash-navigation/Image_58_DirectoryStructureDiagram.png)

A location within a file system is identified using something called a _path_.
For example, the path to the `lesson1.txt` document in the file structure
pictured above would be:

```console
/home/my_site/webappdev/unix/notes/lesson1.txt
```

The `/` characters in the path represent the "nesting" of folders or files
inside other folders.

### Identify Our "Home Directory"

Whenever you open a terminal session, either by launching the program or by
opening a new window, you will be placed in your _home directory_.

Typically, the path to the home directory looks like this for Mac OSX:

```console
/Users/username
```

and like this for Linux:

```console
/home/username
```

The `/` on the far left of the path name means the very top of the file system
"tree." The `/` directory is also called the "root" directory. It contains all
the "top-level directories" that can contain sub-directories (...which can
contain sub-directories, which can contain sub-directories, on and on).

So the home paths above indicate that the "root" contains a directory called
`Users` or `home` (depending on your operating system), which in turn contains
`username`. Obviously, our names (well, most of our names) are not `username`.
Instead we log into our systems as `Byron Poodle` or `Nancy the Cat`. How can we
find out what our logged-in-user name is?

### Identify My Logged-In Username with `whoami`

We can ask the computer who we are logged in as using the `whoami` command:

```console
$ whoami
```

**Note:** _Any time you see the_ `$` _character, you shouldn't type it in. This
is just a standard way to represent the command prompt in a shell application.
Yours may or may not be a_ `$`.

!["whoami"](https://curriculum-content.s3.amazonaws.com/prework/whoami.jpg)

The `whoami` command lets you see which user account you're logged in to from
the CLI. This might seem obvious, especially if you're logged in on your
personal computer. But Unix machines have multiple accounts by default (though
you may not have seen them yet).

My system says I am `kellyegreene`. Based on what we learned about home
directories, I could figure out what my home directory should be, but there's an
easier way: we can ask our computer to tell us what path we're in!

### Identify the "Current Working Directory" With `pwd` ("print working directory")

Try running the following:

```console
$ pwd
```

You should see some output describing the directory you are currently in. It's
probably something like `/Users/byron_the_poodle`.

The `pwd` command stands for "**p**rint **w**orking **d**irectory". As you
"navigate" your file system, you might get lost. Just like wandering in a big
city, you can look for street signs to find out where you are. The `pwd` command
acts like those street signs. You'll never be lost again!

We've just used `pwd` to verify that when we open the shell application, the
operating system automatically "puts" us in our home directory. Now let's learn
how to do some real "navigation" in our file structure.

### Change Directories Using `cd`

Try typing this in the command line:

```console
$ cd ..
```

This command "moves up" one level of nesting, so you should now be one
level up from where you were and one level closer to the "root" directory.
Verify this by running `pwd` again:

```console
/Users
```

The `cd` command stands for "**c**hange **d**irectory".

The `..` is a shortcut for the directory _above_ the working directory. The
shell application provides a series of "shortcuts" for some commonly-used file
system paths. `..` means "this directory's containing folder". These shortcuts
look strange but they're designed to be _short_ and therefore _easy to type_ and
therefore _fast_ and, as we've hinted, the CLI is all about speed.

So in this command example we said: `change directory to the parent folder`. You
could run the same command again to navigate up to the `/` (root) directory.

Another shortcut, that might not seem very useful at first, is `.` meaning "the
current directory I'm in."

If you try this command:

```console
$ cd .
$ pwd
```

You should see you are still in the same directory where you wrote the command.
You will learn a bit later in the course about when and how the `.` is used.

The shell application provides one additional shortcut: `~`. This symbol is used
to indicate the home directory.

If you haven't already, use `cd ..` a second time to go "up" another level to
the root directory. Run `pwd` to verify; you should see `/` output.

You can then navigate back to your home directory by running:

```console
$ cd ~
```

You'll see you're back in your home directory. Use `pwd` to verify!

> **Note:** Actually, you don't even need the `~`! If you enter `cd` with _no_
> argument from anywhere in your file structure, you'll be taken to your home
> directory.

### Paths in Shell

In addition to shortcuts like `..` or `~`, you can also provide a **path** as
the argument to the `cd` command. For example, another way I could get back to my home
directory is to run this command:

```console
$ cd /Users/kellyegreene
```

Or, equivalently (in this case):

```console
$ cd Users/kellyegreene
```

Note the difference between these two commands: the first one, which has the `/`
at the front, is called an _absolute_ path. The second, without the leading `/`,
is a _relative_ path.

The difference between the two is that the _absolute_ path will always get you
to the destination folder, regardless of where you currently are in the file
structure. The absolute path tells the shell application to start from the root
directory (`/`), then go "down" into `Users`, then "down" again into
`kellyegreene`.

The _relative_ path, on the other hand, tells the shell application where to
navigate **relative** to where you currently are in the file structure. So, if
I'm in the root directory, I can use the `cd Users` command, but if I'm
somewhere else in the file structure, typing `cd Users` will give me an error:

```console
cd: no such file or directory: Users
```

To get to the `Users` directory (without using one of the shortcuts), I
could either use `cd ..` until I'm back at the root directory then run `cd
Users` **or** I could use the absolute path.

If the difference between relative and absolute paths is still unclear, try
thinking of it in terms of giving a friend directions to your house. In most
cases, you (or your friend's GPS system) will give them directions _relative_ to
some starting point, but you could also give them the exact latitude and
longitude of your house, which will work no matter where they start from.

## Time-Saving Tip: Tab Completion

As you type in commands in the shell, you can use "tab completion." Tab
completion allows the shell to be smart and to try and guess what command you
want to run when you hit the tab. If there's only one logical way to complete
your command, the shell application will fill in the rest for you. If there are
multiple possibilities, it will show those to you and you can continue to add
letters until the shell application can tell exactly what you're trying to do.

For example let's say I'm in a directory that has the following two sub-
directories:

```console
/flatiron_school
/flatiron_building
```

If I type `$ cd f` and then hit `tab`, it will fill in everything that's the
same, so I'll see `$ cd flatiron_`. If I then add the `s` and hit `tab` it will
fill in `$ cd flatiron_school` and I can hit enter.

Tab completion can also be used with the other shell commands we'll be learning
in the lessons that follow.

## Conclusion

As you continue to explore and work with the command line, you will start to unlock
and understand its full potential! Becoming comfortable with working in the
terminal will allow you to become more productive.

So far we've been finding out where we are in the file system "tree." Next,
we'll learn how to explore what's _in_ these directories.

## Resources

- [Lifehacker on the Command Line](http://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything)
- [More on paths - Wikipedia](http://en.wikipedia.org/wiki/Path_(computing))
