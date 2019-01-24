# SCSS Demo

![sass logo](./resources/Sass.png)

---

## Instructions

1. Install SASS using npm
    ```bash
    npm install -g sass
    ```
2. Compile the SASS files into CSS which could be used in a webpage.
    ```bash
    sass ./sass/styles.scs ./css/main.css
    ```
3. The compiled CSS could be seen by visiting `./index.html`

**For documentation on SASS/SCSS visit the [Documentation](https://sass-lang.com).**

---

## SASS Structure

* `scss/style.scss` - The primary stylesheet. This is the file that will be compiled and will import all subsequent files.
* `scss/modules` - Reserved for scss code that does not cause sass to output CSS. Things like mixin declarations, functions, and variables.
* `scss/partials` - Where most of the meat of the scss is constructed.
* `scss/vendor` - Reserved for 3rd party CSS, such as `Normalize.css`

**For more information on file structure, check out [John W. Long's Blog](http://thesassway.com/beginner/how-to-structure-a-sass-project).**

---

## Important Notes

### SASS

Below is a list of the core features in SASS which you will see the most. Most of using SASS is just knowing CSS the other part is making CSS **DRY** (Don't Repeat Yourself).

* #### Variables
    A way to store information that can be reused throughout the stylesheet (anything from colors, font-weight, datatypes, etc...).
    ```sass
    $white: #fff;
    $box-size: 16px;
    ...

* #### Nesting
     Sass will let you nest your CSS selectors in a way that follows the same visual hierarchy of your HTML. Be aware that overly nested rules will result in over-qualified CSS that could prove hard to maintain and is generally considered bad practice.
    ```scss
    nav {
        position: relative;

        // Equivalent to nav::before
        &::before {
            content: 'hello world!'
            position: absolute;
            top: -5px;
            right: -5px;
        }

        ul {
            margin: 0;
            padding: 0;
            list-style: none;
        }

        li { display: inline-block; }

        a {
            display: block;
            padding: 6px 12px;
            text-decoration: none;
        }
    }
    ```

* #### Partials
    You can create partial Sass files that contain little snippets of CSS that you can include in other Sass files. This is a great way to modularize your CSS and help keep things easier to maintain. A partial is simply a Sass file named with a leading underscore. You might name it something like `_partial.scss`. The underscore lets Sass know that the file is only a partial file and that it should not be generated into a CSS file. Sass partials are used with the `@import` directive.

* #### Extend/Inheritance
    Using @extend lets you share a set of CSS properties from one selector to another. It helps keep your Sass very DRY.
    ```scss
    /* This CSS will print because %message-shared is extended. */
    %message-shared {
        border: 1px solid #ccc;
        padding: 10px;
        color: #333;
    }

    // This CSS won't print because %equal-heights is never extended.
    %equal-heights {
        display: flex;
        flex-wrap: wrap;
    }

    .message {
        @extend %message-shared;
    }

    .success {
        @extend %message-shared;
        border-color: green;
    }

    .error {
        @extend %message-shared;
        border-color: red;
    }

    .warning {
        @extend %message-shared;
        border-color: yellow;
    }

* #### Mixins
    A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. 
    ```scss
    @mixin transform($property) {
        -webkit-transform: $property;
        -ms-transform: $property;
        transform: $property;
    }

    .box { @include transform(rotate(30deg)); }
    ```

* #### Functions
    A function is very similar to a mixin, however the output from a function is a single value. This can be any Sass data type, including: numbers, strings, colors, booleans, or lists.
    ```scss
    @function my-calculation-function($some-number, $another-number){
        @return $some-number + $another-number
    }
    .my-module {
        padding: my-calculation-function(10px, 5px);
    }

* #### Operators
    Sass has a handful of standard math operators like +, -, *, /, and %.
    ```scss
    .container {
        width: 100%;
    }

    article[role="main"] {
        float: left;
        width: 600px / 960px * 100%;
    }

    aside[role="complementary"] {
        float: right;
        width: 300px / 960px * 100%;
    }
    ```