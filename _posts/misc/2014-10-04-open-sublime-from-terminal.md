---
category: misc
---

A quick tip on opening up Sublime text form the terminal, if your like me and spend a lot of time in the terminal and my favourite editor at the moment is sublime text. I find it really useful to be able to open up Sublime after I have browsed to the directory for the site I am working on and launching sublime with all my files ready.

This is for Mac by the way, if you use windows I'm extremely sorry!

To make the subl command available, Link the subl binary in the application to a location in the $PATH environment variable:

Open up your terminal and run:

For sublime text 2:

{% highlight console %}
sudo ln -s /Applications/Sublime\ Text\ 2.app/Contents/SharedSupport/bin/subl /usr/bin/subl
{% endhighlight %}

For sublime text 3:
{% highlight console %}
ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/sublime
{% endhighlight %}

Once run you should be able to browse to the directory where your files are and run:

{% highlight console %}
subl .
{% endhighlight %}