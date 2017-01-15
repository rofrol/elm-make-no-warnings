No warning from child if you compile second time. You need to remove `elm-stuff/build-artifacts`.

[SSSCCE](http://sscce.org/) for https://github.com/elm-lang/elm-compiler/issues/1558

```shell
$ elm-make Main.elm --warn
=================================== WARNINGS ===================================

-- unused import ------------------------------------------------- .\.\Child.elm

Module `Dict` is unused.

3| import Dict
   ^^^^^^^^^^^
Best to remove it. Don't save code quality for later!

-- missing type annotation --------------------------------------- .\.\Child.elm

Top-level value `title` does not have a type annotation.

5| title = "I am child"
   ^^^^^
I inferred the type annotation so you can copy it into your code:

title : String

Success! Compiled 39 modules.
Successfully generated index.html

$ elm-make Main.elm --warn
Success! Compiled 1 module.
Successfully generated index.html

$ rm -rf elm-stuff/build-artifacts/ && elm-make Main.elm --warn
=================================== WARNINGS ===================================

-- unused import ------------------------------------------------- .\.\Child.elm

Module `Dict` is unused.

3| import Dict
   ^^^^^^^^^^^
Best to remove it. Don't save code quality for later!

-- missing type annotation --------------------------------------- .\.\Child.elm

Top-level value `title` does not have a type annotation.

5| title = "I am child"
   ^^^^^
I inferred the type annotation so you can copy it into your code:

title : String

Success! Compiled 39 modules.
Successfully generated index.html
```
