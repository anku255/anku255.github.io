---
layout: post
title: What is the use of align-content in Flexbox
date: 2017-10-27
---

<p class="intro"><span class="dropcap">I</span> have talked about <code>justify-content</code>, <code>align-items</code> and <code>align-content</code> to align flex-items. All of them are a property of container and applies for every flex-item inside the container. <code>align-self</code> comes into play when we want to align only one flex-item at a time.</p>

I am going to use below code sample to explain the working of `align-self`.

```html
<div class="container">
    <div class="box box1">1</div>
    <div class="box box2">2</div>
    <div class="box box3">3</div>
    <div class="box box4">4</div>
    <div class="box box5">5</div>
    <div class="box box6">6</div>
</div>
```

```css
.box {
  color:white;
  font-size: 100px;
  text-align: center;
  text-shadow:4px 4px 0 rgba(0,0,0,0.1);
  padding:10px;
}

/* Colours for each box */
.box1 { background:#1abc9c;}
.box2 { background:#3498db;}
.box3 { background:#9b59b6;}
.box4 { background:#34495e;}
.box5 { background:#f1c40f;}
.box6 { background:#e67e22;}

.container {
 display: flex;
 border: 10px solid #000000;
 align-items: flex-start;
 height: 100vh; 
}

.box2 {
  padding-bottom: 200px;
}

.box5 {
  padding-top: 250px;
}

.box2 {
  align-self: center;
}
```

<figure>
  <img src="{{ '/assets/img/posts/align-self.png' | prepend: site.baseurl }}">
  <figcaption>Output for starter code</figcaption>
</figure>

`align-self` is basically `align-item` which works for single flex-item. I have already discussed `align-item` <a href="https://anku255.github.io/blog/align-items/">here</a>. `align-self`, aligns the particular flex-item with respect to the cross-axis. The possile values for `align-self` are `flex-start`, `flex-end`, `center`, `stretch` and `baseline`. I am going to apply `align-self` on box 5. All the outputs are given below:

```css
.box5 {
  align-self: flex-start;
}
```

<figure>
  <img src="{{ '/assets/img/posts/align-self.png' | prepend: site.baseurl }}">
  <figcaption>align-self: flex-start</figcaption>
</figure>

```css
.box5 {
  align-self: flex-end;
}
```

<figure>
  <img src="{{ '/assets/img/posts/align-self-flex-end.png' | prepend: site.baseurl }}">
  <figcaption>align-self: flex-end</figcaption>
</figure>

```css
.box5 {
  align-self: center;
}
```
<figure>
  <img src="{{ '/assets/img/posts/align-self-center.png' | prepend: site.baseurl }}">
  <figcaption>align-self: center</figcaption>
</figure>

```css
.box5 {
  align-self: stretch;
}
```

<figure>
  <img src="{{ '/assets/img/posts/align-self-stretch.png' | prepend: site.baseurl }}">
  <figcaption>align-self: stretch</figcaption>
</figure>

`align-self: baseline`, is supposed to align the flex-item according to the baselines of all other flex-items whose `align-self` is also set to `baseline`. So, we must need to set this property to at least two flex items to see the effect.

```css
.box5 {
  align-self: baseline;
}

.box2 {
  align-self: baseline;
}
```

<figure>
  <img src="{{ '/assets/img/posts/align-self-baseline.png' | prepend: site.baseurl }}">
  <figcaption>align-self: baseline</figcaption>
</figure>

This is all about `align-self` in Fexbox. I am taking a Flexbox course <a href="https://flexbox.io" target="_blank" >What The Flex Box </a> by Wes Bos. It is a great course. Be sure to check it out if you want to learn Flexbox in depth.


