---
layout: post
title:  Kramdown Syntax
categories: Etc
tags: kramdown
---

* content
{:toc}

{::comment}===================={:/}
## Headers

#### Setext Style
{:.no_toc}
~~~
First level header
==================

Second level header
------

Other first level header
=
~~~

#### atx Style
{:.no_toc}
~~~
# First level header (h1)

## Second level header (h2)
...
###### Sixth level header (h6)
~~~

{::comment}===================={:/}
## Blockquotes
~~~
> This is the first blockquote.
>     on multiple lines
that may be lazy.
>
> This is the second paragraph.
>
> > This is the second blockquote.
~~~

> This is the first blockquote.
>     on multiple lines
that may be lazy.
>
> This is the second paragraph.
>
> > This is the second blockquote.


{::comment}===================={:/}
## Code Blocks

#### Standard Code Blocks
{:.no_toc}
A code block can be started by using *`four spaces`* or *`one tab`* and
then the text of the code block.
~~~
    Here comes some code

    This text belongs to the same code block.
~~~


#### Fenced Code Blocks
{:.no_toc}
~~~~~~
~~~
Here comes some code.
~~~
~~~~~~

#### Language of Code Blocks
{:.no_toc}
~~~~~~
~~~
Console.WriteLine("How to use the Code Blocks? First method");
~~~
{: .language-csharp}
~~~~~~

~~~
Console.WriteLine("How to use the Code Blocks? First method");
~~~
{: .language-csharp}

or

~~~~~~
~~~ csharp
Console.WriteLine("How to use the Code Blocks? Second method");
~~~
~~~~~~

~~~ csharp
Console.WriteLine("How to use the Code Blocks? Second method");
~~~

{::comment}===================={:/}
## Lists
A list is started with a list marker (in case of unordered lists one of `+`, `-` or `*` – you can mix them – and in case of ordered lists a number followed by `a period`) followed by `one tab` or at least `one space`

#### Ordered lists
{:.no_toc}

~~~
1. ordered list 1, item 1
    1. nested list item 1 (indent `four spaces` or `one tab`)
2. ordered list 1, item 2
^
1. ordered list 2, item 1
    2. nested list item 1
        3. nested list item 2
            4. nested list item 3
2. ordered list 1, item 2
10. ordered list 1, item 3
~~~

1. ordered list 1, item 1
    1. nested list item 1 (indent `four spaces` or `one tab`)
2. ordered list 1, item 2
^
1. ordered list 2, item 1
    2. nested list item 1
        3. nested list item 2
            4. nested list item 3
2. ordered list 1, item 2
10. ordered list 1, item 3

#### Unordered lists
{:.no_toc}

~~~
+ unordered list, item 1
    - nested list item 1
        * nested list item 2
            + nested list item 3
* unordered list, item 2
~~~

+ unordered list, item 1
    - nested list item 1
        * nested list item 2
            + nested list item 3
* unordered list, item 2

#### Definition Lists
{:.no_toc}

~~~
definition term
: This definition will just be text because it would normally be a
  paragraph and the there is no preceding blank line.

  > although the definition contains other block-level elements

: This definition *will* be a paragraph since it is preceded by a
  blank line.
~~~

definition term
: This definition will just be text because it would normally be a
  paragraph and the there is no preceding blank line.

  > although the definition contains other block-level elements

: This definition *will* be a paragraph since it is preceded by a
  blank line.

{::comment}===================={:/}
## Tables

~~~
|-----------------+------------+-----------------+----------------|
| Default aligned |Left aligned| Center aligned  | Right aligned  |
|-----------------|:-----------|:---------------:|---------------:|
| First body part |Second cell | Third cell      | fourth cell    |
| Second line     |foo         | **strong**      | baz            |
| Third line      |quux        | baz             | bar            |
|-----------------+------------+-----------------+----------------|
| Second body     |            |                 |                |
| 2 line          |            |                 |                |
|=================+============+=================+================|
| Footer row      |            |                 |                |
|-----------------+------------+-----------------+----------------|
~~~

|-----------------+------------+-----------------+----------------|
| Default aligned |Left aligned| Center aligned  | Right aligned  |
|-----------------|:-----------|:---------------:|---------------:|
| First body part |Second cell | Third cell      | fourth cell    |
| Second line     |foo         | **strong**      | baz            |
| Third line      |quux        | baz             | bar            |
|-----------------+------------+-----------------+----------------|
| Second body     |            |                 |                |
| 2 line          |            |                 |                |
|=================+============+=================+================|
| Footer row      |            |                 |[see more][kramdown_table1]|
|-----------------+------------+-----------------+----------------|

