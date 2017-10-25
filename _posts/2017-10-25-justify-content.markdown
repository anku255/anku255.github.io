---
layout: post
title: What is justify-content in Flexbox
date: 2017-10-25
---

<p class="intro"><span class="dropcap">I</span>n my <a href="https://anku255.github.io/blog/flexbox-wrapping/">last post</a>, I discussed about <code>flexbox-wrap</code> and <code>order</code>. Today, I will be talking about the role of <code>justify-content</code> in Flexbox.</p>


I will be using below code sample to explain `justify-content`. I have 6 divs (flex-items) inside a container div (flex-container).

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
}
```

The above code produces following output:

<figure>
  <img src="{{ '/assets/img/posts/justify-content.png' | prepend: site.baseurl }}">
  <figcaption>Output for starter code</figcaption>
</figure>

`justify-content` defines the alignment of flex-items along the main-axis in a flex-container. It also helps distribute extra free space left over when either all the flex items on a line are inflexible, or are flexible but have reached their maximum size.

The default value for `justify-content` is `flex-start` which aligns the flex-items towards the start of the main axis. If we change the value of `justify-content` to `flex-end` then it will align flex-items towards the end of the main axis as seen below:

<figure>
  <img src="{{ '/assets/img/posts/justify-content-flex-end.png' | prepend: site.baseurl }}">
  <figcaption>justify-content: flex-end</figcaption>
</figure>

Changing `flex-items` to `center` will align all the flex-items to the center of the main axis (see, how easy it is to center in Flexbox) as seen below:

<figure>
  <img src="{{ '/assets/img/posts/justify-content-center.png' | prepend: site.baseurl }}">
  <figcaption>justify-content: center</figcaption>
</figure>

To distribute the extra space among all the flex-items we can set `justify-content` to `space-between`. The first item is on the start of the main axis while the last item is on the end of the main axis as seen below:

<figure>
  <img src="{{ '/assets/img/posts/justify-content-space-between.png' | prepend: site.baseurl }}">
  <figcaption>justify-content: space-between</figcaption>
</figure>

We can see that first and last flex-items don't have the margin on the left and right side respectively. We can fix this by changing `justify-content` to `space-around`.

<figure>
  <img src="{{ '/assets/img/posts/justify-content-space-around.png' | prepend: site.baseurl }}">
  <figcaption>justify-content: space-around</figcaption>
</figure>

Still, the first and last flex items have only one unit margin on their respective left and right side while other flex-items have 2 units margin. To fix this we can set `justify-content` to `space-evenly`. Now, the spacing between any two items (and the space to the edges) is equal as seen below:

<figure>
  <img src="{{ '/assets/img/posts/justify-content-space-evenly.png' | prepend: site.baseurl }}">
  <figcaption>justify-content: space-evenly</figcaption>
</figure>

This is all about `justify-content` in Flexbox. I am learning Flexbox from Wes Bos's course <a href="https://flexbox.io" target="_blank" >What The Flex Box </a>. It is a great free course.





