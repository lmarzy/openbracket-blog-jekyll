---
category: js
---

Lets now take a look at the array helper 'map'. This is probably one of the most used helpers and you should find a lot of use for it. Let's dive in.

Let say we have an array with numbers and we want to create a new array with each number from the initial array doubled:

{% highlight javascript %}
var nums = [1, 2, 3, 4];
var double = nums.map(function(num) {
  return num * 2;
});
console.log(double); // [2, 4, 6, 8]
{% endhighlight %}

OK, lets break this down.

We first create our nums array which holds our numbers, we then create a new variable which will eventually be our new array. We call the map method on the nums array passing in an anonymous function with a num parameter, this function will then be called for every item in the nums array assigning the doubled value to a new array, you need to make sure the function has a return statement which will assign the value to the new array.

So for the first value in the nums array the function is called with this value being passed in, the function then returns the new value to a new array which we have assigned to the variable double. This will continue for each value until it reaches the end, we then have a brand new array with the values we wanted.

Lets take a look at another example:

We will create a new array but this time the array is an array of objects with multiple properties. We want to create a new array for a particular property in the object.

{% highlight javascript %}
var posts = [
  { title: 'Title-1', desc: 'Description one' },
  { title: 'Title-2', desc: 'Description two' }
];
var titles = posts.map(function(title) {
	return title.title;
});
console.log(prices) // ['10,000', '100,000']
{% endhighlight %}

This is a very common operation and can be seen in use in lot's of client side frameworks, as with the above example it's extremely common to build a UI that is made up of a list of items. As with the above example we might want to show a list of posts and pluck out all the necessary bits of data that the UI needs to display.

There you have it, the array map helper. I hope you find some use for it.
