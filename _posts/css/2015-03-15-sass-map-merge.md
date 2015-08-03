---
category: css
---

Maps are a great feature of Sass allowing me to store configuration data and values in an easily accessible way. I was recently working on a site where I was sharing a Sass directory allowing me to have multiple sites based off of the same core css instead of copying and pasting the same code over and over.

This let to some interesting challenges but one challenge I had was having various Sass maps that had some values to be shared but also some values that were specific to one of the sites. I originally just though about storing all the information in one map but though this could get a little messy, I then just though about having multiple maps. This again was messy and as I had some functions that consumed the maps, this meant that I would have to essentially have multiple functions that do the same job. So I did what everyone does and turned to Google, here I came across Sass map merge, this sounded like just the ticket.

This allowed me to set up my shared map and then another map in the specific site and just merge them allowing me to use one function to consume the newly merged map as shown:

{% highlight css %}
$mapOne: (
 key1: value1,
 key2: value2
);

$mapTwo: (
 key3: value3,
 key4: value4
);
{% endhighlight %}

Now the merging needs to happen:

{% highlight css %}
$mergedMaps: map-merge($mapOne, $mapTwo);
{% endhighlight %}

Once the merging has taken place you can use like any other map to get a value:

{% highlight css %}
map-get($mergedMaps, key2); // value2
{% endhighlight %}

Sass map merge, pretty neat eh.

The above is obviously a very generic example and you may wonder if you will ever have a need for this. As stated above this came in really useful due to the fact I was sharing some core css to allow me to have various sites from one core css as all the sites shared common base styles such as typography, forms, buttons etc... as well as configuration and settings information, so lets look at what this really helped me with.

For the sites I work with now I have all my colours stored in maps, this is great for ease of use and allows me to store all this information in a neatly organised way. Below is a simplified version of my shared colours map:

{% highlight css %}
$shades: hsl(0, 0%, 100%); // white

$colours: (
 shades: (
  white : $shades,
  black : hsl(0, 0%, 0%)
 ),
 alerts: (
  info : hsl(200, 65%, 91%)
 ),
 social: (
    facebook : hsl(221, 44%, 41%)
 ),
 techType: (
  html : hsl(31, 97%, 62%)
 )
);
{% endhighlight %}

Now here is the map that is specific to a site:

{% highlight css %}
$pallette: (
 root: (
  bgBody : hsl(60, 2%, 92%),
  textColour : hsl(199, 20%, 37%)
 ),
 links: (
  linkColour : inherit
 ),
 brand: (
  a : hsl(187, 99%, 45%),
 ),
 texture: (
  borderColour : hsl(60, 2%, 92%)
 )
);
{% endhighlight %}

So to use colours I have a function that I pass in a map. This means if I wanted to have separate maps I would need to use two functions, one to consume the shared colours and one for the colours that are specific to a site. Not really what you want as this is not very dry(don't repeat yourself).

Sass map merge to the rescue, I can keep my one function but pass it the newly merged map:

{% highlight css %}
$col: map-merge($colours, $pallette);
{% endhighlight %}

Here I create my new variable to store the merged maps which I can now use in my function:

{% highlight css %}
@function colour($type, $colour) {
 @if not map-has-key($col, $type) {
  @warn "No colour found for `#{$type}` in $colours map. Property omitted.";
 }
 @return map-get(map-get($col, $type), $colour);
}
{% endhighlight %}

This now means to get a colour for a specific site I can just use my new function:

{% highlight css %}
background: colour(brand, a); // background: hsl(187, 99%, 45%);
{% endhighlight %}

Hope this was useful for you and you never know it may come in handy one day.