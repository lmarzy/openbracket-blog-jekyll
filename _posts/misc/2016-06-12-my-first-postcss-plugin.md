---
category: misc
---

PostCss is a fairly new way of writing css, it seems to be getting a lot of attention and for good reason I think. Don't get me wrong I am a big fan of pre-processors such as Sass and Stylus, but PostCss opens up the doors to create a way of working exactly in tune with what you want. Pre-processors give you a lot of functionality which can be a great thing but you may not want or need all of this, with PostCss you can choose what you want and even create your own plugins to do a very specific job which is exactly what I did.

When I started with PostCss I needed to re-create some of the functionality that I got with my pre-processor, one of these was the ability to keep a good vertical rhythm which I did through a function to calculate the line height based on the base font-size and line-height. I did some searching but could not find anything that exactly matched my needs so I decided to create my own.

For this plugin I wanted it to parse my css and find all the font-size declarations and add in the correctly calculated line-height but only for font-sizes that varied from the base size.

I typically always set my base font size to 100% which is typically 16px and I set my line-height to 1.5, this gave me my starting values to calculate the new line-heights when the font-size changed. For this plugin however I enabled the plugin to accept options in the form of the base font-size and line-height.

I have now published this plugin to NPM so you can read more about it there and even download if you think it may be useful.

Check it out [postcss-vr](https://www.npmjs.com/package/postcss-vr)

As always any feedback/bugs please let me know.
