# Guess the Output

## the below code will console.log 1-8 but the order will be dictated by the Node.JS event loop. Can you guess the order?

```js
const fs = require("fs");

setImmediate(() => console.log(1));

Promise.resolve().then(() => console.log(2));

process.nextTick(() => console.log(3));

fs.readFile(__filename, () => {
  console.log(4);
  setTimeout(() => console.log(5));
  setImmediate(() => console.log(6));
  process.nextTick(() => console.log(7));
});

console.log(8);
```

## Answer

> 8,3,2,1,4,7,6,5

## Node.JS Event Loop

### Micro-Task Queues

- Process.nextTick()

- Promises Resolve/Reject

## Main Event Loop

> Polling

The poll phase executes I/O-related callbacks. This is the phase that application code is most likely to execute in. When your main application code starts running, it runs in this phase.

> Check -

In this phase, callbacks that are triggered via setImmediate() are executed.

> close -

This phase executes callbacks that are triggered via EventEmitter close events. For example, when a net.Server TCP server closes, it emits a close event that runs a callback in this phase.

> timers -

Callbacks scheduled using setTimeout() and setInterval() are executed in this phase.

> pending -

Special system events are run in this phase, like when a net.Socket TCP socket throws an ECONNREFUSED error
