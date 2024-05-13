Avoid making the class you test depend on other classes in a test. E.g. if you have a class `x` that depends on a class `y`, save from instantiating the class `y`, your tests for class `x` should not know about the details of class `y`.

This also applies to private methods that are part of class `x`. By testing the public ones, you should be able to assert that the private ones do what they are supposed to.
