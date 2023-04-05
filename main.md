

# **ES6 Default vs named exports**

## Default export

Good points

-   Support Flexible and Simple importing
-   No name conflict (not needed to use the alias keyword ‘as’)

Bad points

-   Not optimized access (can’t import partially)
-   Not supporting tree shaking

  

## Named export

Bad points

-   Tend to trigger Name conflict across different files (can solve by creating namespace using “*” and “as” keywords like “import * as foo from bar”)
-   Strict but standardized name importing (have to import explicitly only using the exported name)

Good points

-   Support tree shaking
-   Support optimization of the importing due to its partial importing nature

  

## When should we use default export ? (my perspective)

-   Use default export to export the “main” thing of the module so that it can be simply imported across other modules

- Use to replace “import * as foo from bar” with “import foo from bar” which supports cleaner syntax

*NOTE: Most libraries tend to export their things in both default and named exporting ways to keep the module consumer use any importing style.*
