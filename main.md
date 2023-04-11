
  
# **ES6 Default vs Named exports**

## Default export

Good points

- More Flexible and Simple Importing  
- Disinclination toward triggering name conflicts (not needed to use the alias keyword ‘as’)
- Cleaner syntax

Bad points

- Not optimized access (can’t import partially)  
- Not supporting tree shaking  
- Being able to be used only once in a module

## Named export

Bad points

- Tendency to trigger name conflicts across different files (which can be solved by creating a namespace using "*" and "as" keywords like `import * as foo from bar`)  
- Stricter but more standardized name imports (have to import explicitly only using the exported name or use the alias syntax "as")  
- Inhibition against refactoring in some cases

Good points

- Support tree shaking  
- Support optimization of the import due to its partial import nature.  
- Being able to be used multiple times in a module  
- More standardized importing

## When should we use default export ? (my perspective)

- Use default export to export the "main" thing of the module so that it can be simply imported across other modules in a relatively cleaner way.  
- Use to replace `import * as foo from bar` with `import foo from bar`, which apparently supports cleaner syntax.  
- Generally suitable for component modules in React (jsx, tsx).

## With React

In terms of React, we tend to use default exporting when it comes to component files (tsx, jsx) because it enforces the single responsibility rule, i.e., whenever we have multiple things to be exported from a single component file (jsx, tsx), it is a good time to refactor our files appropriately 
*(note: we might have multiple components in a single component file, but if we do have to export multiple components or things from a single tsx file, normally it is great to refactor our file, like extracting the frequently used components or alike to a kinda common folder or alike where they can be exported partially via index files.)*

*ps: good points and bad points are determined objectively, and they can presumably be different from different perspectives. And, most libraries tend to export their things in both default and named exporting ways to let the module consumer use any importing style (like both `import * from something` and `import something from something` are the same)*
