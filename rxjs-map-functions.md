For each mapping function shown here, the following example code is used and `MAP` is replaced with the respective mapping function.

```ts
import { fromEvent, interval } from 'rxjs';
import { exhaustMap, take } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const result = clicks.pipe(
  MAPPING_FUNCTION(() => interval(1000).pipe(take(5)))
);

result.subscribe(x => console.log(x));
```

**exhaustMap**

Maps all values to a new observable and flattens these new observables using the `exhaust` strategy.



