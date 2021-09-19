# Answer

```md
8
3
2
1
4
7
6
5
```

```js
    const fs = require("fs");

4.    setImmediate(() => console.log(1));

3.    Promise.resolve().then(() => console.log(2));

2.    process.nextTick(() => console.log(3));

    fs.readFile(__filename, () => {
5.      console.log(4);
8.      setTimeout(() => console.log(5));
7.      setImmediate(() => console.log(6));
6.      process.nextTick(() => console.log(7));
    });

1.    console.log(8);
```
