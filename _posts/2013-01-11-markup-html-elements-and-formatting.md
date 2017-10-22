---
title: "Markup: HTML Elements and Formatting"
excerpt: "The common elements"
categories:
  - Markdown
tags:
  - content
last_modified_at: 2017-10-04T18:55:59-05:00
---

# ***A variety of common HTML elements to demonstrate the theme's stylesheet and verify they have been styled appropriately.***

## **1. Order of header**
```
# Header one

## Header two

### Header three
```

*And what we see*

># Header one
>## Header two
>### Header three

---

## **2. Blockquotes**

*1. Single line blockquote:*
```
> Stay hungry. Stay foolish.
```

*Result:*

> Stay hungry. Stay foolish.


*2.Multi line blockquote with a cite reference:*
```
> People think focus means saying yes to the thing you've got to focus on. But that's not what it means at all. It means saying no to the hundred other good ideas that there are. You have to pick carefully. I'm actually as proud of the things we haven't done as the things I have done. Innovation is saying no to 1,000 things.

<cite>Steve Jobs</cite> --- Apple Worldwide Developers'Conference, 1997
{: .small}
```

*Results:*

> People think focus means saying yes to the thing you've got to focus on. But that's not what it means at all. It means saying no to the hundred other good ideas that there are. You have to pick carefully. I'm actually as proud of the things we haven't done as the things I have done. Innovation is saying no to 1,000 things.

<cite>Steve Jobs</cite> --- Apple Worldwide Developers' Conference, 1997
{: .small}


## **3. Tables**

```
| Employee         | Salary |                                                              |
| --------         | ------ | ------------------------------------------------------------ |
| [John Doe](#)    | $1     | Because that's all Steve Jobs needed for a salary.           |
| [Jane Doe](#)    | $100K  | For all the blogging she does.                               |
| [Fred Bloggs](#) | $100M  | Pictures are worth a thousand words, right? So Jane × 1,000. |
| [Jane Bloggs](#) | $100B  | With hair like that?! Enough said.                           |

| Header1 | Header2 | Header3 |
|:--------|:-------:|--------:|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|-----------------------------|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|=============================|
| Foot1   | Foot2   | Foot3   |
```

*Results:*

| Employee         | Salary |                                                              |
| --------         | ------ | ------------------------------------------------------------ |
| [John Doe](#)    | $1     | Because that's all Steve Jobs needed for a salary.           |
| [Jane Doe](#)    | $100K  | For all the blogging she does.                               |
| [Fred Bloggs](#) | $100M  | Pictures are worth a thousand words, right? So Jane × 1,000. |
| [Jane Bloggs](#) | $100B  | With hair like that?! Enough said.                           |

| Header1 | Header2 | Header3 |
|:--------|:-------:|--------:|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|-----------------------------|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|=============================|
| Foot1   | Foot2   | Foot3   |

## **4. Definition Lists**

Definition List Title
: Definition list division.

Startup
: A startup company or startup is a company or temporary organization designed to search for a repeatable and scalable business model.

#dowork
: Coined by Rob Dyrdek and his personal body guard Christopher "Big Black" Boykins, "Do Work" works as a self motivator, to motivating your friends.

Do It Live
: I'll let Bill O'Reilly [explain](https://www.youtube.com/watch?v=O_HyZ5aW76c "We'll Do It Live") this one.

## **5. Unordered Lists (Nested)**
```
  * List item one 
      * List item one 
          * List item one
          * List item two
          * List item three
          * List item four
      * List item two
      * List item three
      * List item four
  * List item two
  * List item three
  * List item four
```

*Results:*

  * List item one 
      * List item one 
          * List item one
          * List item two
          * List item three
          * List item four
      * List item two
      * List item three
      * List item four
  * List item two
  * List item three
  * List item four

## **6. Ordered List (Nested)**
```
  1. List item one 
      1. List item one 
          1. List item one
          2. List item two
          3. List item three
          4. List item four
      2. List item two
      3. List item three
      4. List item four
  2. List item two
  3. List item three
  4. List item four
```

*Results:*


  1. List item one 
      1. List item one 
          1. List item one
          2. List item two
          3. List item three
          4. List item four
      2. List item two
      3. List item three
      4. List item four
  2. List item two
  3. List item three
  4. List item four

## **7. Address element**
```
<address>
  1 Infinite Loop<br /> Cupertino, CA 95014<br /> United States
</address>
```

*Result:*

<address>
  1 Infinite Loop<br /> Cupertino, CA 95014<br /> United States
</address>

## **8. Anchor element (aka. Link)**
```
This is an example of a [link](http://apple.com "Apple").
```

*Result:*

This is an example of a [link](http://apple.com "Apple").

## **9. Abbreviation element**

The abbreviation CSS stands for "Cascading Style Sheets".
```
*[CSS]: Cascading Style Sheets
```

*Result:*

*[CSS]: Cascading Style Sheets

## **10. Cite element**
```
"Code is poetry." ---<cite>Automattic</cite>
```

*Result:*

"Code is poetry." ---<cite>Automattic</cite>

## **11. Code element**

You will learn later on in these tests that `word-wrap: break-word;` will be your best friend.

## **12. Strike element**
```
This element will let you <strike>strikeout text</strike>.
```

*Result:*

This element will let you <strike>strikeout text</strike>.

## **13. Emphasize element**

The emphasize element should _italicize_ text.

## **14. Insert element**

This element should denote <ins>inserted</ins> text.

## **15. Keyboard element**
```
This scarcely known element emulates <kbd>keyboard text</kbd>, which is usually styled like the `<code>` element.
```

*Result:*

This scarcely known element emulates <kbd>keyboard text</kbd>, which is usually styled like the `<code>` element.

## **16. Preformatted element**

This element styles large blocks of code.
```
<pre>
.post-title {
	margin: 0 0 5px;
	font-weight: bold;
	font-size: 38px;
	line-height: 1.2;
	and here's a line of some really, really, really, really long text, just to see how the PRE element handles it and to find out how it overflows;
}
</pre>
``` 

*Results:*

<pre>
.post-title {
	margin: 0 0 5px;
	font-weight: bold;
	font-size: 38px;
	line-height: 1.2;
	and here's a line of some really, really, really, really long text, just to see how the PRE element handles it and to find out how it overflows;
}
</pre>

## **17. Quote element**
```
<q>Developers, developers, developers&#8230;</q> &#8211;Steve Ballmer
```

*Result:*

<q>Developers, developers, developers&#8230;</q> &#8211;Steve Ballmer

## **18. Strong element**

This element shows **bold text**.

## **19. Subscript element**
```
Getting our science styling on with H<sub>2</sub>O, which should push the "2" down.
```

*Result:*

Getting our science styling on with H<sub>2</sub>O, which should push the "2" down.

## **20. Superscript element**
```
Still sticking with science and Isaac Newton's E = MC<sup>2</sup>, which should lift the 2 up.
```

*Result:*

Still sticking with science and Isaac Newton's E = MC<sup>2</sup>, which should lift the 2 up.

## **21. Variable element**
```
This allows you to denote <var>variables</var>.
```

*Result:*

This allows you to denote <var>variables</var>.