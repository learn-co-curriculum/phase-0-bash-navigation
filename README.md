# Navigation Commands in Bash

## Learning Goals

* Define a Unix path
* Identify typical Unix "Home Directory" paths
* Identify my logged-in username with `whoami`
* Identify the current working directory" with `pwd` ("print working directory")
* Navigate up one directory in the file system
* Navigate back to a home directory
* Demonstrate how to navigate the CLI with Bash

## Introduction

Using the CLI (command line interface) might seem like a big challenge to first-time
users who are afraid of making mistakes that could break their computers
or ruin their files. Fear not! We'll step you through it.

The command-line interfaces, or "shells", used on OSX and Linux and the "Windows Subsystem for Linux" or "WSL," is called 
`bash`. We'll document how to use the `bash` CLI in this module.

## Demonstrate How to Navigate With `bash`

To review: `bash` is a text-based interpreter that provides a _command-line
interface_ for controlling your computer (or operating system).

> **ASIDE**: Bash is actually an acronym which stands for **B**ourne-**A**gain
> **SH**ell. As the word "again" suggests, there are _other_ shells, some of
> which came before `bash`. There are also shells that have come along _since_
> `bash`. Nevertheless most programmers use `bash` or something very similar.

A great place to start learning about the CLI is by using it to do a task
you're already familiar with: looking to see what's inside folders like
your directories and desktop. Programmers call this activity: _navigating_.
In the CLI we imagine that we're "traveling" to different places. We'll use
metaphors like "go into the folder" or "go up one folder" or "visit the location
at such-and-such _path_."

As you learn to navigate with the shell and get to used to it, you'll see that it's friendlier than it
might seem at first. In no time, you'll be looking like this typing-machine from "Ghost in the Shell:"

