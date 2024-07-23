Large function are bad. Make smaller ones. Good way to identify where you can refactor is to look for where there are comments in the function. This usually indicates areas where code is unclear and should be moved into a separate function. Also if you find yourself wanting to add a comment, most often, make a new function instead.

If you are looking at a part of a function trying to figure out what it does, when you figure it out, refactor out that part and name it the "what".

Super small functions are fine and can sometimes make things clearer. An example is if the intent is one thing, but the implementation is something else. Like if highlighting something is done by reversing something, you might have a highlight method that just called reverse. This makes reading the code much easier.

[[comments-indicate-potential-refactors]]
