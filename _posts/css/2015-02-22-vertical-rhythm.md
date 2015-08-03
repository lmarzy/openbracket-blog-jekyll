---
category: css
---

There is a lot of talk about vertical rhythm in web design and whether it’s actually needed or or not.

I believe vertical rhythm is a good thing, it forces me to think about the visual experience the users of the site will have giving familiarity and removing visual barriers making the content easier and more readable.

So, what is vertical rhythm. From a non technical point it’s…

> a strong, regular, repeated pattern of movement or sound

So in web design it really boils down to giving your site a structure that guides the reader through the content. Vertical rhythm gives balance to a layout making content easier to read.

Creating good vertical rhythm can be a challenge and comes with practice, understanding the theory and unfortunately for some, Math.

The key to good vertical rhythm is line height. To determine your line heigh the best place to start is with the font size. I tend to set my root font size to 100% to not force the user to use a particular font size. now 100% usually = 16px in most browsers so this is what my base font size will be

Base font size = 16px - check!

Typically line heights are set between 1.4 to 1.6 times your font size. I go for the in-between value and set mine to 1.5. you can use values for line height such as em,rem px etc but I stick with a unitless value of 1.5. This makes my base line height 24px (16 x 1.5).

Base line-height = 1.5 - check!

Lastly is the spacing between elements, typically browsers tend to set a top and bottom margins of 1em meaning the rhythm would be thrown out. The spacing should match your line height.

margin-bottom = 1.5rem - check!

I would set the above setting on the root element i.e. the html element. As I use Sass I would have something like this.

{% highlight css %}
$font--size: 16px;
$font--lineHeight: 24px;

html {
  font-size: 100%;
  line-height: $font--lineHeight / $font--size;
}
{% endhighlight %}

By setting the base font size on the root element I can define additional font sizes in Rems allowing the site to scale proportionally.

Images in your design can be problematic for keeping good vertical rhythm so I make sure image heights match up to multiples of our magic number. This works for the heigh as well as the margin meaning you could have an image that is 96px tall (24 x 4 = 96) with a 24px margin bottom. you could also have an image that is 108px tall with a 12px margin bottom. As long as the Math always adds up to multiples of the magic number(24px) your good to go.

So you may be thinking this all sounds great but I don’t just stick with one font size in my sites so how does this work when the font size changes. I would respond with good question and i’m glad you asked…

I have created a mixin that I use to help me out with vertical rhyhm:

{% highlight css %}
@mixin vr($size, $multiplier: 1, $margin-bottom: null) {

    font-size: ($size / $font--size) * 1rem;
    line-height: ceil($size / $font--lineHeight) * (($font--lineHeight * $multiplier)  / $size);

    @if ($margin-bottom != null) {
      margin-bottom: $spacing * $margin-bottom;
    }

}
{% endhighlight %}

So for example if I wanted a font size of 32px I would use the following:


{% highlight css %}
.double { @include vr(32px); }
{% endhighlight %}

giving the following css:

{% highlight css %}
.double {
  font-size: 2rem; // 32 / 16 = 2
  line-height: 1.5; // (ceil(32 / 24) = 2) 2 * 1.5 = 3 - Remember ceil rounds up
}
{% endhighlight %}

Now say I wanted a font size of 40px but double line height and double margin bottom

{% highlight css %}
.crazy(40px, 2, 2)
{% endhighlight %}

The above would give the following css:

{% highlight css %}
.crazy {
  font-size: 2.5rem; // 40 / 16 = 2.5
  line-height: 2.4; // 40 / 24 = 1.66 (rounds to 2 (remember ceil rounds up)) *  (24 * 2 = 48) / 40) = 1.2 so 2 x 1.2 = 2.4
  margin-bottom: 3rem;  // 1.5 * 2 = 3
}
{% endhighlight %}

I hope the above makes sense and I hope I have my Math right. As you can see Sass plays a pivotal role in creating our vertical rhythm and without it would be hard work.

To help me visualise this while in development I also use baseline grid tool from basehold.it. This can be include as a separate css file or added as a background. Once added a vertical grid will be shown on screen based on your settings. I find this really helpful and I can instantly see if I have any issues.

So there you have it, I hope vertical rhythem now makes a little more sense and you may even give it a go in your next project if your not already doing so!