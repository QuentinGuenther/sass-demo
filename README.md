# SCSS Demo

![sass logo](./resources/Sass.png)

---

## Table of Contents

1. [Introduction](#introduction)
2. [Instructions](#instructions)
3. [Sass Project Structure](#sass-project-structure)
4. [Important Notes](#important-notes)
    1. [SASS](#sass)
        1. [Variables](#variables)
        2. [Nesting](#nesting)
        3. [Partials](#partials)
        4. [Extend/Inheritance](#extend-inheritance)
        5. [Mixins](#mixins)
        6. [Functions](#functions)
        7. [Operations](#operations)

---

## Introduction

>Sass stands for *Syntactically Awesome Stylesheets*. Sass and is basically just an extension to CSS that help us write more flexible styles.
It helps us make larger and complicated stylesheets clearer to understand and easier to maintain. Thanks to features like variables,  mixins, nesting, inheritance the code is more organized, allowing us to work quicker.
Be aware that when we write in sass, browsers are not going to understand our code, because it’s not CSS we’re writing, so we need to use a compiler to compile our sass code to CSS.

-[designmodo](https://designmodo.com/introduction-sass/)

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

## SASS Project Structure

* `scss/style.scss` - The primary stylesheet. This is the file that will be compiled and will import all subsequent files.
* `scss/modules` - Reserved for scss code that does not cause sass to output CSS. Things like mixin declarations, functions, and variables.
* `scss/partials` - Where most of the meat of the scss is constructed.
* `scss/vendor` - Reserved for 3rd party CSS, such as `Normalize.css`

**For more information on file structure, check out [John W. Long's Blog](http://thesassway.com/beginner/how-to-structure-a-sass-project).**

---

## Important Notes

### SASS

Below is a list of the core features in SASS which you will see the most. Most of using SASS is just knowing CSS the other part is making CSS **DRY** (Don't Repeat Yourself).

* #### Variables <a name="variables"></a>
    A way to store information that can be reused throughout the stylesheet (anything from colors, font-weight, datatypes, etc...).
    ```sass
    $white: #fff;
    $box-size: 16px;
    ...

* #### Nesting <a name="nesting"></a>
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

* #### Partials <a name="partials"></a>
    You can create partial Sass files that contain little snippets of CSS that you can include in other Sass files. This is a great way to modularize your CSS and help keep things easier to maintain. A partial is simply a Sass file named with a leading underscore. You might name it something like `_partial.scss`. The underscore lets Sass know that the file is only a partial file and that it should not be generated into a CSS file. Sass partials are used with the `@import` directive.

* #### Extend/Inheritance <a name="extend-inheritance"></a>
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

* #### Mixins <a name="mixins"></a>
    A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. 
    ```scss
    @mixin transform($property) {
        -webkit-transform: $property;
        -ms-transform: $property;
        transform: $property;
    }

    .box { @include transform(rotate(30deg)); }
    ```

* #### Functions <a name="functions"></a>
    A function is very similar to a mixin, however the output from a function is a single value. This can be any Sass data type, including: numbers, strings, colors, booleans, or lists.
    ```scss
    @function my-calculation-function($some-number, $another-number){
        @return $some-number + $another-number
    }
    .my-module {
        padding: my-calculation-function(10px, 5px);
    }

* #### Operators  <a name="operations"></a>
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