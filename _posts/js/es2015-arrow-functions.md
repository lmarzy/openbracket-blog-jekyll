---
category: js
---

Arrow functions in ES2015 are anonymous functions that provide a neater way of writing functions, they allow a little shorter syntax when compared to function expressions and lexically bind the 'this' value.

Lets take a look:

Below is a regular function that we are all used to:

{% highlight javascript %}
var greet = function(message, name) {
  return message + ' ' + name;
}
{% endhighlight %}

Lets re-write this as an arrow function;

{% highlight javascript %}
var greet = (message, name) => {
  return message + ' ' + name;
}
{% endhighlight %}

As you can see the difference here is quite subtle, we have removed the funciton keyword and added in the =>. We can actually make this much smaller though.

{% highlight javascript %}
var greet = (message, name) => message + ' ' + name;
{% endhighlight %}

As you can see this is a much shorter syntax as we no longer need the function or return keywords, if you only have one parameter you can also remove the brackets as such:

{% highlight javascript %}
var greet = message => message;
{% endhighlight %}

So what about 'this'?

Lets look at a typical example:

{% highlight javascript %}
var superObj = {
  name: "super",

  showMessage: function(message, fn) {
    fn(message);
  },

  get: function() {
    var self = this;

    this.showMessage('Hi', function(message) {
        console.log(message + ' ' + self.name);
    });
  }
};
{% endhighlight %}

As you can see in the get function we have to create a variable to reference the name property as the function we pass into showMessage does not have access to the name property when it's invoked as it's out of scope.

Arrow functions actually remedy this issue, lets see:

{% highlight javascript %}
var superObj = {
  name: "super",

  showMessage: function(message, fn) {
    fn(message);
  },

  get: function() {
    this.showMessage('Hi', message => console.log(message + ' ' + this.name));
  }
};
{% endhighlight %}

By using arrow functions we now correctly have access to the parent scope and therefore access to the name property.
