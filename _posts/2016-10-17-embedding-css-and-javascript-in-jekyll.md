---
layout: post
title: Embedding CSS and JavaScript in Jekyll
summary: "Embedding CSS and JavaScript can make your Jekyll-based site even faster. Here’s how I do it."
---

<figure class="full-width">
  <img src="/img/medium/1*x8Uw4fh2OLtFy6clLh7Uiw.jpeg">
</figure>

# {{ page.title }}

*Update on 3/9/18: Because my site now contains many pages, I no longer use these techniques. If your site is a single page, you should still consider doing this stuff.*

A few weeks ago, I decided to work on speeding up my <a href="https://jekyllrb.com/">Jekyll</a>-generated <a href="http://www.matthewgifford.com/">personal website</a>. It is a single page that acts as a short introduction to me with links to my profiles on other sites. Because most visitors are there for a short time and never return, it doesn’t benefit from browser caching. It seemed obvious that I should reduce the number of HTTP requests by embedding the CSS and JS.

But, how I could accomplish this was not so obvious. I first looked at several asset-handling plugins. None of them did embedding. After a lot of searching, I discovered that Jekyll could do much of what I wanted without plugins, if I thought a little more creatively about how things worked. What Jekyll couldn’t do on its own could be solved by writing a couple small plugins.

## CSS

The key to all this is realizing that you can put <a href="http://markdotto.com/2014/02/28/including-css-in-jekyll/">any kind of file in the _includes directory</a>. When you treat CSS like an include, embedding is easy.

<figure>
  <script src="https://gist.github.com/mattg/822eec0f40aa27f249605162e710ebda.js"></script>
</figure>

But this won’t work if you want to use SCSS or minify the CSS. I needed to find a way to process the include. I found <a href="https://www.sitepoint.com/inline-css-in-jekyll/">a page</a> on how to do this using the capture tag and Jekyll’s scssify filter.

<figure>
  <script src="https://gist.github.com/mattg/cfc5f935b40a26a6667b3033a8d06d91.js"></script>
</figure>

There was one more thing I wanted to do. I use Google Fonts on my site, which requires a request for a CSS file, then requests for the font files. I decided to embed that CSS, too. So, I wrote a [plugin for a tag that will download an external resource](https://github.com/mattg/jekyll-download-tag).

Once you have the plugin set up, including external CSS is simple.

<figure>
  <script src="https://gist.github.com/mattg/4438bceb931d8b9702784df97f10aafd.js"></script>
</figure>

## JavaScript

You can embed JavaScript using the technique described above. But Jekyll doesn’t have a built-in way to minify it. To fix this, I wrote another small [plugin that will allow you to filter text through UglifyJS](https://github.com/mattg/jekyll-uglify-filter).

It works just like scssify does in the above CSS example.

<figure>
  <script src="https://gist.github.com/mattg/d64a2ea697400cc54d28f12c36be80b5.js"></script>
</figure>

***

When I started this little project, I didn’t think to sample how fast the page was loading. So, I can’t tell you how much improvement you should expect to see. I can tell you that it’s ready to read in less than 100ms from my very underpowered server over my cable connection. I’m happy with that.
