Definition: Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.

Meaning if you have a class `Vehicle` and you have a subclass `Car`, you should be able to use `Car` everywhere your program expects `Vehicle` without causing errors.

Another good example is using `Bird`, `Sparrow` and `Ostrich`. The following would violate LSP:

```dart
class Bird {
  void fly() {
    print("Flying");
  }
}

class Ostrich extends Bird {
  @Override
  void fly() {
    throw new UnsupportedOperationException("Ostrich can't fly");
  }
}

Bird myBird = Ostrich();
myBird.fly();  // This will throw an exception
```

In order to fix this, we can create a new interface for things that can fly:

```dart
abstract class Flyable {
  void fly();
}
```

Then, we can fix the code from earlier:

```dart
class Bird {
  void makeSound() {
    print("Bird sound");
  }
}

class Sparrow extends Bird implements Flyable {
  @Override
  public void fly() {
    prnt("Sparrow flying");
  }
}

class Ostrich extends Bird {
  // Ostrich does not implement Flyable
}
```
