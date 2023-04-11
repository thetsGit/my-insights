
  
# **ES6 Default vs Named exports**

## Prerequisites

> You are supposed to be already familiar with [ES6 modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) and how to use them in advance because this blog is not about what is ES6 module and how to use them, but a discussion about when and why to use either ES6's named or default export. 

## Default export

Good points

- More Flexible and Simple Importing  
- Disinclination toward triggering name conflicts (not needed to use the alias keyword ‘as’)
- Cleaner syntax

Bad points

- Not optimized access (can’t import partially)  
- Not supporting tree shaking  
- Being able to be used only once per module
- Inconsistency of the imported names can lead to name confusion along with the growing code base 

## Named export

Bad points

- Tendency to trigger name conflicts across different files (which can be solved by creating a namespace using "*" and "as" keywords like `import * as foo from bar`)  
- Stricter but more standardized name imports (have to import explicitly only using the exported name or use the alias syntax "as")  
- Inhibition against refactoring in some cases

Good points

- Support  [tree shaking](https://web.dev/reduce-javascript-payloads-with-tree-shaking/#what_is_tree_shakingv)
- Optimized importing due to its partial import nature.  
- Being able to be used multiple times per module  
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

Yes! we might have multiple components in a single component file, but if we do have to export multiple components or alike (objects, functions, or else) from a single jsx or tsx file, normally, it is great to refactor our file, like extracting the frequently used components or alike to a kinda common folder or alike where they can be exported partially via [index files](https://dev.to/fahadaminshovon/-how-to-use-indexjs-fileproperly-302f).

On the other hand, named export is quite practical to be used with like constant and util files due to its supported multiple and partial exporting nature. On top of that, it is widely used to implement the ["index js" pattern.](https://dev.to/fahadaminshovon/-how-to-use-indexjs-fileproperly-302f)

*ps: good points and bad points mentioned above might sound subjective at some points, and they can presumably be different from different perspectives. And, most libraries tend to export their things in both default and named exporting ways to let the module consumer use any importing style (like both `import * from something` and `import something from something` are the same) and to diminish confusion*

