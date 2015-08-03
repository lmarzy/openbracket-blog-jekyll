---
category: js
---

As I did a post on working with strings in Javascript, I though it only fair to do a post on working with numbers. Enjoy!

Here what's up.

- Rounding numbers
- Generating random numbers
- Converting strings to integers and decimals
- Convert strings to numbers, numbers to strings
- Controlling the length of decimals

As you may be aware numbers and considered primitive types, but the same applies to numbers as strings. They can also be considered objects due to the useful methods we can use with numbers. Again you don’t need to concern yourself with this just know Javascript takes care of this for you. Thank you very much Javascript.

##Rounding Numbers

So you have a number that needs rounding to the nearest integer. Simple, just use Math.round() of course.

Math.round() takes a number and rounds to the nearest integer.

{% highlight javascript %}
var x = "3.4"
Math.round(x); // Yields 3
{% endhighlight %}

{% highlight javascript %}
var x = "3.5"
Math.round(x); // Yields 4
{% endhighlight %}

Simple right!

Things to note:

- Math. is how all math functions begin. The "M" must be a capital letter
- Just like Math class, the function rounds up when the decimal is .5 and down below .4
- You can enclose a literal number in the parentheses and not just a variable e.g. Math.round(3.1)
- You can however force Javascript to round up or down to the nearest integer:

{% highlight javascript %}
var x = "3.4"
Math.floor(x); // Yields 3
{% endhighlight %}

{% highlight javascript %}
var x = "3.4"
Math.ceil(x); // Yields 4
{% endhighlight %}

Just remember, floor to go down and ceil for ceiling to go up. Simple!

##Generating random numbers

Generating random numbers is a useful tool to have, luckily Javascript gives us this ability with another useful method, Math.random().

{% highlight javascript %}
var x = Math.random();
{% endhighlight %}

The above will generate a random number. Well technically it will generate a pseudo-random number. Javascript will generate a pseudo-random number with 16 decimal places ranging from:

{% highlight javascript %}
0.0000000000000000 through 0.9999999999999999
{% endhighlight %}

The value returned may not be that useful as most of the time we will want to work with whole numbers, we could convert the decimal to an integer by multiplying by one hundred quadrillion(1 followed by 17 zeros).

{% highlight javascript %}
0.0000000000000000 * 100000000000000000 = 0
{% endhighlight %}

Trillions of possible numbers are not likely what we will want. So to generate a more useable number such as a random number between 1 and 10 we firstly multiply our giant decimal by 10.

{% highlight javascript %}
0.0000000000000000 * 10 = 7.845848485689415
{% endhighlight %}

Excellent, we now have a number we could just round down, however this will not quite work mathematically. Nothing rounds up to 0 and nothing rounds down to 10. The trick is to add 1 to the number and then round.

{% highlight javascript %}
0.0000000000000000 * 10 + 1 = 8.845848485689416
{% endhighlight %}

So to generate a useable random number following the following:

{% highlight javascript %}
var randomNumber = Math.floor(Math.random() * 6) + 1;
{% endhighlight %}

##Converting strings to numbers(integers & decimals)

Sometimes you need to convert strings into it's numerical equivalent to enable you to perform math related tasks. Javascript gives you this ability with parseInt & parseFloat.

###parseInt
parseInt converts the string to a number even floating-point numbers will be converted but the decimals will be removed.

{% highlight javascript %}
var myInt = parseInt(10.99); // Yields 10
{% endhighlight %}

parseFloat
parseFloat will convert the string to a number but keep the decimals.

{% highlight javascript %}
var myDecimal = parseFloat(10.99); // Yields 10.99
{% endhighlight %}

##Converting strings to numbers, numbers to strings

As you saw above you can convert strings to both integers and decimals using parseInt and parseFloat. There is however another way to convert strings to numbers that does not distinguish between integers and decimals. This is conveniently called Number(note the capital N).

{% highlight javascript %}
var myNumber = Number(10.99); // Yields 10.99
{% endhighlight %}

You can also convert numbers to strings, this my be handy if you need to present a large number to a user but you want to format it with commas to make it more readable.

{% highlight javascript %}
var myNumberAsString = 10.99.toString(); // Yields "10.99"
{% endhighlight %}

##Controlling the length of decimals

When doing math in Javascript with numbers you may want to control the length of the decimal returned, this is especially helpful when working with numbers.

{% highlight javascript %}
var price = 9.99;
var vat = 17.5%;
var total = price + ((price / 100) * vat); // Yields 11.73825
{% endhighlight %}

Hardly a price we can give to the customer. so to turn this into a price value we can use toFixed.

{% highlight javascript %}
var usableTotal = total.toFixed(2); // Yields 11.74
{% endhighlight %}

As you can see toFixed also rounds the value based on where the decimal falls but be warned this is not always the case and can sometimes round down depending on the browser!