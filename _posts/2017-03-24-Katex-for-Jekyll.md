---
layout: post
title: Katex for Jekyll
description: "Katex for Jekyll"
modified: 2017-03-24
tags: [Katex, Jekyll]
image:
  feature: 
  credit: 
  creditlink: 
---

### 1. Reason

I recently create a github page for writing somethings in my spare time. The most thing I would do involving computational fluid dynamics.I was going to write my first post but suddenly found that my theme did not have a math render. Working around, I find out there are two ways to do that:
- [MathJax](https://www.mathjax.org/): a popular math render. There are some good [blogs](http://haixing-hu.github.io/programming/2013/09/20/how-to-use-mathjax-in-jekyll-generated-github-pages/) show you how to embbed it into github page.
- [Katex](https://github.com/Khan/KaTeX): I actually know it when I use **VScode**. It's pretty faster than Mathjax as proving in [this blog](https://github.com/Khan/KaTeX).So I did embbed it in my page. Here, I show you a simply way to do that since I found no clear instruction. I hope it would help someones with no experence in JS or CSS like me. 

---
### 2. Configure Katex in Github Page

1. First, you should download the [Katex source](https://github.com/khan/katex/releases) and push it intp your root directory of your page. Say, we call the folder is **katex**.

2. Open your `head.html` in your `_include` folder and add the link to katex source. You can add it directly to your `page.html` or `post.html`, depending on your purpose. Here, I call auto render since I want Katex scan all my post and render rather than put **equation** in a block. Mean, you just type `$ equation $` as normal. 

```javascript
<link rel="stylesheet" href="{{ site.url }}/katex/katex.min.css">
<script src="{{ site.url }}/katex/katex.min.js"></script>
<script src="{{ site.url }}/katex/contrib/auto-render.min.js"></script>
```

3. Now, in `_layout` folder, you insert the following code in the lastline before tag `<\body>` of `post.html` or `page.htm`, or whatever page you want to render math equation.

```javascript
<script>
  renderMathInElement(
    document.getElementById("main"),
    {
      delimiters: [
        {left: "$$", right: "$$", display: true},
        {left: "\\[", right: "\\]", display: false},
        {left: "$", right: "$", display: false},
        {left: "\\(", right: "\\)", display: false}
      ]
    }
  );
</script>
```

Note that, `"main"` is the name of the **main content** in my page. You can refer **[this page](https://github.com/Khan/KaTeX/tree/master/contrib/auto-render)** for detail. **Done**

---
### 3. Let's test some math equations

Now we can test some equations.
- A simple equation
```code
\\[\alpha = \beta\\]
```
\\[\alpha = \beta\\]

Inline: $\alpha = \beta$

Test a display math:
\\[
   |\psi_1\rangle = a|0\rangle + b|1\rangle
\\]
Is it O.K.?

Another Test:

\\(
P(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{ - \frac{(x - \mu)^2}{2\sigma ^2}}
\\)                                                                            

---

Finally, now I can type math on my Page with Katex! Hope this trick could also help you!
