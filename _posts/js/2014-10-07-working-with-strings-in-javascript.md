---
category: js
---

I am going to go through some of the basics of working with strings in Javascript, I am going to make an effort to do these more ofter, again for my purpose so I have a reference, but hopefully someone may find it useful too.

- Find length
- Change case
- Slice
- Finding segments
- Finding characters
- Replacing characters

As you know strings in Javascript are considered Primative types but they have a bunch of useful methods. So wait, are strings Primative types or objects?? The answer is both!

Take the following:

{% highlight javascript %}
var x = "string";
typeof x // yields "string"
{% endhighlight %}

Now consider the following:

{% highlight javascript %}
var x = new String('string');
typeof x // yields "object"
{% endhighlight %}

Typically, you don't need to concern yourself about whether you're dealing with a string primitive or a String object because JavaScript automatically converts the primitive to a String object when you call a method.

##Finding the length

You can easily find the length of a string using the folowing:

{% highlight javascript %}
var x = "string"
x.length;
{% endhighlight %}

This will return the length of the string (the above should return 6). Just remember that everything is counted, even spaces.

##Changing case

You can easily change the case wth Javascript to either all upper or all lower, changing case is a great help when you are doing comparisons and need to compare apples to apples as the data you get back from users could have any case type.

{% highlight javascript %}
var x = "STRING"
x.toLowerCase(); // yeilds "string"
{% endhighlight %}

{% highlight javascript %}
var x = "string"
x.toUpperCase(); // yeilds "STRING"
{% endhighlight %}

##Slice (copying sections of a string)

To copy sections of a string you can use the slice method. Say you get a string from the user but you need the first letter to be uppercase, you cant use the toUpperCase method as this will alter the entire string but if you break the string into 2 segments, you can use the slice method to get the results you need.

{% highlight javascript %}
str.slice(beginSlice, endSlice)
{% endhighlight %}

beginSlice

Where to beging the slice(0 based index)

endSlice

Where to end the extraction(0 based index)

So for example if the user has entered a string value of "James" which has been assigned to the variable "name" we can do the following:

{% highlight javascript %}
var firstChar = name.slice(0, 1);
// firstChar will now hold the value of "j"
{% endhighlight %}

Things to note:

- Strings are indexed like arrays, each index number is referring to a character in the string and indexing begins with 0
- In the slice method, the first number inside the parentheses is the index of the first character in the slice, the second number is the first character after the slice
- If you omit the second number in the slice, all the characters from the number to the end of the string are included.

{% highlight javascript %}
var someChars = name.slice(2);
// someChars will now hold the value of "mes"
{% endhighlight %}

##Finding segments

Say you receive some text from a user but you need to replace a word in the text with another word. Javascript comes with a useful utility to acheive this called indexOf

{% highlight javascript %}
var firstChar = text.indexOf("word to find")
{% endhighlight %}

If the text that you pass to indexOf exists, the index is of the first character is returned

{% highlight javascript %}
var text = "Some words to find";
var firstChar = text.indexOf("words"); // returns 5, which is the index of the letter w in word
{% endhighlight %}

If the word does not exitst, the method returns -1 to the variable so you know the word does not exist

Below shows an example of how you could replace a word in a sentence.

{% highlight javascript %}
var text = "Javascript sucks"
var firstChar = text.indexOf("sucks");
if (firstChar !== -1) {
  text = text.slice(0, firstChar) + "Rules" + text.slice(firstChar + 5);
}
{% endhighlight %}

##Finding a character at a location

You already know how to extract characters from a string by using slice, Javascript does however offer a alternative way that is a little more direct.

{% highlight javascript %}
var firstChar = text.charAt(0);
To find the last character of a string:
{% endhighlight %}

{% highlight javascript %}
var lastChar = text.charAt(name.length - 1);
{% endhighlight %}

##Replacing characters

We have already seen how we can replace words using a combinatio of indexOf and slice, but there is a more direct way to do this. You may be thinking why not just write about this method, i'm thinking that too but you now know what the others do if you encounter that code anywhere. So there...

{% highlight javascript %}
str.replace("toFind", "replaceWith");
The above will find the first occurance of "toFind" and replace with "replaceWith".
{% endhighlight %}

If you want to replace all occurances of a word you need to use a global replace as follows:

{% highlight javascript %}
str.replace(/toFind/g, "replaceWith");
{% endhighlight %}

Example:

{% highlight javascript %}
var text = "Javascript sucks";
text = text.replace("sucks", "rules");
{% endhighlight %}

Thanks again, until next time!