[kramdown_table1]: https://kramdown.gettalong.org/syntax.html#tables "kramdown Syntax - tables"

{::comment}===================={:/}
## Horizontal Rules

~~~
* * *

---

  _  _  _  _

---------------
~~~

* * *

---

  _  _  _  _

---------------

{::comment}===================={:/}
## Links and Images
Three types of links are supported: automatic links, inline links and reference links.

#### Automatic Links
{:.no_toc}

~~~
Information can be found on the <http://example.com> homepage.\\
You can also mail me: <me.example@example.com>
~~~

>
Information can be found on the <http://example.com> homepage.\\
You can also mail me: <me.example@example.com>
{: class="preview"}

#### Inline Links
{:.no_toc}

~~~
This is [a link](http://google.com) to a page.
A [link](../test "local URI") can also have a title.
And [spaces](link with spaces.html)!
~~~
>
This is [a link](http://rubyforge.org) to a page.
A [link](../test "local URI") can also have a title.
And [spaces](link with spaces.html)!
{: class="preview"}

#### Reference Links
{:.no_toc}

~~~
This is a [reference style link][linkid] to a page.
And [this][linkid] is also a link. As is [this][] and [THIS].

[linkid]: http://www.example.com/ "Optional Title"
~~~

>
This is a [reference style link][linkid] to a page.
And [this][linkid] is also a link. As is [this][] and [THIS].
>
[linkid]: http://www.example.com/ "Optional Title"
{: class="preview"}

#### Images
{:.no_toc}

~~~
Here comes a ![smiley](../images/smiley.png)! And here
![too](../images/other.png 'Title text'). Or ![here].
With empty alt text ![](see.jpg)
~~~

>
Here comes a ![smiley](/assets/img/noti_fore_smile.png)! And here
![too](/assets/img/noti_fore_chatting.png 'Title text'). Or ![here].
With empty alt text ![](/assets/img/noti_fore_chatting.png)
{: class="preview"}

~~~
Here is an inline ![smiley](smiley.png){:height="56px" width="33px"}.
And here is a referenced ![smile]

[smile]: smile.png "Title text"
{: height="56px" width="33px"}
~~~

>
Here is an inline ![smiley](/assets/img/noti_fore_smile.png){:height="56px" width="33px"}.
And here is a referenced ![smile]
{: class="preview"}

[smile]: /assets/img/noti_fore_smile.png "Title text"
{: height="56px" width="33px"}

{::comment}===================={:/}
## Emphasis

~~~
This is a ***text with light and strong emphasis***.
This **is _emphasized_ as well**.
This *does _not_ work*.
This **does __not__ work either**.
~~~

>
This is a ***text with light and strong emphasis***.\\
This **is _emphasized_ as well**.\\
This *does _not_ work*.\\
This **does __not__ work either**.
{: class="preview"}

{::comment}===================={:/}
## Code Spans

~~~
Use `<html>` tags for this.
~~~

>
Use `<html>` tags for this.
{: class="preview"}

~~~
Here is a literal `` ` `` backtick.
And here is ``  `some`  `` text (note the two spaces so that one is left
in the output!).
~~~
>
Here is a literal `` ` `` backtick.\\
And here is ``  `some`  `` text (note the two spaces so that one is left\\
in the output!).
{: class="preview"}

~~~
This is a ` literal backtick.
As \`are\` these!
~~~

>
This is a ` literal backtick.
As \`are\` these!
{: class="preview"}

~~~
This is a C# code fragment `x = new SmartListBox();`{:.language-csharp}
~~~

>
This is a C# code fragment `x = new SmartListBox();`{:.language-csharp .highlight}
{: class="preview"}

{::comment}===================={:/}
## Footnotes

~~~
This is some text.[^1]. Other text.[^footnote]

[^1]: Some *crazy* footnote definition.
[^footnote]: this is a footnote definition.
~~~

This is some text.[^1]. Other text.[^footnote]

[^1]: Some *crazy* footnote definition.
[^footnote]: this is a footnote definition.

{::comment}===================={:/}
## Extensions

~~~~~~
{::comment}
This text is completely ignored by kramdown - a comment in the text.
{:/comment}

Do you see {::comment}this text{:/comment}?
{::comment}some other comment{:/}

{::options key="val" /}
~~~~~~

>
{::comment}
This text is completely ignored by kramdown - a comment in the text.
{:/comment}
>
Do you see {::comment}this text{:/comment}?
{::comment}some other comment{:/}
>
{::options key="val" /}
{: class="preview"}

---
