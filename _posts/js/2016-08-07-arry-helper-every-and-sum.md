---
category: js
---

Lets take a look at the Array helpers of every and some.

The every Array helper is basically going to return us a Boolean value if every value in the array is true, for the some helper we will get a Boolean value if some of the items return true.

Lets create a new array called people, this array will be an array of objects with a name and an age value:

{% highlight javascript %}
const people = [
  { name: 'Jack', age: 30 },
  { name: 'Jim', age: 28 },
  { name: 'Bob', age: 36 },
  { name: 'Fred', age: 24 },
];
{% endhighlight %}

Ok, lets say we want to check if everyone's age is greater than 30:

{% highlight javascript %}
people.every(function(person) {
  return person.age > 30;
});
// return false
{% endhighlight %}

As you can see this will return false as not everyone's age is greater than 30.

Now lets look at the some:

{% highlight javascript %}
people.some(function(person) {
  return person.age > 30;
});
// return true
{% endhighlight %}

This as expected returns true as some of the people are aged greater then 30.

These helpers are pretty straightforward, you might be thinking sure these are great but I'm not sure I would ever use them. One situation where the every helpers may come in useful is validation.

Typically with forms you need to check the length of required fields to make sure something has been entered.

So you grab the value of the input and check the length which is then stored in an Array:

{% highlight javascript %}
const fields = [username, password];
{% endhighlight %}

Then you want to check that these fields are not empty:

{% highlight javascript %}
const isValid = fields.every(function(field) {
    return field.length > 0;
})
{% endhighlight %}

The further in the code you can check if these fields are greater than 0 then submit the form, if not show the validation error messages.
