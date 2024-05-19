Make sure your code reads like well written prose. This way you can _read_ your code and understand what it does, e.g. instead of

``` ts
if (a || b || c && y) {
	x.map((y) => y + z);
}
```

``` ts
if (somethingIsTrue()) {
	doSomethingSpecial();
}
```

All your functions should read like "TO paragraphs", e.g. "to do something, we need to do something else. To do something else, we need to do something entirely different. To do something entirely different, we need to ..." This is called the stepdown rule.

The name of a function should be inversely proportional to its scope. I.e. the longer the name of a function, the more specific it is.
