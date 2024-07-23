Fowler, M. (2018). _Refactoring: Improving the Design of Existing Code_ (2nd ed.). Addison-Wesley.

[[$Bibliography]]

[[refactor-before-performance-optimization]]

[[refactor-in-small-steps]]

[[do-not-mix-refactoring-with-other-activities]]

[[the-best-time-to-refactor]]

[[do-not-tell-your-manager-about-refactoring]]

Break down code ownership. Even though you are responsible for frontend code, does not mean you cannot make changes to the backend code. This makes life much easier if you are doing some work in frontend and need some change done in the backend. You can just do it.

Consider in a team of senior developers to forgo the concept of feature branches. It makes it more complicated to do CI, and it's not needed when the code ecosystem is good.

[[comments-indicate-potential-refactors]]

Naming things in code is hard. However when it's hard to come up with a good name, it often indicates something wrong with your code as a whole. Renaming can therefore lead to larger refactors.

Long function are bad. Make smaller ones. Good way to do it is look for where there are comments in the function. Usually indicates areas where code is unclear and should be moved into a separate function. Also if you find yourself wanting to add a comment, most often, make a new function instead.

Long parameter lists are bad. They make it hard to see what the function is supposed to do. Consider making a class when you have long parameter lists.

Loops should be avoided and replaced by first class functions. .map, .filter, etc are much clearer and cleaner.

Extract function when you are looking at code trying to figure out "what" it does. When you do, extract the method and name the function after the "what".

Super small functions are fine and can sometimes make things clearer. An example is if the intent is one thing, but the implementation is something else. Like if highlighting something is done by reversing something, you might have a highlight method that just called reverse.