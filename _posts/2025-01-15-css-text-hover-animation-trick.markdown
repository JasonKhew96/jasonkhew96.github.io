---
layout: single
title: "CSS text hover animation trick"
date: 2025-01-15 22:04:48 +0800
categories: css
---
Today, I found an interesting CSS animation at [『天久鷹央の推理カルテ』TVアニメ公式サイト][atdk-a] drawer menu, which animate letter by letter when hovering the words.

<video src="/assets/video/2025-01-15-css-text-hover-animation-trick.mp4" autoplay loop controls></video>

{% highlight html %}
<a href="#introduction" class="l-nav__link">
  <span class="l-nav__link-txt">
    <span class="u-color-red">I</span>
    <span>N</span>
    <span>T</span>
    <span>R</span>
    <span>O</span>
    <span>D</span>
    <span>U</span>
    <span>C</span>
    <span>T</span>
    <span>I</span>
    <span>O</span>
    <span>N</span>
  </span>
</a>
{% endhighlight %}

{% highlight css %}
.l-nav__link-txt span {
  display: inline-block;
  vertical-align: baseline;
  transition: transform 0.6s cubic-bezier(0.25, 1, 0.5, 1);
}
.l-nav__link-txt span:nth-child(1) {
  transition-delay: 0s;
}
.l-nav__link-txt span:nth-child(2) {
  transition-delay: 0.05s;
}
/* ... */
.l-nav__link-txt span:nth-child(19) {
  transition-delay: 0.9s;
}
.l-nav__link-txt span:nth-child(20) {
  transition-delay: 0.95s;
}
@media (hover: hover) {
  .l-nav__link:hover .l-nav__link-txt span {
    transform: rotateY(360deg);
  }
}
{% endhighlight %}

Well, it turns out, they hardcoding `:nth-child` in CSS because CSS does not support getting the index from variable.

So, I modify and recreate it with `calc()` function support which is based on [A nth-child CSS trick][a-nth-child-css-trick] by [Kevin Pennekamp][kevin-pennekamp]

<style type="text/css">
:nth-child(1) {
    --index: 1;
}
:nth-child(2) {
    --index: 2;
}
:nth-child(3) {
    --index: 3;
}
:nth-child(4) {
    --index: 4;
}
:nth-child(5) {
    --index: 5;
}
:nth-child(6) {
    --index: 6;
}
:nth-child(7) {
    --index: 7;
}
:nth-child(8) {
    --index: 8;
}
:nth-child(9) {
    --index: 9;
}
:nth-child(10) {
    --index: 10;
}
:nth-child(11) {
    --index: 11;
}
:nth-child(12) {
    --index: 12;
}

span.text > span:nth-child(1) {
    color: red;
}
span.text > span {
    font-size: 25px;
    letter-spacing: 0.12rem;
    display: inline-block;
    transition: transform 0.6s cubic-bezier(0.25, 1, 0.5, 1);
    transition-delay: calc(0.05s * (var(--index) - 1));
}
span.text:hover > span {
    transform: rotateY(360deg);
}

</style>
<span class="text"><span>I</span><span>N</span><span>T</span><span>R</span><span>O</span><span>D</span><span>U</span><span>C</span><span>T</span><span>I</span><span>O</span><span>N</span></span>

{% highlight css %}
:nth-child(1) {
    --index: 1;
}
:nth-child(2) {
    --index: 2;
}
/* ... */
:nth-child(11) {
    --index: 11;
}
:nth-child(12) {
    --index: 12;
}

span.text > span {
    display: inline-block;
    transition: transform 0.6s cubic-bezier(0.25, 1, 0.5, 1);
    transition-delay: calc(0.05s * (var(--index) - 1));
}
span.text:hover > span {
    transform: rotateY(360deg);
}
{% endhighlight %}

[atdk-a]:                https://atdk-a.com/
[a-nth-child-css-trick]: https://crinkles.dev/writing/a-nth-child-css-trick/
[kevin-pennekamp]:       https://github.com/vycke
