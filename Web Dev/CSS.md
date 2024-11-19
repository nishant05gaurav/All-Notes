## `CSS`:

- Stands for Cascading Style Sheets, created by **Håkon Wium Lie**
- It is a stylesheet language used to describe the visual presentation of a webpage written in HTML
- It operates by selecting HTML elements and applying styles to them

```js
                                selector
                                    |
                                    |___h1{
                                        color:  red;
                                          |      |
                                          |      |
                                          V      V
                                      property  value
                                    }
```

#### `Feature`:

- Styles and layouts of webpages
- Enables responsive design for different screen sizes
- Allows reusability of same code

### `Ways to add CSS`:

1. **Inline**:

- Used to apply a unique style for a single element
- To use inline CSS, Insert the `style` attribute within the HTML element's opening tag.

```js
<h1 style="color: red"> Nishant Gaurav </h1>
```

2. **Internal**:

- Used when we are designing a single HTML page
- Define under `<style>` tag in the `head` section below `<title>` element
- Written below the `<title>` tag in HTML

```js
                                <style>
                                    h1{
                                        color: magenta;
                                    }
                                </style>
```

3. **External**:

- With using the external style-sheet, we can change the look/view of an entire website by changing just one file

```js
                    <link rel = "spreadsheet" href = "style.css>
```

- We have to link this file in the `<head>` section of HTML
- `rel=stylesheet`: **rel** stands for the relationship b/w the HTML document and the linked resource i.e, **spreadsheet**through this we used to style the HTML content
- `href` attribute stands for hypertext reference. It specifies the path or URL to the external resource.

#### The priority of these three are as follows: `Inline CSS > Internal CSS > External CSS`
- If we add `!important`in any  of the threee then its effect become the final one  

### `CSS Selectors`: CSS selectors allow us to choose specific elements and apply styles to them
1. **Universal Selector**: Represented by `*` targets all the HTML elements on the page.
```js
                                * {
                                    property : value;
                                }                    
```
2. `Element Selector`: Selects the target element based on the specific type.
-  It is not recommended as the same tag can be used multiple times in the document
```js
                                Element {
                                    property : value;
                                }
```
3. `ID Selector`:  Targets the elements based on the specific ID and written with `#`
```js
                                #ID {
                                    property : value;
                                }
```
4. `Class Selector`: Targets group of various types of elements and written with the period `.` followed by the class name
- It helps in grouping two or more elements.
```js
                                .class {
                                    property : value;
                                }
```
5. `Group Selector`: Used to minimise the code.  Commas `,` are used to separate each selector in a grouping.
```js
                                div, p, a {
                                    property : value;
                                }
```

### `Properties in CSS`:

1. **Color Property**: Used to set the color of _foreground_

```js
                                color: red;
                                color: pink;
```

2. **Background-Color Property**: Used to set the color of _background_

```js
                                background-color: red;
                                background-color: pink;
```
   
3. **Text-Properties**
   1. `text-allign`: left/right/centre
   2. `text-decoration`: underline/ overline/ line-through
   ```js
                                text-decoration: underline;
                                text-decoration: underline dotted;
                                text-decoration: underline dotted red;
                                text-decoration-style: green wavy underline;
                                text-decoration: underline overline #FF3028;
   ```
   3. `font-weight`: normal/ bold/ bolder/ lighter
      - value varies from 100-900
   4. `font-family`: arial/ arial,roboto
      - We can give multiple text as if one fails then second one gets loaded
   5. `line-height`: 2px/ 3/ normal (gives height b/w two lines)
   6. `text-transform`: uppercase/ lowercase/ capitalize/ none
