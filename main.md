

  
# **ES6 Default vs Named exports (When and Why ?)**

## Prerequisites

> You are supposed to be already familiar with [ES6 modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)  and how to use them due to the fact that this blog is not about what is ES6 modules and how to use them, but rather about when and why to use either ES6’s named or default export.

## Introduction

In writing modern javascript codes, ES6 modules have been being crucial with the widespread use of javascript from building web pages to desktop and mobile apps, 2D/3D graphics and more for years.

 As a javascript developer, deciding whether to use ES6 named or default exporting can be a pain in the neck when one has no clue about the benefits and drawbacks of each before putting them to use. 

So, today, I am going to compare and contrast them objectively based on my development knowledge and experience thus far.

> For the sake of reducing verbosity, listing style is deemed to be preferable to paragraphing style.

## Default export

Good points

- More Flexible and Simple Importing style
- Disinclination toward triggering name conflicts (Also, it is not needed to use the alias keyword ‘as’)
- Cleaner syntax (apparently)

Bad points

- Not optimized access (partial importing is not supported)  
- Not supporting tree shaking  
- Being able to be used only once per module (it can be good or bad in different context)
- Inconsistency of the imported names can lead to name confusion as the code base grows

## Named export

Bad points

- Tendency to trigger name conflicts across different files (which can be solved by creating a namespace using "*" and "as" keywords like `import * as foo from bar`)  
- Stricter but more standardized name imports (have to import explicitly only using the exported name or use the alias syntax "as")  
- Inhibition against refactoring in some cases

Good points

- Support  [tree shaking](https://web.dev/reduce-javascript-payloads-with-tree-shaking/#what_is_tree_shakingv)
- Optimized importing due to its partial importing nature
- Being able to be used multiple times per module (it can be good or bad in different context)
- Standardized importing
- Better editor support (like name highlighting, and automatic renaming as the actual exported name is changed)

## When should we use default export ? (in general)

- Use default export to export the "main" thing of the module so that it can be simply imported across other modules in a relatively cleaner manner.  
- Use to replace `import * as foo from bar` with `import foo from bar`, which apparently supports cleaner syntax.  
- Generally suitable for component modules in React (jsx, tsx).
- Use when there's only one thing to be exported from a file, and to ditch the horrible syntax '{}'
- Use to easily replace commonJS "exports.default" syntax

Otherwise, named exports are apparently used due to the above-mentioned edges.

## With ReactJS

In terms of React, we tend to use default exporting when it comes to component files (tsx, jsx) because it enforces the single responsibility rule, i.e, whenever we have multiple things to be exported from a single component file (jsx, tsx), it is a good time to refactor our files appropriately. 

Yes! we might have multiple components in a single component file, but if we do have to export several items (objects, functions, or anything) from a single jsx or tsx file, normally, it is great to refactor our file, like extracting the frequently used components or alike to a kinda common folder or alike where they can be exported partially via [index files](https://dev.to/fahadaminshovon/-how-to-use-indexjs-fileproperly-302f).

On the other hand, named export is quite practical to be used with like constant and util files due to its supported multiple and partial exporting nature. On top of that, it is widely used to implement the ["index js" pattern.](https://dev.to/fahadaminshovon/-how-to-use-indexjs-fileproperly-302f)

## Conclusion


The good and bad points mentioned above might sound subjective at some points, and they can presumably be different from different perspectives. 
Moreover, I have found out that certain developers and teams solely use named exporting in building up their modern javascript products. 

In fact, most javascript libraries tend to export their things in both default and named exporting ways to let the module consumer use any importing style (like both `import * from something` and `import something from something` are the same) and to diminish extra work and confusion.

At the end of the day, I sincerely hope that this blog will help anyone new to ES6 modules in making sense of it, as well as those who are already familiar with it.

*Respectfully,
Thet han
#11th April 2023*



