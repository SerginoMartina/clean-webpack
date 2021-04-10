# Styleguide structure

## Preface
This document exists as a short explanation why certain decisions were taken

## Directories represent styleguide sections
Every root directory e.g. `typography` corresponds to a part of a styleguide:

* brand-element
* button
* corner-radius
* grid
* color
* icon
* normalize
* shadow
* spacing
* theme
* typography
* underlay

## Styleguide sections
All styleguide sections are structured in the following way:
(explained using `typography` as an example)
* `_typography-factory.scss`: contains the generator mixins for the styleguide section, and may **never output actual css** by including it.
* `_typography-variables.scss`: contains the default variables being used by the styleguide section generator.
* `_typography.scss`: is the file responsible for calling the factory **outputing css** for this styleguide section.

The Factory and Variables file is optional, if the content would be empty.

The variable files of the styleguide are all defaults: !default;
The override variable files per brand are never specifying the !default flag.

## Using third party mixins

Every component need to access the styleguide factories to access third party mixins.
Components cannot directly import a bootstrap mixin file from the node_modules folder for instance.
Our own factory work as a proxy in that case.

## Grid

We opted to both implement the AEM grid and Bootstrap 4 grid. The AEM grid facilitates the layout functions within
the authoring experience in AEM. The Bootstrap 4 grid has been implemented to use in our own components.

## Mixins

Mixins starting with the word `generate` are considered private, and shouldn't be used in components.
Instead, use an existing shortcut from within the styleguide section you're looking for, or create one 
in the `_<styleguide-section>.scss` file relevant to your needs.