!["Ghost in the Shell"](https://i.giphy.com/fsoCk5kgOcYMM.gif)

### Identify Our "Home Directory"

Whenever you open a terminal session (new window, new terminal tab, launching the program for the first time
after a reboot), you will be placed in your home directory. Directory names on Unix systems are written
like: 

`/parentdirectory/subdirectory/another/subdirectory/`

We call a bit of text meant to communicate location on a file system a _path_. Paths use `/` to show levels of "nesting."

For example, a user's home directory is often written like: `/Users/username` or `/home/username`. The `/` on the far left of the path name means the very top of the file system "tree." The `/` directory is also called the "root" directory. It contains all the directories that contain sub-directories.

Let's take a second to look at some typical home directories:

`/Users/username`

This means the "root" contains a directory called `Users` and `Users` contains `username`. Paths like this are typical for Mac OSX.

`/home/username`

This means the "root" contains a directory called `home` and `home` contains `username`. Paths like this are typical for Linux.

Obviously, our names (well, most of our names) are not `username`. Instead we log into our systems as `Byron Poodle` or `Nancy the Cat`. How can we find out what our logged in user name is? We can ask the shell to tell us who it thinks we are. We'll use `whoami` to do just this in the next section.


### Identify My Logged-In Username with `whoami`

Let's start simply. Let's ask the computer who I am logged in as:

```bash
$ whoami
```

!["whoami"](https://curriculum-content.s3.amazonaws.com/prework/whoami.jpg)

The `whoami` command lets you see which user account you're logged in to from a
terminal window. This might seem obvious, especially if you're logged in on your
personal computer. But Unix machines have multiple accounts by default (though you may not
have seen them yet). Some of those accounts have superpowers and it's possible
to really mess up your computer when you're acting as them. Sometimes before
doing something drastic we like to run a quick `whoami` to make sure we're doing
what we want to do. Or, to install some software you might need to perform that action
as a "super user" – kind of like when you need to enter your login password in order to
install new software updates.

My system says I am `kellyegreene`. Based on what we learned about home directories, what
do you think my home directory _path_ is? In the next section, we'll ask the shell to tell us
what our home directory's path is.

### Identify the Current Working Directory" With `pwd` ("print working directory")

```bash
$ pwd
```

**Note:** *Any time you see the* `$` *character, you shouldn't type it in. This
is just a standard way to represent a bash prompt. Yours may or may not be a*
`$`.

You should see some output describing the directory you are currently in.
The `pwd` command stands for "**p**rint **w**orking **d**irectory". As you
"navigate" your file system, you might get lost. Just like wandering in a big
city, you can look for street signs to find out where you are. The `pwd` command
acts like those street signs. You'll never be lost again!

We've just used `pwd` to demonstrate that when we open a `bash` session the
operating system automatically "puts" us in our home directory. Let's now do
some real "navigation." In the next section we'll learn to move "up" one containing
directory.

### Navigate Up One Directory in the File System

Try typing this in the command line:

```bash
$ cd ..
$ pwd
```

You "moved up" one level of nesting, so you should now see that you are one
level up from where you were and one level closer to the "root" directory.
In your terminal see this by using `pwd`:

`/Users`

The `cd` command stands for "**c**hange **d**irectory".
The `..` represents the directory _above_ the working directory. The `bash` shell
provides a series of "shortcuts" for some commonly-used file system paths. `..` means
"this directory's containing folder.

So in this command example we said: `change directory to the parent folder`.

Let's use `cd` to get back to our home directory.

### Change Directories Using `cd`

The `bash` shell provides default shortcut for your home directory: `~`.

If you try this command:

```bash
$ cd ~
$ pwd
```

You'll see you're back in your home directory. Also, by the way, if you enter
`cd` with no argument, you'll be taken to your home directory.

Another shortcut, that might seem not too useful at first, is `.` meaning "the current
directory I'm in.

If you try this command:

```bash
$ cd .
$ pwd
```

You should see you are still in the same directory where you wrote
the command.

Instead of using shortcuts like `..`, `.`, or `~`, you can give a
path to `cd` and it will "take" you there.

Try `cd /Applications` or even `cd /`. You can run a `pwd` in these directories
and see that you've "navigated into" them. Try `cd alksdjfalksdjfalskdjf`. What
error does `bash` give you? Is that what you expected? We'll discuss more
about the types of paths you can give `bash` in the next section.

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
would return an error because that sub-directory doesn't exist there (because
I, Kellye Greene, am the Masked Rapper, while my brother can't rhyme).

Relative paths exist to make it simpler to move around. Real life is like this
too. If someone asks if you want to go get a slice of pizza they're probably
thinking within a few blocks or miles of where you're currently located –
somewhere close _relatively_ speaking.

"Oh yeah, let's go West on 18th street, cross 6th Avenue and go to the place on
the corner."

What would surprise the heck out of them would be if you gave them absolute
coordinates; and it would be _even more_ surprising if that location were far
away:

What if you replied to the question about pizza with: "Oh yeah, let's go
to 41.890221 and -87.633904!"

Latitude and longitude give _absolute_ directions based on the Equator and Prime Meridian. They're not
commonly used by humans to make decisions on where to get lunch (even if
it points to one of our favorite pizzerias in Chicago).

So far we've been finding out where we are in the file system "tree," how about
we find out what's _in_ these directories (besides other directories)? We'll
cover that in our next lesson.

## Conclusion

As we keep exploring and working with the command line, we will start to unlock
and understand its full potential! Adopting the terminal
can allow us to become more productive users.

## Resources

- [Lifehacker on the Command Line](http://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything)
- [Environment Variables](http://cbednarski.com/articles/understanding-environment-variables-and-the-unix-path/)
- [Built-in Shell Commands](https://www.gnu.org/software/bash/manual/html_node/Bash-Builtins.html) *Very useful*
- [15 Useful Bash Commands](http://www.thegeekstuff.com/2010/08/bash-shell-builtin-commands/)
- [The One True Path](http://blog.seldomatt.com/blog/2012/10/08/bash-and-the-one-true-path/)
- [More on paths - Wikipedia](http://en.wikipedia.org/wiki/Path_\(computing\))
