
**exhaustMap**

Maps all values to a new observable and flattens these new observables using the `exhaust` strategy. Example:

```ts
import { fromEvent, interval } from 'rxjs';
import { exhaustMap, take } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const result = clicks.pipe(
  exhaustMap(() => interval(1000).pipe(take(5)))
);

result.subscribe(x => console.log(x));
```

When clicked, `interval` will emit every second for 5 seconds. If clicked again during t