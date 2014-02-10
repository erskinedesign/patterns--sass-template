Example Sass pattern template
=============================

This is an example of our module pattern in SCSS.

    /module
    |-- module.scss
    |-- _style.scss
    |
    |-- /docs
    |   |-- module-data.yml
    |   |-- module-template.handlebars
    |
    |-- /includes
    |   |-- _module-default-vars.scss
    |   |-- _module-scaffold.scss
    |   |-- _module-utilities.scss
    |
    |-- /modifiers
    |   |-- _module-hierarchy.scss
    |   |-- _module-size.scss



Directory Structure
---------------------

#### `_styles.scss` partial

Exposes this module for import into another SASS file.

This is where the meat of the module's base styles should be written (module scaffolding is imported by default).

Modifiers (such as colors, sizing, etc) are imported at the end of the file and can be optionally turned on or off via default vars.

#### `module.scss`

The example `module.scss` (which might be called `buttons.scss` or `grid.scss` in a real project) imports _styles.scss and exports a single CSS file which is then included in a document `<head>`, or combined by a post-processor.

#### `/docs` directory

This directory contains files required for outputting HTML markup for documenting this module in a pattern library.

- `module-data.yml`: YAML formatted example data for templating this module in a pattern library.
- `module-template.handlebars`: [Handlebars](http://handlebarsjs.com/) template which can can be populated with data above for use in a pattern library.

#### `/includes` directory

This directory contains the utilities (mixins/functions) and default variables that are specific to this module.

Including files from this directory should **never** cause additional CSS output.  such as the global variables, and the module’s defaults.

- `_module-default-vars.scss`: This file defines sensible defaults for the module and consists of well commented variable declarations only. All variables are namespaced to `module` name. Private global variables should be avoided, but if required prefix with `_`.
- `_module-utilities.scss`: This file defines mixins and functions for the module, prefixed with the `module` name. Private mixins/fns should be prefixes with `_`. No variable declarations in global scope permitted.
- `_module-scaffold.scss`: This file provides some import sugar for the module by importing the default vars and utils above, along with the project-wide config. Do not add anything other than `@imports` to this file.


#### `/modifiers`

Often throughout a project we’ll need to optionally style separate modifiers for color, sizing or  positioning, without contaminating the default styles.

These should be contained in separate partials (e.g `_button-color.scss`, `button-size.scss`) in a `/modifiers` directory in the the root module directory, which are then `@import`ed into `_style.scss`

About this pattern template
---------------------------

This template style was developed using [a fork](https://github.com/erskinedesign/Idiomatic-SCSS-Comments-Snippets) of the Idiomatic CSS comment syntax Sublime Text package, which we use to ensure files are kept consistently organised and documented.

