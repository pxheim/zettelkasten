Fowler, M. (2018). _Refactoring: Improving the Design of Existing Code_ (2nd ed.). Addison-Wesley.

[[$Bibliography]]

[[refactor-before-performance-optimization]]

[[refactor-in-small-steps]]

[[do-not-mix-refactoring-with-other-activities]]

[[the-best-time-to-refactor]]

[[do-not-tell-your-manager-about-refactoring]]

[[break-down-code-ownership]]

Consider in a team of senior developers to forgo the concept of feature branches. It makes it more complicated to do CI, and it's not needed when the code ecosystem is good.

[[comments-indicate-potential-refactors]]

Naming things in code is hard. However when it's hard to come up with a good name, it often indicates something wrong with your code as a whole. Renaming can therefore lead to larger refactors.

[[refactor-large-functions-into-small-ones]]

[[refactor-long-parameter-lists]]

Loops should be avoided and replaced by first class functions. .map, .filter, etc are much clearer and cleaner.