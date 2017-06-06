---
category: css
---

I have been putting off looking into the new CSS grid, mainly due to the projects I was working on needing older browser support and me being a little idle, but as CSS grid is now available in most modern browsers I decided it was time to take a peek.

As with anything I want to learn, I find the hands on approach much better, I therefore decided to see if I could create a typical grid system. You know the thing that we have enough of to enable us to use a new one on a daily basis for our entire career. That being said I have typically always used my own grid system using our good friend 'float' so though it would makes sense to see if I could bring this up to date.

So what is this CSS grid. Well according the docs or something I may have read it's the most powerful layout system available in CSS. Wow, sounds pretty intimidating! The long and short of it is that we have been waiting a long time for CSS to give us a proper way to layout our sites and now I think we might just have it.  
CSS grid is a two dimensional layout system which works by applying rules to both a parent(the grid container) and the children(the grid items).  

Let's have a look at setting up a simple grid using plain old css, lets create a simple 2 column layout.


{% highlight html %}
<div class="grid">
  <div class="half">Item one</div>
  <div class="half">Item two</div>
</div>
{% endhighlight %}

So from the above we have a container(.grid) and 2 child elements that we want to be positioned side by side.
Let's look at the '.grid' class first:

{% highlight css %}
.grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-gap: 20px;
}
{% endhighlight %}

We first set the display to 'grid'. To set the amount of columns we want, we use the repeat keyword passing in 12 as the columns and the amount we want each column to span we used 1fr meaning 1 fraction so the columns evenly space out. Lastly we set the 'grid-gap' to 20 px, this will give a gap of 20px between each column. No more negative margins or having to target the last column to remove the space at the end, happy times.

Now we'll look at the '.half' classes:

{% highlight css %}
.half {
  grid-column: span 6;
}
{% endhighlight %}

Pretty simple right, I'm telling the element to span 6 columns, as we set the parent to give us 12 columns this element now spans 6 of those giving us a 2 column layout.

As you can see this is actually really simple to create a grid system using CSS grid, once you have the parent set, all you have to do is create all the classes for each column width you need based on the number of columns you set on the parent. So for example in the above we set 'grid-template-columns' to 12, we now need a child class for each of the 12 columns(1 through 12).

{% highlight css %}
.span1 {
  grid-column: span 1;
}
.span2 {
  grid-column: span 2;
}
All the way up to:
.span12 {
  grid-column: span 12;
}
{% endhighlight %}

This is all well and good but who creates non responsive sites anymore and uses plain old css for that matter, Let's look at one way we could tackle this with my favorite preprocessor Sass.

To get this to work in a much more automated way I used a combination of variables, loops and some mixins.

So for this grid system as with the many out there I wanted to be able to add multiple classes to the layout element telling it how much width to occupy based on the breakpoint.

Let't take the above example and update it as follows:

{% highlight html %}
<div class="grid">
  <div class="span12 span6@bp10">Item one</div>
  <div class="span12 span6@bp10">Item two</div>
</div>
{% endhighlight %}

Not too much different from above, we have the parent '.grid' class and the children, this time with 2 classes on which is basically saying at the default width before any breakpoint kicks in span the full 12 columns and when at breakpoint 10 span 6 columns.

Lets first create our variables that we will need.

The first one I created was actually a Sass map to store all my breakpoints, this gives us the ability to loop over the values.

{% highlight css %}
$breakpoints: (
  10: 400px,
  20: 800px
);
{% endhighlight %}

Note: As you can see my breakpoints are names '10', '20' etc. I don’t use typical names for my breakpoints such as small, medium, large etc as I want greater flexibility over these and believe breakpoints should be created based on the content, I therefore use 10, 20 etc as my breakpoint names, this then allows me some flexibility, if I create my first breakpoint which would be 10 and then later in the build I need a breakpoint that is a little smaller I then have another 9 to play with(1 to 9).

Next I created a variable to store the number of columns we want for our grid, as stated above we will stick with 12 for this but as you will see having this variable makes it easy to create whatever you want.

{% highlight css %}
$grid-columns: 12;
{% endhighlight %}

The last variable I created is really an optional one, I just like having my classes with an @ symbol such as @bp10, I think it makes it highly readable what the class is responsible for.

{% highlight css %}
$at: \@;
{% endhighlight %}

Now we have our variables, let's look at the mixins I used.

The first mixin is used to return the media query based on passing in a value from the Sass map.

{% highlight css %}
@mixin bp($breakpoint) {
  @media (min-width: map-get($breakpoints, $breakpoint)) {
    @content;
  }
}
{% endhighlight %}

This is used as follows:

{% highlight css %}
@include bp(10) {
...
}
{% endhighlight %}

Which produces:

{% highlight css %}
@media (min-width: 400px) {
...
}
{% endhighlight %}

Now the final mixin I created was to create all the necessary classes for each column width.

{% highlight css %}
@mixin grid-widths($atbp: "") {
  @for $i from 1 through $grid-columns {
    .span#{$i}#{$atbp} {
      grid-column: span $i;
    }
  }
}
{% endhighlight %}

This is used as follows:

{% highlight css %}
@include grid-widths; or
@include grid-widths($at + bp10);
{% endhighlight %}

As you can see this mixin will generate us our CSS grid class names using a 'for' loop, this loop goes from 1 through to the number of 'grid-columns' specified in the variable, in our case 12.  

Right, we now have our variables and mixins, let's see how we can use this.

First I will call the 'grid-widths' mixin and pass no parameter:

{% highlight css %}
@include grid-widths();
{% endhighlight %}

This will give us the following classes:

{% highlight css %}
.span1 {
  grid-column: span 1;
}
.span2 {
  grid-column: span 2;
}
All the way up to:
.span12 {
  grid-column: span 12;
}
{% endhighlight %}

Now we need to create each of the above classes but when inside each breakpoint:

{% highlight css %}
@each $bp, $query in $breakpoints {
  @include bp($bp) {
    @include grid-widths($at + "bp" + $bp);
  }
}
{% endhighlight %}

We firstly loop through each breakpoint with an '@each' loop, for each turn in the loop we then call the mixin 'bp' which contains the final mixin 'grid-widths' but this time passing in the parameter. This now gives us:

{% highlight css %}
@media (min-width: 400px) {
  .span1\@bp10 {
    grid-column: span 1;
  }
  .span2\@bp10 {
    grid-column: span 2;
 }
Etc, etc...
 .span12\@bp10 {
    grid-column: span 12;
 }
}
@media (min-width: 800px) {
  .span1\@bp20 {
    grid-column: span 1;
  }
  .span2\@bp20 {
    grid-column: span 2;
 }
Etc, etc...
 .span12\@bp20 {
    grid-column: span 12;
 }
}
{% endhighlight %}

Now all we have to do is decorate out HTML with the required classes, so if we wanted a column to be full width at defaut(before any breakpoint) and then half at the first breakpoint(10) and finally a third at the last breakpoint(20) we would do the following:

{% highlight css %}
<div class="span12 span6@bp10 span4@bp20></div>
{% endhighlight %}

This is now a little more involved but as you can see with a little help form Sass we now have a fully functioning grid system that works across all breakpoints.

I hope this has given you an insight into some of the workings of CSS grid. As you can appreciate CSS grid gives us a lot of power and multiple ways of handling layout. Please take a look at the spec and see what it's fully capable of.

Have fun!
