---
title: "Markdown Guide"
date: 2022-02-04T21:19:00-06:00
categories:
  - cheat sheet
tags:
  - Markdown
toc_sticky: true
---

This guide is created for the purpose of *Markdown* syntax reference for myself. The context is mainly based on the site [Markdown Guide](https://www.markdownguide.org/). 

Please note that special syntax allowed in [*kramdown*](https://kramdown.gettalong.org) along with [*Jekyll*](https://jekyllrb.com) will have its own seperate page. This guide intends to include only the basic Markdown syntax, but in no way it is complete.

## Headings

The most common (and suggested) way to specify a heading is by adding one or multiple number signs (`#`) along with a space right before the text of heading. There could be as many as six levels of heading. The number of hash signs corresponds to the number of level, e.g. six hash signs is used for level 6 heading.

Another way to specify a heading is by adding multiple `==` characters for level 1 heading and multiple `--` characters for level 2 heading.

No matter which heading style you choose, **pick one and keep it consistent** across the document. This is also true for all of the following syntax to avoid confusion.

The **suggested** syntax for heading:

```markdown
# Level 1 Headline
## Level 2 Headline
### Level 3 Headline
#### Level 4 Headline
##### Level 5 Headline
###### Level 6 Headline
```

The **alternative** syntax for heading:

```markdown
1st Level Headline
===

2nd Level Headline
---
```

## Text Formatting

In a Markdown document, we could format text in the following ways without using inline HTML.

- *italics*
- **bold**
- ***bold and italics***
- ~~strikethrough~~

### Italic

To turn text into italic face, surround the text with **one** asterisk (`*`) or underscore sign (`_`).

| Markdown Command | Rendered Text |
| :--------------- | :------------ |
| `*this works*`   | *this works* |
| `_this also works_` | _this also works_ |
| `do t*hi*s` | do t*hi*s |
| `don't do t_hi_s` | don't do t_hi_s |

### Bold

To turn text into bold face, surround the text with **two** asterisk signs or underscore signs.

| Markdown Command | Rendered Text |
| :--------------- | :------------ |
| `**this works**` | **this works** |
| `__this also works__`  | __this also works__ |
| `do t**hi**s` | do t**hi**s |
| `don't do t__hi__s` | don't do t__hi__s |

### Bold and Italic

To turn text into bold and italic face, surround the text with **three** asterisk or underscore signs.

| Markdown Command | Rendered Text |
| :--------------- | :------------ |
| `***this works***` | ***this works*** |
| `___this also works___`  | ___this also works___ |
| `__*this also works*__`  | __*this also works*__ |
| `**_this also works_**`  | **_this also works_** |
| `do t***hi***s` | do t***hi***s |
| `don't do t___hi___s` | don't do t___hi___s |

### Strikethrough

To strikethrouhg a text, surround the text with double tilde signs (`~~`).

| Markdown Command | Rendered Text |
| :--------------- | :------------ |
| `~~strikethrough~~` | ~~strikethrough~~ |

## Lists

It is convenient to organize items into lists.

### Ordered Lists

Add line items with numbers followed by periods. The numbers don't have to be in numerical order, but the list should start with the number one. Indent to create a nested list.

The most proper way:

```markdown
1. 1st item
2. 2nd item
    1. 1st sub-item
3. 3rd item
```

It is rendered like this:

1. 1st item
2. 2nd item
    1. 1st sub-item
3. 3rd item

This also works, but it is not the best way:

```markdown
1. 1st item
3. 2nd item
    1. 1st sub-item
2. 3rd item
```

It is rendered like this:

1. 1st item
3. 2nd item
    1. 1st sub-item
2. 3rd item

### Unordered Lists

Add dash (`-`), asterisk (`*`) or plus (`+`) signs in front of the item to create an unordered list. Indent to create a nested list. It is best to keep the unordered list sign consistent and don't mix match. Just pick one and stick with it.

All of the following works:

```markdown
- dash
  - dash
- dash

+ plus
  + plus
+ plus

* asterisk
  * asterisk
* asterisk

- don't
+ do
* this
```

It is rendered like this:

- dash
  - dash
- dash

+ plus
  + plus
+ plus

* asterisk
  * asterisk
* asterisk

- don't
+ do
* this

### Task Lists

Add brackets with a space (`[ ]`) in front of task list items. Task lists will always appear as unordered list. To select the checkbox, replace the space with a `x` inside the brackets.

```markdown
1. [ ] first
2. [x] second

- [ ] dash
  - [x] dash
- [ ] dash

+ [ ] plus
  + [x] plus
+ [ ] plus

* [ ] asterisk
  * [x] asterisk
* [ ] asterisk

- [ ] don't
+ [x] do
* [ ] this
```

The rendered output looks like this:

1. [ ] first
2. [x] second

- [ ] dash
  - [x] dash
- [ ] dash

+ [ ] plus
  + [x] plus
+ [ ] plus

* [ ] asterisk
  * [x] asterisk
* [ ] asterisk

- [ ] don't
+ [x] do
* [ ] this

## Tables

To add a table, use three or more dashed (`---`) to create each column's header, and use pipes (`#`) to separate each column. Add pipe on both ends of the row for compatibility. The widths of cell can vary.

```md
| Header 1    | Header2     |
| ----------- | ----------- |
| r1c1        | r1c2        |
| r2c1        | r2c2        |
```

The rendered output looks like this:

| Header 1    | Header2     |
| ----------- | ----------- |
| r1c1        | r1c2        |
| r2c1        | r2c2        |

It is recommended to use tools like [Tables Generator](https://www.tablesgenerator.com/markdown_tables), or [TableConvert](https://tableconvert.com) to conveniently generate markdown tables without much effort.

### Alignment

To align text in the columns to the left, right or center by adding a colon to the left, right, or on both side of the dashes within the header row.

```md
| Header 1    | Header 2    | Header 3      |
| :---        |    :----:   |          ---: |
| Align       | Align       | Align         |
| Left        | Center      | Right         |
```

The rendered output looks like this:

| Header 1    | Header 2    | Header 3      |
| :---        |    :----:   |          ---: |
| Align       | Align       | Align         |
| Left        | Center      | Right         |

## Code

It is convenient to insert code inside Markdown documents.

### Inline Code

To denote a word or phrase as code, enclose it in backticks (`` ` ``). For example, the rendered output of `` `var` `` looks like `var`.

### Fenced Code Blocks

It is also possible to include code block in Markdown documents. Use triple backticks (`` ``` ``) or tildes (`` ~~~ ``) to enclose the code block. Apply syntax highlighting by specifying the programming language next to the backticks before the fenced code block.

```markdown
~~~python
def hello:
  print("hello world")
~~~
```

the rendered output looks like this:

```python
def hello:
  print("hello world")
```

Common programming languages supported with syntax highlighting are `c`, `cmake`, `cpp` (with alias `c++`), `csharp` (with aliases `c#`, or `cs`), `css`, `diff`, `fortran`, `go`, `html`, `java`, `javascript` (with alias `js`), `json`, `lua`, `make`, `markdown` (or `md`, `mkd`), `matlab` (with alias `m`), `perl` (with alias `pl`), `php` (with alias `php3`, `php4`, `php5`), `plaintext` (with alias `text`), `powershell` (with alias `posh`), `python` (with alias `py`), `r` (with alias `R`, `s`, or `S`), `ruby` (with alias `rb`), `scala`, `shell` (with aliases `bash`, `zsh`, `ksh`, or `sh`), `sql`, `swift`, `tex` (with alias `TeX`, `LaTeX`, or `latex`), `typescript` (with alias `ts`), `vb` (with alias `visualbasic`), `xml`, and `yaml` (with alias `yml`). A nice list of supported syntax highlighting in Jekyll can be found in this [page](https://www.fabriziomusacchio.com/blog/2021-08-11-Syntax_Highlighting_in_Jekyll/).

## Blockquotes

For a single paragraph blockquote, add a `>` in front of a paragraph to create a blockquote.

``` markdown
> This is a blockquote
```

The rendered output looks like this:

> This is a blockquote

For a multiple paragraphs blockquote, add `>` on the blank lines between the paragraphs.

``` markdown
> The first paragraph
>
> The second paragraph
```

The rendered output looks like this:

> The first paragraph
>
> The second paragraph

## Horizontal Rules

To insert horizontal rules in Markdown documents, use three or more asterisks (`***`), dashes (`---`), or underscores (`___`) on a line by themselves.

```md
***
---
___
```

The rendered output of all three looks like this (they all looked identical):
***
---
___

## Links

Link could be presented in Markdown documents, but they differ in syntax from one to another.

### URL

URLs or addresses could be directly created by enclosing them within angle brackets (`<` and `>`). The link to google and an arbitrary email like below.

```markdown
<https://www.google.com>

<fake@example.com>
```

The rendered output looks like this:

<https://www.google.com>

<fake@example.com>

It is also possible to embed link in texts. To do so, enclose the link text in square brackets and then follow it immediately with the URL in parentheses. Optionally, you could also add a title for the link by enclose it in quotation marks after the URL. Titles will appear as a tooltip when the cursor hovers over the link.

```markdown
[Google](https://www.google.com "https://www.google.com") it!
```

The rendered output looks like this:

[Google](https://www.google.com  "https://www.google.com") it!

### Reference-style Links

Reference-style links make it easier to display and read in Markdown. They are constructed in two parts: the part you keep inline and the part you store somewhere else in the file to keep the text easy to read.

The first part of a reference-style link is formatted with two sets of square brackets. The **text link** is put inside the first set of brackets. The **label** of the link is placed inside the second set of brackets. An example for the first part is given below.

```markdown
- [Google][link-google-1]
- [Google][link-google-2]
- [Google][link-google-3]
```

The second part of a reference-style link is formatted with the following attributes:

1. The label placed inside square brackets followed immediately by a colon and at least one space. (`[label]: `)
2. The URL of the link. It is optional to use angle brackets to enclose the URL.
3. Optionally, you can also include the title of the link by enclosing them within double quotes, or single quotes.

``` markdown
[link-google]: https://www.google.com "https://www.google.com"
[link-google]: <https://www.google.com> 'https://www.google.com'
```

Putting together the first and second part of the reference link. The rendered output looks like this:

- [Google][link-google-1]
- [Google][link-google-2]

[link-google-1]: https://www.google.com "https://www.google.com"
[link-google-2]: https://www.google.com 'https://www.google.com'

### Header Links

You can also add links to header by creating a standard link with a number sign followed by the header ID. The header ID is default to the lowercase of heading text where the texts are connected by hyphens if they are originally seperated by spaces in heading.

```md
[Link to the "Reference-style Links" Header](#reference-style-links)
```

The rendered output looks like this:

[Link to the "Reference-style Links" Header](#reference-style-links)

## Images

To insert an image in markdown documents, add an exclamation mark (`!`) followed by alt text (a short description text of the image) in brackets, and the path or URL to the image asset in parentheses. Optionally, you can add a title in quotation marks after the path or URL (similar to the title of links).

```md
![Pablo Escobar meme image](/assets/images/2022-02-04-markdown-guide-pablo-escobar-1.jpg "Pablo Escobar sitting on the bench")
```

The rendered output looks like this:
![Pablo Escobar meme image](/assets/images/2022-02-04-markdown-guide-pablo-escobar-1.jpg "Pablo Escobar sitting on the bench")

To add a link to an image, enclose the image with brackets and include link in the paranthesis followed.

```md
[![Seattle skyline and mountain Ranier](/assets/images/2022-02-04-markdown-guide-seattle.jpg "Seattle skyline and Ranier")](https://images.unsplash.com/photo-1535581652167-3a26c90bbf86?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1740&q=80)
```

The rendered output looks like this:
[![Seattle skyline and mountain Ranier](/assets/images/2022-02-04-markdown-guide-seattle.jpg "Seattle skyline and Ranier")](https://images.unsplash.com/photo-1535581652167-3a26c90bbf86?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1740&q=80)

## Emoji

You can copy and paste an emoji 🚀 from source like [Emojipedia][Emojipedia] or [Unicode Emoji List][Unicode-Emoji-List] to insert an emoji in markdown documents.

[Emojipedia]: https://emojipedia.org "Emojipedia"
[Unicode-Emoji-List]: https://unicode.org/emoji/charts/full-emoji-list.html "Unicode Emoji List"

## $$\LaTeX$$ Commands

To insert a $$\LaTeX$$ command, type the equation enclosed by double dollar signs as below.

```latex
$$a = 1$$

$$\frac{1}{3}$$

$$\pi$$
```

The rendered output looks like this:

$$a = 1$$

$$\frac{1}{3}$$

$$\pi$$

## Footnotes

To add a footnote reference, add a caret (`^`) with an identifier inside brackets. Identifiers need to be alphanumerical, but it cannot contain specs or tabs. In the output, the identifiers are numbered sequentially.

To add footnote, use another caret and with the associated identifier inside brackets. Put the footnote text followed by a colon. (As of now, I have not figured out how not to attach footnote at the bottom of the post.)

```md
Something needs to be noted[^1], and a fact[^ref]

[^1]: A good place to explain further.
[^ref]: The argument is based on some literature.
```

The rendered output looks like this:

Something needs to be noted[^1], and a fact[^ref]

[^1]: A good place to explain further.
[^ref]: The argument is based on some literature.
