All examples use the following code, with the mapping function changed:

```ts
import { fromEvent, interval } from 'rxjs';
import { exhaustMap, take } from 'rxjs/operators';

const clicks = fromEvent(document, 'click');
const result = clicks.pipe(
  mappingFunction(() => interval(1000).pipe(take(5)))
);

result.subscribe(x => console.log(x));
```

**exhaustMap**

When clicked, `interval` will emit every second for 5 seconds. If clicked again before finished, nothing will happen. 

> Think of it as the stream being too exhausted to handle new tasks.

**switchMap**

When clicked, `interval` will emit every second for 5 seconds. If clicked again before finished, the previous interval will be unsubscribed, and a new one will be subscribed to.

> Think of it like switching to a new stream immediately when a new one comes up.

**concatMap**

When clicked, `interval` will emit every second for 5 seconds. If clicked again before finished, the next stream will be "queued" and will trigger once the first one finishes.

> Think of it like concatenating the streams together in a line.

**mergeMap**

When clicked, `interval` will emit every second for 5 seconds. If clicked again before finished, the new stream will start right away and run alongside the first one.

> Think of it like merging the streams together.
