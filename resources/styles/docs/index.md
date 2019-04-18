---
title: Project Conventions
---

## Folder Structure

As front end development has become more complicated over the years, it's important to organize code into more than two or three large files. The convention in use on this project is based on [Atomic Design](#). All front end styles are within `resources/styles/`.

Within `resources/styles/`, there are the following subdirectories:

* **docs/** - contains project specific, front end documentation (such as this.)
* **atoms/** - contains atoms, as described by Atomic Design.
* **molecules/** - contains molecules, as described by Atomic Design.
* **organisms/** - contains organisms, as described by Atomic Design.
* **templates/** - contains templates, as described by Atomic Design.
* **pages/** - contains pages, as described by Atomic Design.
* **utilities/** - contains utilities that are independent of components.

There's also a handful of Sass files within this folder itself:

* **main.scss** - This is the root file that Boilerplate compiles to **main.css**. It just contains `@import` statements.
* **variables.scss** - contains Sass variables.
* **utilities.scss** - contains Sass utilities that are too simple to define standalone.
* **base.scss** - Base styles, such as typography.
* **mixins.scss** - contains Sass mixins and functions that don't make sense to get their own folder.


## Component File Structure and Naming

### Quick Reference

* **styles/&lt;category&gt;/&lt;component-name&gt;/&lt;component-name&gt;.scss**
* **styles/&lt;category&gt;/&lt;component-name&gt;/&lt;component-name&gt;.twig**
* **styles/&lt;category&gt;/&lt;component-name&gt;/README.md**
* **styles/&lt;category&gt;/&lt;component-name&gt;/&lt;component-name&gt;[--&lt;variant-name&gt;].twig**
* **styles/&lt;category&gt;/&lt;component-name&gt;/&lt;component-name&gt;.js**
* **styles/&lt;category&gt;/&lt;component-name&gt;/&lt;component-name&gt;.config.json**

### Explanation

Components are first categorized and put in one of the following folders, based on Atomic Design principles: **utilities/**, **atoms/**, **molecules/**, **organisms/**, **templates/**, or **pages/**. [Atomic Design](http://atomicdesign.bradfrost.com/) is a methodology for breaking down and front end development into manageable, modular pieces that are easier to maintain. Boilerplate uses Atomic Design because it is useful, thought out, well documented, and has a strong community.

The notable addition to the typical Atomic Design categories is **utilities/** (although Atomic Design doesn't oppose this kind of category at all.) The **utilities/** folder is meant for utilities - code that isn't specific to a single component.

*It's okay for components to change categories during development.* Whenever you're trying to choose a category for a component, make your best guess, erring on making it smaller. For example, if you're torn between something being an atom or a molecule, start with atom.

Each component should have its own folder. These folder names should use `kebak-case`. Within that folder, a component may contain the following:

* A Sass file, with the same name as the folder, defining the styles for this component.
* A Twig file, with the same name as the folder, containing example markup for this component.
* Additional Twig files, showing additional examples markup (what [Fractal calls Variants](#)) for this component.
* A README.md, with additional, component specific documentation.
* A JavaScript file, with the same name as the folder, meant to work with the example markup to render the component. Note that this isn't meant to be the source code of a JavaScript plugin or library, but rather the code required to *use* on the example markup.
* A [Fractal configuration file](#), defining how to display this component within the pattern library.

For example, for buttons, we have the following:

* **atoms/button/**
* **atoms/button/button.scss**
* **atoms/button/button.twig**
* **atoms/button/button--disabled.twig**
* **atoms/button/button.config.json**



## Class Names

### Quick Reference

* `.componentName__elementName -modifierName`

### Explanation

Boilerplate recommends a BEM convention based on the [BEM variant ABEM](https://css-tricks.com/abem-useful-adaptation-bem/). The [BEM approach](http://getbem.com/) ensures we're using a consistent, modular naming convention that minimizes conflicts while maintaining readability and flexibility. ABEM (as well as [BEVM](https://www.slideshare.net/Jyaasa/bevm-blockelementvariation-modifier)) offers some simple enhancements over vanilla BEM:

* **Chainable modifiers** are easier to read and chain by avoiding repetition.
* Having a convention for a **namespaces** is better, even if not used for all classes.

Other conventions from BEM, ABEM and Atomic Design apply, such as:

* Use class names for selectors; avoiding using tag names or IDs.
* Atoms, Molecules, Organisms, Templates and Pages should also be "Blocks" from a BEM perspective.
* The class name for a component should be the `lowerCamelCase` version of its name.
* Components should not depend on other components/elements within a page.
* Components can contain other components as well as elements, but not elements of elements.
* Both components as well as elements can have modifiers.

ABEM and Chainable modifiers introduces the following:

* Avoid styling modifier classes without also targeting a component or element.
* Boilerplate treats the namespace prefix as optional; if you want to use them, use them, but the documentation doesn't.
* The one exception to namespace prefixes is `js-`. Boilerplate recommends that the `js-` prefix is used to denote every class that's used for targeting from JavaScript, and that these classes do not overlap with those used for styling.


## Sass Mixins and Functions

If you'd like to define sass mixins or functions, Boilerplate recommends

* Mixin and function names are in `lowerCamelCase`.
* Component specific sass mixins are defined with the component's sass file.
* Simple Sass mixins and functions can be put in the **mixins.scss** file and documented with a comment.
* Bigger Sass mixins and functions should get their own folder and Sass file within the **utilities/** folder. These mixins may also have their own example markup and README.md files within their folders.