Do not work on performance while also doing refactoring. It's a separate activity that requires special attention. Otherwise you'll end up thinking you optimize here and there without actually being able to take into consideration how compilers, runtime and hardware works.

Know where to optimize for performance before you start, otherwise it might be useless. See  [[theory-of-constraints]]

The two hats: when programming, always either add new features or do refactoring. Never do both at the same time. Or mix any other activity for that matter.

Sometimes you don't have to, or should not, refactor at all. For example when you are not touching some code, then you don't have to, even though the code is messy. Sometimes, it's better to replace some code vs refactoring. Knowing when takes practice.
