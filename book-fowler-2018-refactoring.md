Fowler, M. (2018). _Refactoring: Improving the Design of Existing Code_ (2nd ed.). Addison-Wesley.

[[$Bibliography]]

[[refactor-before-performance-optimization]]

Refactoring should be done in small steps. Very small. Then after every change, compile, test and commit your changes. It's a rhythm you should get into. You might be surprised by how small changes are to be done. Always leave your code in a working state. That way you can stop at any time.

The two hats. When programming, always either add new features or do refactoring. Never do both at the same time.

The best time to refactor is before you add a new feature or before you fix a bug. This is often called preparatory refactoring. You often see a better way of adding something that can be done by refactoring, so you should. Similarly, comprehension refactoring is similar, but is done for you to understand better what the code does, most likely before adding something new.

If you have a manager that understands technology, refactoring should be welcome by him / her. If, however, your manager is a product person, you might be better off not mentioning refactoring and just doing it instead. You are a professional after all, paid to do a good job.

Sometimes you don't have to, or should not, refactor. For example when you are not touching some code, then you don't have to, even though the code is messy. Sometimes, it's better to replace some code vs refactoring. Knowing when takes practice.

Break down code ownership. Even though you are responsible for frontend code, does not mean you cannot make changes to the backend code. This makes life much easier if you are doing some work in frontend and need some change done in the backend. You can just do it.

Consider in a team of senior developers to forgo the concept of feature branches. It makes it more complicated to do CI, and it's not needed when the code ecosystem is good.

Do not fix performance while also fixing other things. It's a separate activity that requires special attention. Otherwise you'll end up thinking you optimize here and there without actually taking or being able to take into consideration how compilers, runtime and hardware works. Know where to optimize before you start.

Naming things in code is hard. However when it's hard to come up with a good name, it often indicates something wrong with your code as a whole. Renaming can therefore lead to larger refactors.

Long function are bad. Make smaller ones. Good way to do it is look for where there are comments in the function. Usually indicates areas where code is unclear and should be moved into a separate function. Also if you find yourself wanting to add a comment, most often, make a new function instead.

Long parameter lists are bad. They make it hard to see what the function is supposed to do. Consider making a class when you have long parameter lists.

Loops should be avoided and replaced by first class functions. .map, .filter, etc are much clearer and cleaner.

Extract function when you are looking at code trying to figure out "what" it does. When you do, extract the method and name the function after the "what".

Super small functions are fine and can sometimes make things clearer. An example is if the intent is one thing, but the implementation is something else. Like if highlighting something is done by reversing something, you might have a highlight method that just called reverse.