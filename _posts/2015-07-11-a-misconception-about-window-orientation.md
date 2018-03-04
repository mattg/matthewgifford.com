---
layout: post
title: A misconception about window.orientation
summary: "When people think about window.orientation, they probably envision something like the following poorly-done drawing."
---

# {{ page.title }}

When people think about window.orientation, they probably envision something like the following poorly-done drawing.

<figure>
  <img src="/img/medium/0*1xJoWPZLu5SeZ9K7.jpg">
</figure>

0 is the bottom. 90 and -90 are the sides. 180 is the top. Simple concept. But there’s something implied by this drawing that is incorrect. Do you see it? Let’s get some devices out and see if we can discover the error. On each device, we’ll load a <a href="http://www.matthewgifford.com/tests/orientation/">test page</a> I wrote. Then, we will hold them in portrait orientation and see what the page says. We’ll keep turning them 90° counterclockwise and checking the results until we’ve done all 4 sides.

First, an iPod touch.

<figure>
  <img src="/img/medium/0*1XZmOF0WtBlKfqsI.jpg">
</figure>

Apple has decided that you’re not allowed to use your iPod upside down. Other than that, this fits with our mental image.

Next, let’s get out a Nexus S.

<figure>
  <img src="/img/medium/0*ULEOHYX3MhABJNvw.jpg">
</figure>

Google also doesn’t think you should be using your phone upside down. This device is also reporting both sides as 90, which is not very useful if you care about which side is facing down. But it still mostly fits with what we expect.

Let’s try a tablet. This is a Kindle Fire.

<figure>
  <img src="/img/medium/0*uaPtqwZlk6vCfStU.jpg">
</figure>

Good job, Amazon! This fits exactly with our expectations.

Next up is our Toshiba Thrive.

<figure>
  <img src="/img/medium/0*K4A594VALgZYS2LG.jpg">
</figure>

How unexpected! After looking at the results for a minute, you might notice that the numbers have shifted one position to the right. Let’s shift them to the left so they line up with results for the other devices.

<figure>
  <img src="/img/medium/0*YxDpOAGtexSteHC1.jpg">
</figure>

So, on the Thrive, orientation 0 is landscape rather than portrait. Why is this? Is it a bug? A bad interpretation of a spec? No. It’s because this is how someone at Toshiba intends for you to hold the device when using the browser.

This may seem weird to you. It’s certainly not the norm. But it’s not wrong. The problem is that many people assume that 0 means portrait. What 0 *really* means is the default orientation.

Have you run into any other devices where window.orientation 0 is landscape? If you can’t rely on window.orientation to determine if a device is in landscape or portrait, what *do* you use?
