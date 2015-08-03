---
category: css
---

Although these units have been around for a while now, they have not gained a wide spread adoption. I have not used them with great extent but recently I needed to create a site with a background image that spanned with full width and heigh of the browser window. Using VH was the perfect solution.

The VH unit stands for viewport height and VW for viewport width, there is also VMIN VMAX which represents whichever of VH or VW is the shortest length or largest length respectively.

So I hear you say, enough waffle, how does it work?

1vh represents 1% of the current viewport height and 1vw represents 1% of the current viewport width(the content area of the browser window).

So if you want an element to be 100% height or 100% width set the values to either 100vh or 100vw respectively.

These units are also dynamic, meaning if you resize the browser window, the computed values will also change. If the browser window is 1000px wide and you have an element set to 50vw, the value woudl be 500px, if you then shrunk the browser window to 100px wide the value would then be 50px.

<!-- View the example -->

These units can also be used for font-sizing, allowing the text to grow or shrink based on the size of the viewport

So if the browser is 1000px wide and you set the font size to 10vw the font size will be 100px

<!-- View the example (change botht the browser width and heigh to see the font sizes change) -->

Browser support is fairly good

- IE10 — full support
- IE9 — supported, but vmin is named “vm”
- Chrome 22+ — full support
- Safari 6 and iOS Safari 6 — full support
- Firefox — full support
- Blackberry Browser 10 — full support