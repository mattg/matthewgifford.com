---
layout: post
title: Why aren’t you using HSL?
summary: "You need to define colors in your CSS. Why not do it in an intuitive way?"
---

# {{ page.title }}

You’re a web designer/developer for a company that has one official color, cornflower blue.

<figure>
  <img src="/img/medium/1*gYfpbIaB6743JV-QotuOhA.png">
</figure>

While working on the new website, you realize that you need a background color for pull-quotes. It needs to be a light color. Something other than light cornflower blue. Maybe you’ll try a desaturated tint of the complement.

Being a big fan of cornflower blue, you have its hexadecimal RGB value memorized: <code>#6495ED</code>.

## Guessing with RGB

If you don’t care much about color, you might just make guesses about the RGB value for your desired color until you get close enough. After a few changes and page reloads, you settle on <code>#EFCFA2</code>.

<figure>
  <img src="/img/medium/1*ALavE6XJ7esfM1yteQk3Rw.png">
  <figcaption>#EFCFA2, left, versus the desired color</figcaption>
</figure>

You could also make guesses using your computer’s color picker. You paste in <code>#6495ED</code> and move the RGB sliders around until you get close.

<figure class="wide">
  <img src="/img/medium/1*S_kKorHlwNKNzNgk9T-zJQ.png">
</figure>

This time you end up with <code>#EFE2BA</code>, which isn’t any better than <code>#EFCFA2</code>.

<figure>
  <img src="/img/medium/1*brpvUuwdCh_fCbQ7pN7gaA.png">
  <figcaption>#EFCFA2, left, versus the desired color</figcaption>
</figure>

## Why is this so hard?

Think about how you talk about a color. Is it red, reddish-orange, or orange? Is it brilliant or faded? Is it light or dark? It’s not easy for most of us to translate these concepts into manipulations of red, green, and blue. For example, if you wish to lighten a color without changing its hue or saturation, you must change all three RGB axes, usually at different rates.

Isn’t there a system that mirrors how we think about color?

## No guessing with HSB

HSB stands for Hue, Saturation, Brightness. This color model was designed to be more intuitive than RGB. You’ll notice that these three axes answer the three questions at the beginning of the previous section.

Let’s get back to our scenario. After pasting in the hex value for cornflower blue, instead of adjusting the RGB sliders, you switch to the HSB sliders. The complement of a color is on the opposite side of the color wheel, so you subtract 180° from the hue. You move the brightness to 100%. Then you slide the saturation to 25%. Switch back to the RGB sliders and you have the correct hex color.

<figure class="wide">
  <img src="/img/medium/1*B9mg4zO1Tr2Zxt6tpxnDQw.png">
</figure>

No guessing needed.

<figure>
  <img src="/img/medium/1*BJrHWMLJV2ZCWBhyu13FHQ.png">
</figure>

This is much better. But we still have to do the manipulations in the color picker to get the RGB hex code. It sure would be nice if we could use an intuitive color model right in the CSS.

## Dumping the color picker

Starting with CSS3, we gained a new option for defining color: HSL (Hue, Saturation, Lightness). While HSL has the same goal as HSB, they work differently. (I don’t find HSL to be as intuitive as HSB. But that’s likely because I haven’t used it as much.)

Returning to our scenario, since you’re new to HSL, you probably don’t know the correct value to write in CSS for cornflower blue. So, you find a <a href="http://colorizer.org/">color picker site</a> and figure out that it’s <code>hsl(219, 79%, 66%)</code>. Now that you have that, the rest is pretty easy. As with HSB, you subtract 180° from the hue. You increase the lightness to around 85%. And, because of how HSL works, you need to bump the saturation to almost 100%. You end up at <code>hsl(39, 97%, 85%)</code>.

<figure>
  <img src="/img/medium/1*BJrHWMLJV2ZCWBhyu13FHQ.png">
</figure>

## Why aren’t we all doing this?

I’m not sure why we’re not all using HSL in CSS. My guess is that we’ve been using RGB hex codes and color pickers for so long that we’re just used to the pain. Another reason might be that people are using CSS preprocessors that have functions for easy color manipulation. Regardless, you need to define colors in your CSS. You might as well do it in an intuitive way.
