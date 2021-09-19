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

- Poll

> Polling -

- Check

> Check -

- Close

> close -

- Timers

> timers -

- Pending

> pending -
