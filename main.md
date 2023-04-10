

# **ES6 Default vs named exports**

## Default export

Good points

-   Support flexible and simple importing
-   No name conflict (not needed to use the alias keyword ‘as’).

Bad points

-   Not optimized access (can’t import partially)
-   Not supporting tree shaking

  

## Named export

Bad points

-   Tend to trigger name conflicts across different files (which can be solved by creating a namespace using "*" and "as" keywords like "import * as foo from bar")
-   Strict but standardized name importing (have to import explicitly only using the exported name)

Good points

-   Support tree shaking
-   Support optimization of the import due to its partial import nature.

  

## When should we use default export ? (my perspective)

-  Use default export to export the "main" thing of the module so that it can be simply imported across other modules.

-  Use to replace "import * as foo from bar" with "import foo from bar," which supports cleaner syntax.

## With React 

In terms of React, we tend to use default exporting when it comes to component files (tsx, jsx) because it enforces the single responsibility rule, i.e., whenever we have multiple things to be exported from a single component file (jsx, tsx), it is a good time to refactor our files appropriately (note: we might have multiple components in a single component file, but if we do have to export multiple components from a single tsx file, it is great to refactor your code, like migration of the frequently used components to a common folder, it is a great way to refactor

*NOTE: Most libraries tend to export their things in both default and named exporting ways to let the module consumer use any importing style.*
