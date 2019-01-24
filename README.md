# SCSS Demo

---

## Instructions

1. Install using npm
    ```bash
    npm install -g sass
    ```
2. Compile the SASS files into CSS which could be used in a webpage.
    ```bash
    sass sass/styles.scs css/main.css
    ```

**For documentation on SASS/SCSS visit the [Documentation](https://sass-lang.com).**

---

## SASS Structure

* `scss/style.scss` - The primary stylesheet. This is the file that will be compiled and will import all subsequent files.
* `scss/modules` - Reserved for scss code that does not cause sass to output CSS. Things like mixin declarations, functions, and variables.
* `scss/partials` - Where most of the eat of the scss is constructed.
* `scss/vendor` - Reserved for 3rd party CSS, such as `Normalize.css`

**For more information on file structure, check out [John W. Long's Blog](http://thesassway.com/beginner/how-to-structure-a-sass-project)**

---