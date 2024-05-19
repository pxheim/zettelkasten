Definition: Clients should not be forced to depend on interfaces they do not use.

Instead of making large interfaces, split them where logically possible so that implementations of these interfaces only depend on the things they need to.

E.g. instead of a large interface called `Machine`, with methods `print`, `scan` and `fax`, split it up into other interfaces called `Printer`, `Scanner` and `Fax` so that a printer does not have to implement `scan` and `fax` if it does not support it.