4. **Display Property**:

   1. _inline_: Takes only the soace required by the element (no marging/ padding)
   2. _block_: Take full space availabile in width
   3. _inline-block_: Similar to inline but we can set margin and padding
   4. _none_: To remove element from document flow
      ![alt text](https://imgur.com/0HGEZno.png)

5. **Visibility**:
   ![alt text](https://imgur.com/qe3mR9B.png)

- _When_ **visibility** _is set to_ `none` _, space for the element is reserved. But for_ **display** _set to_ `none` _, no space is reserved or blocked for the element_

1. **Position**: The position CSS property sets how an element is positioned in a document.
   `position: static/ relative/ absolute/ fixed`

- static: default position (top, left, bottom, right and z-index properties have no effect)
- relative: element is relative to itself (top, left, bottom, right and z-index properties will work)
- absolute: positioned relative to its closest positioned ancestor (removed from the follow)
- fixed: positioned relative to browser (removed from flow)
- sticky: positioned based on user's scroll position

7. **z-index**:
- It decides the stack level of elements
- Overlapping elements with a large z-index cover those with a smaller one

```js
                                z-index: auto(0)
                                z-index: 1/ 2/ 3...
                                z-index: -1/ -2/ -3..
```

8. **Backgound-Image**: Used to set an image in the background

```js
                               background-image: url(img.jpeg);
```

9. **Backgound-size**:

```js
                               background-size: cover/ contain/ auto;
```

10. **Bachground Repeat**:
```js
                                selector{
                                   background-repeat: repeat-x || repeat-y || repeat || no-repeat;
                                }
repeat-x    --> repeats the image in x-dirn
repeat-y    --> repeats the image in y-dirn
repeat      --> repeats the image both in x and y dirn
no repeat   --> donot repeats the image 
```
11. **max-content**: Makes the element as wide as its content but not wider than the scree
```js
                                selector{
                                     width: max-content;
                                }
```
12. **min-content**: Makes the element's width shrink to the minimum required to display its content
```js
                                selector{
                                    width: min-content;
                                }
```
13. **Text Shadow**: Property adds a shadow to the text.
```js
                    selector{
                        text-shadow:  Horizontal offset, vertical offset, blur radius, color;
                    }
```
14. **CSS Hover**: Used to enhance the user experience by changing the appearance or the behaviour of the HTML element(s) when the user hovers over it.
```js
                                    selector:hover{
                                                /* CSS rule(s) */;
                                                border: 5px solid purple;
                                    }
```


### `Units in CSS`:

- Its in pixles(px)
- 96px = 1 inch

### `Box Model in CSS`:

![Box Model](https://imgur.com/Rz9ei7A.png)

- It is essentially a boc that wraps around every HTML element. It consists of: content, padding, borders and margins
- **Content** - The content of the box, where text and images appear
- **Padding** - Clears an area around the content. The padding is transparent
- **Border** - A border that goes around the padding and content
- **Margin** - Clears an area outside the border. The margin is transparent

1. `Height`: By default, it sets the content area _height_ of the element

```js
                                div{
                                    height: 50px;
                                }
```

- `Total element height` = height + top padding + bottom padding + top border + bottom border

2. `Width`: By default, it sets the content area _width_ of the element

```js
                                div{
                                    width: 50px;
                                }
```

- `Total element width` = width + left padding + right padding + left border + right border

3. `Border`: Used to set an element's border

```js
                                border-width: 2px;
                                border-style: solid/ dotted/ dashed;
                                border-color: black;
                    -------------------------------------------------------
                                     or simply
                    -------------------------------------------------------
                                 border: 2px solid black;
                                 border-radius: 10px;
                                 border-radius: 50%;
                   [Used to round the corners of an elements outer border edge]
```

4. `Margin and Padding`:

- It is done in four ways:

```js
                           margin-right:  /*value*/;  || padding-right:  /*value*/
                           margin-left:  /*value*/;   || padding-left:  /*value*/
                           margin-top:  /*value*/;    || padding-top:  /*value*/
                           margin-bottom:  /*value*/; || padding-bottom:  /*value*/

                                              padding/margin: 50px;
                               padding/margin: 1px 2px 3px 4px;
                                                |   |   |    |
                                        (top)___|   |   |    |___(left)                 --> Clockwise
                                                    |   |
                                        (right)_____|   |_______(bottom)
```

### `Units in CSS`:

- `Percentage (%)`:It is oftem used to define a size as relative to an elements parent object
- `Em`: Font-size of the parent, in the case of typographical properties like `font-size`, and font-size of the element itself, in the case of other properties like `width`
  - If the element's font size is 1.5 em, that means the element will be 1.5 times the size of the parent.
- `Root Em (Rem)`: Front size of the root element and based on the font size of the root element
- `vh`: relative to 1% viewport height
- `vw`: relative to 1% viewport width
