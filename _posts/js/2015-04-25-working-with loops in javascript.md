---
category: js
---

So, what are loops. Loops are used to execute the same block of code a specified number of times or while a specified condition is true. So basically loops allow you to write one block of code and have it repeated a number of times, this obviously saves a lot of time and typing and to make a change you only have to change the one place.

There are various types of loops in Javascript including: while, do while and for loops. There are others but these are the most used. Lets look at each one in turn.

##While loops

The purpose of a while loop is to execute a code block repeatedly as long as a condition is true, as soon as the condition becomes false the loop will exit. So when would you use a while loop. Typically while loops are best used when you don’t know how many times you need to loop, for example. If you ask a user for a number between 1 and 10, if the user enters a number greater than 10 we ask again, so while the number is not between 1 and 10 we keep asking the same question until the condition is satisfied.

Lets look at the syntax for a while loop

{% highlight javascript %}
while ( condition ) {
  do something
}
{% endhighlight %}

Example:

{% highlight javascript %}
var x = 0;
while (x < 10) {
  console.log(x);
  x++;
} // 0123456789
{% endhighlight %}

##Do while

A do while loop is essentially the same as a while loop except the loop will always run at least once as the condition is checked after the code block is executed for the first time, once the code block is executed the condition is then checked.

Syntax for a do while loop:

{% highlight javascript %}
do {
  do something
}while(condition);
{% endhighlight %}

Example:

{% highlight javascript %}
var x = 0;
do {
  console.log(x);
  x++;
}while(x < 10); // 0123456789
{% endhighlight %}

##For loops

A for loop is typically used when you need to perform an action a certain number of times. Once the number of times has been reached the condition will become false and the loop will exit. For loops consists of the following 3 items:

Initialisation - this is run before the loop starts to initialise any variables
condition - the condition to be satisfied for the loop body to run
incrementor - what is done after each iteration of the loop
Syntax for a for loop:

{% highlight javascript %}
for (initialisation; condition; increment) {
  do something;
}
{% endhighlight %}

Example

{% highlight javascript %}
for (var i = 0; i < 10; i++) {
  console.log(i);
} // 0123456789
{% endhighlight %}

The above is a very typical example of a for loop, it starts with a variable initialised to 0, the condition then checks if that variable is less than 10 and on each loop the initialisation variable is incremented by 1.

For loops have a degree of flexibility, you can set the initialiser variable outside of the for loop as shown:

{% highlight javascript %}
var i = 0;
for (; i < 10; i++) {
  console.log(i);
} // 0123456789
{% endhighlight %}

Just remember to keep in the semi-colon as this is still needed even though there is no variable set inside the parens.

You can also declare multiple variables inside the parens:

{% highlight javascript %}
for (var i = 0, j = 10; i < j; i++) {
  console.log(i);
} // 0123456789
{% endhighlight %}

You will often see for loops associated with Arrays as for loops make it easy to loop over the Array.

{% highlight javascript %}
var myArray = [1, 2, 3, 4, 5, 6, 7, 8, 9];
for (var i = 0; i < myArray.length; i++) {
  console.log(myArray[i]);
} // 0123456789
{% endhighlight %}

So there you have a few examples of the most commonly used loops in JavaScript. Hope you found it useful.





{% highlight javascript %}

{% endhighlight %}