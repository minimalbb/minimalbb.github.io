---
title: "Kramdown Markdown Guide with Jekyll"
date: 2022-02-12T14:58:00-06:00
categories:
  - blog
tags:
  - Markdown
  - Kramdown
  - Jekyll
toc_sticky: true
---

When using Jekyll to generate webpages from markdown files for local sites or GitHub Pages, there are a number caveats that needs to be highlighted. There are many more syntax that is not included in this guide, but I will add to this guide when I found them useful. Check [Jekyll documentation][jekyll-doc] and/or [kramdom syntax documentation][kramdown-syntax-doc] for more information.

[jekyll-doc]: https://jekyllrb.com/docs/
[kramdown-syntax-doc]: https://kramdown.gettalong.org/syntax.html

## Emoji :slightly_smiling_face:

If you happen to use Jekyll to build static website and would like to use shortcode to insert emojis (e.g. :rocket: by `:rocket:`), you can to do it through Jekyll plugin [Jemoji][Jemoji]. This will allow Jekyll to render shortcode in the local runs as well as on GitHub Pages. Do the following to enable Jemoji on your Jekyll generated local sites or GitHub Pages.

1. Add Jemoji in the`Gemfile`:
```ruby
gem 'jemoji'
```
2. Add the entry to the plugins list in `_config.yml`:
```yml
plugins:
  - jemoji
```
3. If you are building the site locally, update the bundle by `bundle update` in the command line.

[Jemoji]: https://github.com/jekyll/jemoji 'https://github.com/jekyll/jemoji'

## $$\LaTeX$$ Commands

Many markdown processors come with the ability to interpret LaTeX commands, but not all. If you happen to use Jekyll to build static website and would like to enable LaTeX commands, probably the easiest way is to do it through [MathJax][MathJax]. All you have to do is to include the following HTML script to your layout definition files such as `post.html` or `single.html` located inside the `_layouts` folder. MathJax support will get enabled on all the pages that use those layouts.

```html
<script
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"
  type="text/javascript">
</script>
```

Extended MathJax support can be further enabled by an extensive version of HTML script by Sebastian Flennnerhag mentioned in [Fabrizio Musacchio's website](https://www.fabriziomusacchio.com/blog/2021-08-10-How_to_use_LaTeX_in_Markdown/). Based on his inputs, the extended script would allow inline equation enclosed by single dollar sign just as the original $$\LaTeX$$ syntax. Also, equation numbering can be performed automatically in `equation`, `eqnarray` and `align` environment. Equation referencing can also be done using `\eqref{label}` command.

```html
<script type="text/javascript"
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-AMS_CHTML">
</script>
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [['$','$'], ['\\(','\\)']],
      processEscapes: true},
      jax: ["input/TeX","input/MathML","input/AsciiMath","output/CommonHTML"],
      extensions: ["tex2jax.js","mml2jax.js","asciimath2jax.js","MathMenu.js","MathZoom.js","AssistiveMML.js", "[Contrib]/a11y/accessibility-menu.js"],
      TeX: {
      extensions: ["AMSmath.js","AMSsymbols.js","noErrors.js","noUndefined.js"],
      equationNumbers: {
      autoNumber: "AMS"
      }
    }
  });
</script>
```

[MathJax]: https://www.mathjax.org 'https://www.mathjax.org'

## Notices or Alerts

You can insert notices or alerts by block inline attribute lists (IAL). Simply attach the attribute `{: .notice}` (or its variants listed below) before or after the block-level element to create a notice or alert. This is not part of the syntax feature that comes with standard Markdown but kramdown. See [kramdown documentation for inline attriute lists syntax][kramdown-syntax-ial-doc] for more details.

[kramdown-syntax-ial-doc]: https://kramdown.gettalong.org/syntax.html#inline-attribute-lists "https://kramdown.gettalong.org/syntax.html#inline-attribute-lists"

```md
{: .notice}
Notice (Default) by placing `{: .notice}` above the text

{: .notice--primary}
Notice (Primary) by placing `{: .notice--primary}` above the text

{: .notice--info}
Notice (info) by placing `{: .notice--info}` above the text

{: .notice--warning}
Notice (warning) by placing `{: .notice--warning}` above the text

{: .notice--success}
Notice (success) by placing `{: .notice--success}` above the text

{: .notice--danger}
Notice (danger) by placing `{: .notice--danger}` above the text

Placing the IAL immediately after the bolck element works, too.
{: .notice}

The IAL applies to the preceding element when it is placed immediately before and after a block element.
{: .notice--danger}
The IAL above will not be applied to this line of text, but the one on the bottom will.
{: .notice}
```

The redered ouput looks like this:

{: .notice}
Notice (Default) by placing `{: .notice}` above the text

{: .notice--primary}
Notice (Primary) by placing `{: .notice--primary}` above the text

{: .notice--info}
Notice (info) by placing `{: .notice--info}` above the text

{: .notice--warning}
Notice (warning) by placing `{: .notice--warning}` above the text

{: .notice--success}
Notice (success) by placing `{: .notice--success}` above the text

{: .notice--danger}
Notice (danger) by placing `{: .notice--danger}` above the text

Placing the IAL immediately after the bolck element works, too.
{: .notice}

The IAL applies to the preceding element when it is placed immediately before and after a block element.
{: .notice--danger}
The IAL above will not be applied to this line of text, but the one on the bottom will.
{: .notice}

## Coloring

You can apply color to text by attaching block IAL. Unlike notices or alerts, we have to define the block style by ourselves in advance.

```css
<style>
.white {
  color: white;
}
.gray {
  color: gray;
}
.black {
  color: black;
}
.red {
  color: red;
}
.green {
  color: green;
}
.blue {
  color: blue;
}
.cyan {
  color: cyan;
}
.magenta {
  color: magenta;
}
</style>
```

Then, attach IAL immediately before or after the element similar to  alert block.

```md
A white paragraph.
{: .white}

A gray paragraph.
{: .gray}

A black paragraph.
{: .black}

A red paragraph.
{: .red}

A green paragraph.
{: .green}

A blue paragraph.
{: .blue}

A cyan paragraph.
{: .cyan}

A magenta paragraph.
{: .magenta}
```

<style>
.white {
  color: white;
}
.gray {
  color: gray;
}
.black {
  color: black;
}
.red {
  color: red;
}
.green {
  color: green;
}
.blue {
  color: blue;
}
.cyan {
  color: cyan;
}
.magenta {
  color: magenta;
}
</style>

The rendered output looks like this:

A white paragraph.
{: .white}

A gray paragraph.
{: .gray}

A black paragraph.
{: .black}

A red paragraph.
{: .red}

A green paragraph.
{: .green}

A blue paragraph.
{: .blue}

A cyan paragraph.
{: .cyan}

A magenta paragraph.
{: .magenta}

## Alignment

Text alignment can be achieved by block IAL, too. Simply attach block IAL shown below to format text as centered, left-aligned, right-aligned, or justified.

```md
Centered text.
{: .text-center}

Left aligned text.
{: .text-left}

Right aligned text.
{: .text-right}

Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text.
{: .text-justify}
```

The rendered output will look like this:

Centered text.
{: .text-center}

Left aligned text.
{: .text-left}

Right aligned text.
{: .text-right}

Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text. Justified text.
{: .text-justify}
