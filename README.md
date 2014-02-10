Example Sass pattern template
=============================

This is an example of our module pattern in Sass.

    /module
    |-- module.scss
    |-- _style.scss
    |
    |-- /docs
    |   |-- module-data.yml
    |   |-- module-data.handlebars
    |
    |-- /includes
    |   |-- _module-default-vars.scss
    |   |-- _module-scaffold.scss
    |   |-- _module-utilities.scss
    |
    |--/modifiers
    |  |-- _module-color.scss
    |  |-- _module-size.scss



Exporting a CSS file.
---------------------

The example module.scss (which might be called `buttons.scss` or `grid.scss` in a real project) imports _styles.scss and exports a single CSS file which is then included in the `<head>` of a document.



Dependencies
---------------------

The `/includes` directory contains the utilities (mixins/functions) and default variables that are specific to this module. The `_module-scaffold.scss` file then imports all of the global config variables and the rest of these files together. 

These are files that do not generate styles such as the global variables, and the module’s defaults.



Styling the primary components.
-------------------------------

In the `_styles.scss` file the scaffolding styles are imported first.

Next the main components of a module are then styled beneath. Modifiers (such as colors, sizing, etc) are imported at the end of the file and can be optionally turned on or off.



Styling modifiers.
-------------------------------

Often throughout a project we’ll need to optionally style separate modifiers for color, sizing or  positioning, without contaminating the default styles. These should be contained in separate files such as `_button-color.scss`, `button-size.scss`).



Pattern libraries
-------------------------------

In `/docs` there is data about the module and example markup in a [Handlebars](http://handlebarsjs.com/) template which can then be exported for use in a pattern library.



Comments
-------------------------------

We use [a fork](https://github.com/erskinedesign/Idiomatic-SCSS-Comments-Snippets) of the Idiomatic CSS comment syntax in order to keep files consistently organised and documented.