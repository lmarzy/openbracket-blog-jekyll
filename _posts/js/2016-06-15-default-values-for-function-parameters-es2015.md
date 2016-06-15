---
category: js
---

When working with functions sometimes you want to assign default values to the parameters being used, this would typically involve checking if the parameter has a value and if not assign it a value such as:

{% highlight javascript %}
var greetMessage = function(message) {
  message = message || 'hi';
  return message;
}
{% endhighlight %}

With ES2015 we can now assign default values right where the parameter lives:

{% highlight javascript %}
var greetMessage = function(message = 'Hi') {
  return message;
}
{% endhighlight %}

It still works exactly the same as if multiple parameters exist:

{% highlight javascript %}
var greetMessage = function(name, message = 'Hi') {
  return message + ' ' + name;
}
{% endhighlight %}

From the above we have two parameters, we at least want to message to default to a message if none is passed in, we can still call the function with a name and leave off the message parameter:

{% highlight javascript %}
var greetMessage = function(name, message = 'Hi') {
  return message + ' ' + name;
}
greetMessage('Jimbo'); // Hi Jimbo
{% endhighlight %}

Or we can pass in both parameters and the default message value will be overwritten:

{% highlight javascript %}
var greetMessage = function(name, message = 'Hi') {
  return message + ' ' + name;
}
greetMessage('Jimbo', 'Hello'); // Hello Jimbo
{% endhighlight %}

We can also do the same thing with functions, as crazy as it sounds and potentially looks but let's check it out.

{% highlight javascript %}
function get(done) {
  done();
}
{% endhighlight %}

So we have a function that takes a parameter as a function such as:

{% highlight javascript %}
get(function() {
  console.log('done');
});
{% endhighlight %}

So this works as expected but we can add a function as a default parameter in-case none is passed in:

{% highlight javascript %}
function get(done) {
  done();
}
{% endhighlight %}

So we have a function that takes a parameter as a function such as:

{% highlight javascript %}
function get(done = function() {
    console.log('done');
}){
  done();
}
{% endhighlight %}

Pretty neat eh but also pretty ugly, we can of course tidy this up with the nice and pretty arrow function:

{% highlight javascript %}
function get(done = () => console.log('done')){
  done();
}
{% endhighlight %}

We could go even crazier and get it even shorter, this is not recommended though as it does make the code a little harder to read:

{% highlight javascript %}
let get = (done = () => console.log('done')) => done()
{% endhighlight %}

Have fun!
