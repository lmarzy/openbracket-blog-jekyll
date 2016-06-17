---
category: js
---

When adding properties to an object literal you would typically add them as follows:

{% highlight javascript %}
var person = {
  firstName: "Jimbo",
  lastName: "Bob"
}
{% endhighlight %}

You can of course use previously declared variables to give the keys a value:

{% highlight javascript %}
var firstName = "Jimbo";
var lastName = "Bob";

var person = {
  firstName: firstName,
  lastName: firstName
}
{% endhighlight %}

With ES2015 we can shorten this a little, makes sense I guess due to the name of the post. Let's see:

{% highlight javascript %}
var firstName = "Jimbo";
var lastName = "Bob";

var person = {
  firstName,
  lastName
}

console.log(person.firstName); // "Jimbo"
{% endhighlight %}

If the key is the same name as a value that is declared you don't have to declare the value as it's assumed from the key name.

You can also do the same with a function that is declared:

{% highlight javascript %}
var firstName = "Jimbo";
var lastName = "Bob";
function when() {
  console.log('Now');
}

var person = {
  firstName,
  lastName,
  when
}

person.when(); // "Now"
{% endhighlight %}

Adding methods directly into objects has also taken on a shorter form, instead of having to type the method name then colon and function you can omit the colon and function text:

{% highlight javascript %}
var firstName = "Jimbo";
var lastName = "Bob";

var person = {
  firstName,
  lastName,
  when() {
    console.log('Now');
  }
}

person.when(); // "Now"
{% endhighlight %}

Pretty straight forward but typing less is always a good thing :-)
