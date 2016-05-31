---
category: css
---

In my opinion definition lists are underused on the web, they work in a bunch of situations and provide great semantics. They do however make life a little harder when it comes to styling especially when you want the elements to line up side by side.

By default <dt>s and <dd>s have display block set, meaning we get the elements stacked. In order to turn these into elements that sit side by side we usually fall back to one of the following techniques:

- Floats: not a flexible approach
- Adding &lt;br&gt;s after each <dd> and setting both the <dt> and <dd> as display: inline: this is invalid markup
- Use a different <dl> for each pair: bad as style is dictating markup
- display: run-in on the <dt>: bad browser support

As you can see all the above provide a bit of a hacky solution. We can however insert &lt;br&gt;s through css.

Both CR and LF characters are regular unicode characters that can be inserted anywhere just like any other unicode character. CR's unicode is 00D and LF's unicode is OOA. All this means is that these can be inserted as generated content as long as they are escaped correctly, then we use the appropriate white-space value to make sure the browser respects the line breaks only in that part:

{% highlight css %}
dt, dd { display: inline; }

dd:after {
	content: '\A';
	white-space: pre;
}
{% endhighlight %}

Just a few line's of regular css(no css3 here) and we have achieved what we intended. Some people may argue that this is also not valid as screen readers are expected to voice generated content. You do however have to ask if this really is presentational as the line breaks do provide meaning(well maybe). Anyway I will let you decide if you think this is an acceptable solution.
