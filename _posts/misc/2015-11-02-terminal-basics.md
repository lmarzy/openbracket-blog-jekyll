---
category: misc
---

Terminal, terminal! I hear you scream. But I can just point a click and things work. I actually find working in the terminal quite enjoyable, it makes me feel like some sort of computer wizard or something and look like I know what i'm doing to the less technical (sure fire way to impress the ladies :-)).

Although I use the terminal on a regular basis I still feel I am just getting by, and just getting by is not quite good enough, I am going to document some of the basics of the terminal, well because I can and it would be good for mine or your future reference.

So, The terminal is a text interface for your computer. It's a program that takes in commands, which it passes on to the computer's operating system to run.

From the terminal you have a lot of power, you can navigate through the file system, run programs and write scripts to automate tasks.

I am a mac user and this post will focus on the unix-based commands, you can also do most if not all of this on windows but there is some variances which I will leave up to you to find out.

My terminal of choice is a program called 'iTerm' which is a highly customisable and has a nicer interface but the standard terminal you have will do just fine.

So fire up you chosen terminal and lets get going.

Once fired up you should see $, this is called the 'shell prompt', it appears when the terminal is ready to accept commands.

Lets go through some basic commands, type the following into the terminal as we go along to get a better understanding and reinforce learning. All the following are examples of commands, a directive to the computer to perform a task.

{% highlight console %}
$ ls
{% endhighlight %}

'ls' lists the contents of the current directory.

We can also pass a modifier to give us different results

There are a few more modifiers for ls

- $ ls -a lists contents, including hidden files and directories
- $ ls -l lists all contents in long format
- $ ls -t lists contents by time they were last modified

You could also use 'ls' with all the modifies together:

{% highlight console %}
$ ls -alt
{% endhighlight %}

Note: files that begin with a '.' are hidden by default.

{% highlight console %}
$ pwd
{% endhighlight %}

pwd stands for "print working directory". It shows the name of the directory you are currently in, called the working directory.

{% highlight console %}
$ cd
{% endhighlight %}

cd stands for "change directory". This command allows you to navigate into different directories from where you are.

to move into a child directory you can run:

{% highlight console %}
$ cd 'child-directory'
{% endhighlight %}

you can also move more than one directory at a time:

$ cd 'child/sub-child/'

you can also move up one or more directories:

{% highlight console %}
$ cd ..
{% endhighlight %}

{% highlight console %}
$ cd ../../
{% endhighlight %}

{% highlight console %}
$ mkdir
{% endhighlight %}

The mkdir command stands for "make directory". It takes in a directory name as an argument, and then creates a new directory in the current working directory.

{% highlight console %}
$ mkdir new
{% endhighlight %}

{% highlight console %}
$ touch
{% endhighlight %}

The touch command creates a new file inside the working directory. It takes in a filename as an argument, and then creates an empty file in the current working directory.

{% highlight console %}
$ touch new.txt
{% endhighlight %}

So far we have been using the terminal to navigate the file system, there is lots more you can do in the terminal so lets crack on.

{% highlight console %}
$ cp
{% endhighlight %}

The cp command copies files or directories, this accepts two parameters. The first parameter is what you are copying and the second is where you are copying:

{% highlight console %}
$ cp textfile1.txt textfile2.txt
{% endhighlight %}

This will copy the contents of textfile1 into textfile2. You can also copy files from one location to another:

{% highlight console %}
$ cp /dir/textfile.txt dir/dir/
{% endhighlight %}

This will copy the file textfile.txt into a directory called dir.

To copy multiple files into a directory you can pass a list of source files with the destination directory:

{% highlight console %}
$ cp textfile1.txt textfile2.txt dir/
{% endhighlight %}

To copy all files from a directory into another directory you can pass the * as the first argument:

{% highlight console %}
$ cp * dir/
{% endhighlight %}

Or copy all files beginning with a particular letter:

{% highlight console %}
$ cp a* dir/
{% endhighlight %}

As well as copying we can also move, all the above also works for moving files:

{% highlight console %}
$ mv
{% endhighlight %}

{% highlight console %}
$ rm
{% endhighlight %}

This command deletes files and directories

{% highlight console %}
$ rm textfile.txt
{% endhighlight %}

The rm command also allows modifiers

$ rm -r the r stands for recursive and is used to delete a directory and all of it's child directories. Be warned with this one as there is no undo button once you delete something!

So, there you have it. The above is just an intro to what you can do in the terminal, I will look at doing some further posts going deeper into the terminal so stay tuned.

Until next time.
