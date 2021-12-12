---
description: How to use the formatting and layout features of the ixo-WebApp
---

# Entity Page Styling

The Page View for any entity displayed in the ixo-WebApp is configured using pre-built cards.

In the Create \<entity> Studio view, the page layout can be modified using the drag-and-drop feature to move the order of cards.

The **Main Section** Card at the top of this page cannot be moved or removed, as this contains the minimum required information for setting up an entity and having it display in the Explorer interface.

{% hint style="warning" %}
All information included in the Main Section card is publicly visible and will be stored on the chain. Therefore please do not include sensitive information, or personall identifiable information that would compromise any user's privacy or data protection rights.&#x20;
{% endhint %}

If you do not want to include a card type on the page, the sections in the card can be removed by selecting `- Remove`

Additional sections can be added within each card by selecting `+ Add Section` &#x20;

Within the card text fields, you can use basic Markdown for formatting the text, using the syntax shown below.

## Markdown Styling Options

_Implements Showdown (_[_check out their documentation_](https://github.com/showdownjs/showdown/wiki/Showdown's-Markdown-syntax)_)._

### Paragraphs

Paragraphs in Showdown are just **one or more lines of consecutive text** followed by one or more blank lines.

```
On July 2, an alien mothership entered Earth's orbit and deployed several dozen 
saucer-shaped "destroyer" spacecraft, each 15 miles (24 km) wide.
    
On July 3, the Black Knights, a squadron of Marine Corps F/A-18 Hornets, 
participated in an assault on a destroyer near the city of Los Angeles.
```

The implication of the “one or more consecutive lines of text” is that Showdown supports “hard-wrapped” text paragraphs. This means the following examples produce the same output:

```
A very long line of text
```

```
A very
long line
of text
```

If you DO want to add soft line breaks (which translate to `<br>` in HTML) to a paragraph, you can do so by adding 3 space characters to the end of the line (  ``  ).

You can also force every line break in paragraphs to translate to `<br>` (as Github does) by enabling the option **`simpleLineBreaks`**.

### Headings

#### Atx Style

You can create a heading by adding one or more # symbols before your heading text. The number of # you use will determine the size of the heading. This is similar to [**atx style**](http://www.aaronsw.com/2002/atx/intro).

```
# The largest heading (an <h1> tag)
## The second largest heading (an <h2> tag)
…
###### The 6th largest heading (an <h6> tag)
```

The space between `#` and the heading text is not required but you can make that space mandatory by enabling the option **`requireSpaceBeforeHeadingText`**.

You can wrap the headings in `#`. Both leading and trailing `#` will be removed.

```
## My Heading ##
```

If, for some reason, you need to keep a leading or trailing `#`, you can either add a space or escape it:

```
# # My header # #

#\# My Header \# #
```

#### Setext style

You can also use [**setext style**](https://en.wikipedia.org/wiki/Setext) headings, although only two levels are available.

```
This is an H1
=============
    
This is an H2
-------------
```

#### Header IDs

Showdown generates bookmarks anchors in titles automatically, by adding an id property to an heading.

```
# My cool header with ID
```

```
<h1 id="mycoolheaderwithid">My cool header with ID</h1>
```

This behavior can be modified with options:

* **`noHeaderId`** disables automatic id generation;
* **`ghCompatibleHeaderId`** generates header ids compatible with github style (spaces are replaced with dashes and a bunch of non alphanumeric chars are removed)
* **`prefixHeaderId`** adds a prefix to the generated header ids (either automatic or custom).
* **`headerLevelStart`** sets the header starting level. For instance, setting this to 3 means that `# header` will be converted to `<h3>`.

Read the [README.md](https://github.com/showdownjs/showdown/blob/master/README.md) for more info

### Blockquotes

You can indicate blockquotes with a >.

```
In the words of Abraham Lincoln:
    
> Pardon my french
```

Blockquotes can have multiple paragraphs and can have other block elements inside.

```
> A paragraph of text
>
> Another paragraph
>
> - A list
> - with items
```

### Bold and Italic

You can make text bold or italic.

```
*This text will be italic*
**This text will be bold**
```

Both bold and italic can use either a \* or an \_ around the text for styling. This allows you to combine both bold and italic if needed.

```
**Everyone _must_ attend the meeting at 5 o'clock today.**
```

### Strikethrough

With the option **`strikethrough`** enabled, Showdown supports strikethrough elements. The syntax is the same as GFM, that is, by adding two tilde (`~~`) characters around a word or groups of words.

```
a ~~strikethrough~~ element
```

a ~~strikethrough~~ element

### Emojis

Since version 1.8.0, showdown supports github's emojis. A complete list of available emojis can be foun [here](https://github.com/showdownjs/showdown/wiki/emojis).

```
this is a :smile: smile emoji
```

this is a ![:smile:](https://camo.githubusercontent.com/439fc032bd7e925325f1d8a75823636ba3073089f21aab336f5f9f42bf4a226b/68747470733a2f2f6769746875622e6769746875626173736574732e636f6d2f696d616765732f69636f6e732f656d6f6a692f756e69636f64652f31663630342e706e67) smile emoji

### Code formatting

#### Inline formats

Use single backticks (\`) to format text in a special monospace format. Everything within the backticks appear as-is, with no other special formatting.

```
Here's an idea: why don't we take `SuperiorProject` and turn it into `**Reasonable**Project`.
```

```
<p>Here's an idea: why don't we take <code>SuperiorProject</code> and turn it into <code>**Reasonable**Project</code>.</p>
```

#### Multiple lines

To create blocks of code you should indent it by four spaces.

```
    this is a piece
    of
    code
```

If the options **`ghCodeBlocks`** is activated (which is by default), you can use triple backticks (\`\`\`) to format text as its own distinct block.

````
Check out this neat program I wrote:

```
x = 0
x = 2 + 2
what is x
```
````

### Lists

Showdown supports ordered (numbered) and unordered (bulleted) lists.

#### Unordered lists

You can make an unordered list by preceding list items with either a \*, a - or a +. Markers are interchangeable too.

```
* Item
+ Item
- Item
```

#### Ordered lists

You can make an ordered list by preceding list items with a number.

```
1. Item 1
2. Item 2
3. Item 3
```

It’s important to note that the actual numbers you use to mark the list have no effect on the HTML output Showdown produces. So you can use the same number in all items if you wish to.

#### TaskLists (GFM Style)

Showdown also supports GFM styled takslists if the **`tasklists`** option is enabled.

```
 - [x] checked list item
 - [ ] unchecked list item
```

* [x] &#x20;checked list item
* [ ] &#x20;unchecked list item

#### List syntax

List markers typically start at the left margin, but may be indented by up to three spaces.

```
   * this is valid
   * this is too  
```

List markers must be followed by one or more spaces or a tab.

To make lists look nice, you can wrap items with hanging indents:

```
*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
    Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
    viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
    Suspendisse id sem consectetuer libero luctus adipiscing.
```

But if you want to be lazy, you don’t have to

If one list item is separated by a blank line, Showdown will wrap all the list items in `<p>` tags in the HTML output. So this input:

```
* Bird

* Magic
* Johnson
```

Results in:

```
<ul>
<li><p>Bird</p></li>
<li><p>Magic</p></li>
<li><p>Johnson</p></li>
</ul>
```

This differs from other markdown implementations such as GFM (github) or commonmark.

#### Nested blocks

List items may consist of multiple paragraphs. Each subsequent paragraph in a list item must be indented by either 4 spaces or one tab:

```
1.  This is a list item with two paragraphs. Lorem ipsum dolor
    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
    mi posuere lectus.

    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
    sit amet velit.

2.  Suspendisse id sem consectetuer libero luctus adipiscing.
```

This is valid for other block elements such as blockquotes:

```
*   A list item with a blockquote:

    > This is a blockquote
    > inside a list item.
```

or event other lists.

#### Nested lists

You can create nested lists by indenting list items by **four** spaces.

```
1.  Item 1
    1. A corollary to the above item.
    2. Yet another point to consider.
2.  Item 2
    * A corollary that does not need to be ordered.
    * This is indented four spaces
    * You might want to consider making a new list.
3.  Item 3
```

This behavior is consistent with the original spec but differs from other implementations such as GFM or commonmark. Prior to version 1.5, you just needed to indent two spaces for it to be considered a sublist. You can disable the **four spaces requirement** with option **`disableForced4SpacesIndentedSublists`**

To nest a third (or more) sublist level, you need to indent 4 extra spaces (or 1 extra tab) for each level.

```
1.  level 1
    1.  Level 2
        *   Level 3
    2.  level 2
        1.  Level 3
1.  Level 1
```

#### Nested code blocks

You can nest fenced codeblocks the same way you nest other block elements, by indenting by fours spaces or a tab:

````
1.  Some code:

    ```js
    var foo = 'bar';
    console.log(foo);
    ```
````

To put a _indented style_ code block within a list item, the code block needs to be indented twice — 8 spaces or two tabs:

```
1.  Some code:

    var foo = 'bar';
    console.log(foo);
```

### Links

#### Simple

If you wrap a valid URL or email in `<>` it will be turned into a link whose text is the link itself.

```
link to <http://www.google.com/>

this is my email <somedude@mail.com>
```

In the case of email addreses, Showdown will also perform a bit of randomized decimal and hex entity-encoding to help obscure your address from address-harvesting spambots. You can disable this obfuscation setting **`encodeEmails`** option to `false`.

With the option **`simplifiedAutoLink`** enabled, Showdown will automagically turn every valid URL it finds in the text body to links for you, without the need to wrap them in `<>`.

```
link to http://www.google.com/

this is my email somedude@mail.com
```

#### Inline

You can create an inline link by wrapping link text in brackets ( `[ ]` ), and then wrapping the link in parentheses ( `( )` ).

For example, to create a hyperlink to github.com/showdownjs/showdown, with a link text that says, Get Showdown!, you'd write this in Markdown: `[Get Showdown!](https://github.com/showdownjs/showdown)`.

#### Reference Style

You can also use the reference style, like this:

```
this is a [link to google][1]

[1]: www.google.com
```

Showdown also supports implicit link references:

```
this is a link to [google][]

[google]: www.google.com
```

### Images

Markdown uses an image syntax that is intended to resemble the syntax for links, also allowing for two styles: inline and reference.

#### Inline

Inline image syntax looks like this:

```
![Alt text](url/to/image)

![Alt text](url/to/image "Optional title")
```

That is:

* An exclamation mark: !;
* followed by a set of square brackets, containing the alt attribute text for the image;
* followed by a set of parentheses, containing the URL or path to the image, and an optional title attribute enclosed in double or single quotes.

#### Reference Style

Reference-style image syntax looks like this:

```
![Alt text][id]
```

Where “id” is the name of a defined image reference. Image references are defined using syntax identical to link references:

```
[id]: url/to/image  "Optional title attribute"
```

Implicit references are also supported in images, similar to what happens with links:

```
![showdown logo][]

[showdown logo]: http://showdownjs.github.io/demo/img/editor.logo.white.png
```

#### Image dimensions

When the option **`parseImgDimension`** is activated, you can also define the image dimensions, like this:

```
![Alt text](url/to/image =250x250 "Optional title")
```

or in reference style:

```
![Alt text][id]

[id]: url/to/image =250x250
```

#### Base64 encoded images

Showdown also supports Base64 encoded images, both reference and inline style. **Since version 1.7.4**, wrapping base64 strings, which are usually extremely long lines of text, is supported. You can add newlines arbitrarily, as long as they are added after the `,` character.

**inline style**

```
![Alt text](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAQAAAADCAIAAAA7l
jmRAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAAY
SURBVBhXYwCC/2AAZYEoOAMs8Z+BgQEAXdcR7/Q1gssAAAAASUVORK5CYII=)
```

**reference style**

```
![Alt text][id]

[id]:
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAQAAAADCAIAAAA7l
jmRAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7D
AcdvqGQAAAAYSURBVBhXYwCC/2AAZYEoOAMs8Z+BgQEAXdcR7/Q1gssAAAAASUVORK5CYII=
```

Please note that with reference style base64 image sources, regardless of "wrapping", a double newline is needed after the base64 string to separate them from a paragraph or other text block (but references can be adjacent).

**wrapped reference style**

```
![Alt text][id]
![Alt text][id2]

[id]:
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAQAAAADCAIAAAA7l
jmRAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7D
AcdvqGQAAAAYSURBVBhXYwCC/2AAZYEoOAMs8Z+BgQEAXdcR7/Q1gssAAAAASUVORK5CYII=
[id2]:
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAQAAAADCAIAAAA7l
jmRAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7D
AcdvqGQAAAAYSURBVBhXYwCC/2AAZYEoOAMs8Z+BgQEAXdcR7/Q1gssAAAAASUVORK5CYII=

this text needs to be separated from the references by 2 newlines
```

###

\
\


