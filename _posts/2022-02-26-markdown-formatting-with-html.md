---
title: "Markdown Formatting with HTML"
date: 2022-02-26T18:47:00-06:00
categories:
  - cheat sheet
tags:
  - Markdown
  - HTML
toc_sticky: true
---

Per [Markdown official syntax rule]:

> Markdown’s syntax is intended for one purpose: to be used as a format for writing for the web.
>
> Markdown is not a replacement for HTML, or even close to it. Its syntax is very small, corresponding only to a very small subset of HTML tags. The idea is not to create a syntax that makes it easier to insert HTML tags. In my opinion, HTML tags are already easy to insert. The idea for Markdown is to make it easy to read, write, and edit prose. HTML is a publishing format; Markdown is a writing format. Thus, Markdown’s formatting syntax only addresses issues that can be conveyed in plain text.

With the above quote in mind, minimize your usage of HTML in Markdown documents unless it is the only way to do so. This post briefly discussed a subset of the frequently used HTML formatting syntax. 

[Markdown official syntax rule]: https://daringfireball.net/projects/markdown/syntax#html

## Underlining Text

There is no underlining command in Markdown as the underlining format is reserved to represent links. You may enclose texts with HTML tag `<u>text</u>` to format with underline. The rendered output will look like this:

<u>text</u>

## Coloring

Text coloring is done in the following way. First, enclose the text with the `<span>text</span>` tag. Second, specify the desired color or its associated Hex code in the style attribute. Use website like [HTML Color Codes](https://htmlcolorcodes.com) to find the Hex code of specific color. See below for a few examples.

```html
<!--Predefined Colors-->
<span style="color:white">white</span>
<span style="color:gray">gray</span>
<span style="color:black">black</span>
<span style="color:red">red</span>
<span style="color:green">green</span>
<span style="color:blue">blue</span>
<span style="color:cyan">cyan</span>
<span style="color:magenta">magenta</span>
<span style="color:yellow">yellow</span>
<!--Hex Color Code-->
<span style="color:#FF33AB">hex color code (#FF33AB) </span>
```

The redered output looks like this:

<span style="color:white">white</span>

<span style="color:gray">gray</span>

<span style="color:black">black</span>

<span style="color:red">red</span>

<span style="color:green">green</span>

<span style="color:blue">blue</span>

<span style="color:cyan">cyan</span>

<span style="color:magenta">magenta</span>

<span style="color:yellow">yellow</span>

<span style="color:#FF33AB">hex color code</span>

## Alignment

Text alignment can be done just like text coloring. Use the tag `<div>text</div>` to enclose a section of text. Then, specify center, left, right in the `align` attribute field.

```html
<center>
  centered
</center>

<div align="center">
  centered
</div>

<div align="right">
  right aligned
</div>

<div align="left">
  left aligned
</div>

<div align="justify">
  Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. 
</div>
```

The rendered output will look like this:

<center>
  centered
</center>

<div align="center">
  centered
</div>

<div align="right">
  right aligned
</div>

<div align="left">
  left aligned
</div>

<div align="justify">
  Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. 
</div>

## Superscript and Subscript

| Markdown Command | Rendered Text |
| :--------------- | :------------ |
| `a <sup>superscript</sup>` | a <sup>superscript</sup> |
| `a <sub>subscript</sub>`   | a <sub>subscript</sub> |
