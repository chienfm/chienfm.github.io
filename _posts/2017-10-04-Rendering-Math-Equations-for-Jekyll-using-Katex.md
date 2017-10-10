---
title: "Simply Way to Render Math Equations for Jekyll using Katex"
sub_title: "Katex configuration for Jekyll"
categories:
  - Katex
  - Jekyll
  - Math Render
elements:
  - Math Equation
  - css
  - formatting
  - html
  - markup
last_modified_at: 2017-10-04T18:55:59-05:00
---

[KaTeX](https://github.com/Khan/KaTeX) is a very fast, easy-to-use JavaScript library for TeX math rendering on the Jekyll websites. It also supports various browsers including IE, Chrome and Firefox ... Since my current theme does not support the math render in default, I plan to implement Katex. Luckily, it's not so diffucult to do that.

## 1. Employ Katex in theme

You can [download KaTeX](https://github.com/khan/katex/releases) and host it on the sever or you can employ it online. I choose the second way. To do that, I insert the below code in the *head.php* which we can find in <kbd>_include</kbd> folder

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.8.3/katex.min.css" integrity="sha384-B41nY7vEWuDrE9Mr+J2nBL0Liu+nl/rBXTdpQal730oTHdlrlXHzYMOhDU60cwde" crossorigin="anonymous">
<script src="https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.8.3/katex.min.js" integrity="sha384-L9gv4ooDLrYwW0QCM6zY3EKSSPrsuUncpx26+erN0pJX4wv1B1FzVW1SvpcJPx/8" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.8.3/contrib/auto-render.min.js" integrity="sha384-RkgGHBDdR8eyBOoWeZ/vpGg1cOvSAJRflCUDACusAAIVwkwPrOUYykglPeqWakZu" crossorigin="anonymous"></script>
```

>Note: the third script is used to render the math equations automatically.

## 2. Calling render function in your post

We need to call the exposed fuction <kbd> renderMathInElement </kbd> in a **script** tag before your **body** tag in your post. I do it by simply inserting the below script in the *post.html* which is located in <kbd>_layout</kbd> folder.

```html
<script>
      renderMathInElement(
          document.getElementById("your post id"),
          {
              delimiters: [
                  {left: "$$", right: "$$", display: true},
                  {left: "\\[", right: "\\]", display: true},
                  {left: "$", right: "$", display: false},
                  {left: "\\(", right: "\\)", display: false}
              ]
          }
      );
</script>
```
>Note: remember to change "your post id" correctly. More detail can be found in [this page](https://github.com/Khan/KaTeX/blob/master/contrib/auto-render/README.md)

## 3. Test the render function:

1. Inline
    ```
    Test 1: $f(x) = x^2$    # Inline Render

    Test 2: $$f(x) = x^2$$  # New line, center

    Test 3: \\[f(x) = x^2\\] # New line, center

    Test 4: \\(f(x) = x^2\\) # Inline
    ```

Result:

Test 1: $f(x) = x^2$

Test 2: $$f(x) = x^2$$

Test 3: \\[f(x) = x^2\\]

Test 4: \\(f(x) = x^2\\)

OOp! Test 2 does not show anything. But, it's still fine for me ^^!.