---
title:  Pandoc Markdown Example Document
author:
- name: Stephen Margheim
tags: [reference, example, markdown, pandoc]
...

# Atx Header 1

This is *italics*, and this is also _italics_.

## Atx Header 2

This is **bold**, and this is also __bold__.

### Atx Header 3

This ~~is deleted text.~~

#### Atx Header 4

This is subscript: H~2~O.  
This is superscript: 2^10^ is 1024.

##### Atx Header 5

Body text. 

## Atx Header 2 with *italics*

This is an inline link with a title: [example](http://url.com/ "Title")

Setext Header 1 with ID {#foo}
================

This is a reference link with a title: [example2][id]

[id]: http://example.com/  "Title2"

Setext header 2
----------------

This is image syntax (in verbatim mode): `![alt text](/path/img.jpg "Title")`

> This is a block quote. This
> paragraph has two lines.
      
In contrast, this is a code-block:

````
example code-block
````

Below is an example of a Line Block:

| The limerick packs laughs anatomical
| In space that is quite economical.
|    But the good ones I've seen
|    So seldom are clean
| And the clean ones so seldom are comical


Lists
-----

### Bullet lists ###

A bullet list is a list of bulleted list items.  A bulleted list
item begins with a bullet (`*`, `+`, or `-`).  Here is a simple
example:

* one
* two
* three

This will produce a "compact" list. If you want a "loose" list, in which
each item is formatted as a paragraph, put spaces between the items:

* one

* two

* three

The bullets need not be flush with the left margin; they may be
indented one, two, or three spaces. The bullet must be followed
by whitespace.

List items may include other lists.  In this case the preceding blank
line is optional.  The nested list must be indented four spaces or
one tab:

* fruits
    + apples
        - macintosh
        - red delicious
    + pears
    + peaches
* vegetables
    + broccoli
    + chard

### Ordered lists ###

Ordered lists work just like bulleted lists, except that the items
begin with enumerators rather than bullets.

In standard markdown, enumerators are decimal numbers followed
by a period and a space.  The numbers themselves are ignored, so
there is no difference between this list:


1.  one
2.  two
3.  three


and this one:


5.  one
7.  two
1.  three


## Horizontal Rules ##

Three or more dashes or asterisks:

Dashes HR

---
    
Asterisks HR

* * *

Spaced Dashes HR

- - - - 


### Definition lists ###

Pandoc supports definition lists:

Term 1

:   Definition 1


### Numbered example lists ###

The special list marker `@` can be used for sequentially numbered
examples. The first list item with a `@` marker will be numbered '1',
the next '2', and so on, throughout the document. The numbered examples
need not occur in a single list; each new list using `@` will take up
where the last stopped. So, for example:

(@)  My first example will be numbered (1).
(@)  My second example will be numbered (2).

Numbered examples can be labeled and referred to elsewhere in the
document:


> (@good)  This is a good example.

> As (@good) illustrates, ...

**Note**: The raw HTML is passed through unchanged in HTML, S5, Slidy, Slideous, DZSlides, EPUB, Markdown, and Textile output, and suppressed in other formats. Also, Inline LaTeX is ignored in output formats other than Markdown, LaTeX, and ConTeXt. Docx doesn't have internal linking (Internal links are currently supported for HTML formats (including HTML slide shows and EPUB), LaTeX, and ConTeXt).

Pandoc's markdown allows footnotes, using the following syntax:

Here is a footnote reference,[^1] and another.[^longnote]

[^1]: Here is the footnote.

[^longnote]: Here's one with multiple blocks.

    Subsequent paragraphs are indented to show that they
belong to the previous footnote.

        { some.code }

    The whole paragraph can be indented, or just the first
    line.  In this way, multi-paragraph footnotes work like
    multi-paragraph list items.

This paragraph won't be part of the note, because it
isn't indented.

## Citations

In order to use this feature, you will need to specify a bibliography file
using the `bibliography` metadata field in a YAML metadata section. By default, `pandoc-citeproc` will use a Chicago author-date format for
citations and references.  To use another style, you will need to specify
a [CSL] 1.0 style file in the `csl` metadata field. 

Citations go inside square brackets and are separated by semicolons.
Each citation must have a key, composed of '@' + the citation
identifier from the database, and may optionally have a prefix,
a locator, and a suffix.  The citation key must begin with a letter
or `_`, and may contain alphanumerics, `_`, and internal punctuation
characters (`:.#$%&-+?<>~/`).

**Examples:**

# Pandoc with citeproc-hs

-   This citation doesn't exist: [@nonexistent]

-   Neither does this: @nonexistent

-   @item1 says blah.

-   @item1 [p. 30] says blah.

-   @item1 [p. 30, with suffix] says blah.

-   @item1 [-@item2 p. 30; see also @item3] says blah.

-   In a note.[^1]

-   A citation group [see @item1 p. 34-35; also @item3 chap. 3].

-   Another one [see @item1 p. 34-35].

-   And another one in a note.[^2]

-   Citation with a suffix and locator [@item1 pp. 33, 35-37, and nowhere else].

-   Citation with suffix only [@item1 and nowhere else].

-   Now some modifiers.[^3]

-   With some markup [*see* @item1 p. **32**].

# References

The bibliography will be inserted after this header.  Note that
the `unnumbered` class will be added to this header, so that the
section will not be numbered.

If you want to include items in the bibliography without actually
citing them in the body text, you can define a dummy `nocite` metadata
field and put the citations there:

---
nocite: |
   @item1, @item2
...

[^1]: A citation without locators [@item3].

[^2]: Some citations [see @item2 chap. 3; @item3; @item1].

[^3]: Like a citation without author: [-@item1], and now Doe with a locator [-@item2 p. 44].

