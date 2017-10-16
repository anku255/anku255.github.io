---
layout: post
title: "Understanding wrapping and ordering in Flexbox"
date: 2017-10-16
---

<p class="intro"><span class="dropcap">I</span>n my last post I explained flex-direction. In this post I will be explaining <code>flexbox-wrap</code> and <code>order</code>.</p>

### flex-wrap

By default the flex items will shrink if there is not enough room in container instead of moving to the next row. This happens because `flex-wrap` is set to `nowrap` by default and it stops flex items from wrapping.

To understand how `flex-wrap` works, I am going to use the code below:

```html
<div class="container">
    <div class="box box1">1</div>
    <div class="box box2">2</div>
    <div class="box box3">3</div>
    <div class="box box4">4</div>
    <div class="box box5">5</div>
    <div class="box box6">6</div>
    <div class="box box7">7</div>
    <div class="box box8">8</div>
  </div>
```

```css
.container {
 display: flex;
 border: 10px solid #000000;
}

.box {
  width: 33.333%
}
```

One box will take up 33.333% width of the container. So, only 3 boxes should be present in first row. But if you check the output it looks like below:

<figure>
	<img src="{{ '/assets/img/posts/flex-wrap-nowrap.png' | prepend: site.baseurl }}" alt="position of boxes for default flex-wrap"> 
	<figcaption>flex-wrap: nowrap | default</figcaption>
</figure>   


We can see that the boxes are shrinking themselves and staying in the first row. To change that we need to change `flex-direction` to `wrap`. Then, the output would look something like below:

<figure>
  <img src="{{ '/assets/img/posts/flex-wrap-wrap.png' | prepend: site.baseurl }}" alt="position of boxes for wrap flex-wrap">
  <figcaption> flex-wrap: wrap </figcaption>
</figure>

Now, we get the expected result. There is one more value for `flex-wrap` which is `wrap-reverse`. As expected, it reverses the flex items as seen in the output below:

<figure>
<img src="{{ '/assets/img/posts/flex-wrap-wrap-reverse.png' | prepend: site.baseurl }}" alt="position of boxes for wrap-reverse, flex-wrap">
<figcaption>flex-wrap: wrap-reverse</figcaption>
</figure>


### order

In Flexbox, we can change the order or precendence of individual flex items by applying the Flexbox property `order`. By default all flex items have `order` set to `0`. If we set `order` of one box (say box 3) to `1` then it will appear after all the flex items which have order less than `1`.
Let's look an example here:

```css
.box3 {
  order: 1;
}
```

<figure>
<img src="{{ '/assets/img/posts/order-1.png' | prepend: site.baseurl }}" alt="position of box 3 after setting it's order to 1">
<figcaption>order: 1</figcaption>
</figure>

All the boxes except box 3 have `order 0` so they appear before box 3. Similarly, if we change the order of box 5 to `-1` then it will appear before all the boxes as seen below: 

```css
.box5 {
  order: -1;
}
```

<figure>
<img src="{{ '/assets/img/posts/order-2.png' | prepend: site.baseurl }}" alt="position of box 5 after setting it's order to -1">
<figcaption>order: -1</figcaption>
</figure>

Order of flex items is a relative concept. The order of a flex item will depend upon the order of other flex items. For an example if you set the order of box 3 to 100, even then it does not imply that box 3 will appear last in this list. Box 3 will appear last on the list if and only if other boxes have order less than 100.

Once again, I would like to remind that I am taking a free Flexbox course <a href="https://flexbox.io" target="_blank" >What The Flex Box </a> by Wes Bos. It is a great course and you should check it out if you want to learn Flexbox.