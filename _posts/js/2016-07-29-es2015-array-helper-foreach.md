---
category: js
---

ES2016 has introduced a number of Array helpers. Lets take a look at the forEach method and see how it could help us.

Typically when we have an array and we need to perform some action on each item we would typically reach for the trusted for loop, there is nothing inherently wrong with the for loop but it does add a little baggage when being used such as the counter variable, the code length and it's quite easy to miss a part or introduce typos.

The forEach method gives us a little simpler option and removed the need for any extraneous variables.

Let's take a look, we will create an array of numbers and use forEach to sum the numbers;

{% highlight javascript %}
const numbers = [1, 2, 3, 4];
var sum = 0;
numbers.forEach(function(number) {
  sum += number;
});
console.log(sum) //10
{% endhighlight %}

so we call the forEach method of the numbers array we created and pass in an anonymous function with a parameter, for each item in the array the function is called passing in an array item as the parameter.

I hope you agree, this is quite straightforward, shorter code and easier to read.

Stay tuned for more!
