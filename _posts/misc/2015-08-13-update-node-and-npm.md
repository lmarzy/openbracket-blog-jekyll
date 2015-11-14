---
category: misc
---

I recently realised I was on an out of date version of Node and NPM and needed to upgrade them. I know I could hop over to the Node website and grab the latest but though there must be an alternative easier option. And low and behold it turns out there sure is, NPM of course!

{% highlight console %}
sudo npm cache clean -f
sudo npm install -g n
sudo n stable
{% endhighlight %}

The 'n' here represents a Node helper, running the last command updates Node to the latest stable version. You can specify the version if you so require.

{% highlight console %}
sudo n 0.12.0
{% endhighlight %}

Once complete, you can run:

{% highlight console %}
node -v
{% endhighlight %}

*Please note that it has been reported that this can mess up module paths, so with any upgrade make a backup first. I personally have never had any issues with this upgrade but be warned!!*

##NPM Update

To just update NPM is a breeze, just run:

{% highlight console %}
sudo npm update -g npm
{% endhighlight %}

Happy upgrades!