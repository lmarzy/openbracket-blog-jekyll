---
category: misc
---

When starting a new project I often find I need to replicate one of my starter frameworks. This would typically mean creating the new repo, cloning and copying over all the files from another repo. There is however a better way!

Start by creating your github repo as normal. 

1.Next we need to clone our existing repo, the one we want to duplicate using the –bare flag

{% highlight console %}
git clone --bare https://github.com/exampleuser/existing-repository.git 
{% endhighlight %}

2.Then we do what's called a Mirror-push to the new repository we created.

{% highlight console %}
cd existing-repository.git 
git push --mirror https://github.com/exampleuser/new-repository.git 
{% endhighlight %}

3.Finally you can remove the temporary local repository you created in step 1.

{% highlight console %}
cd .. rm -rf existing-repository.git
{% endhighlight %}

If you project uses a package.json you will also need to update this, running npm init and inputting the repo details should do the trick though.

Hope someone finds this useful.

Have fun!