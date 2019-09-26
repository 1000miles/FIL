# Read a file and write the content of that file into an output file

## Synchronous Code

```javascript

const fs = require('fs');

const textIn = fs.readFileSync("./txt/input.txt", "utf-8");
console.log(textIn);

const textOut = `This is what we know about the avocado: ${textIn}.\nCreate on ${Date.now()}`;

fs.writeFileSync("./txt/output.txt", textOut);
console.log("File written");
```

```
# output.txt
This is what we know about the avocado: The avocado 🥑 is popular in vegetarian cuisine as a substitute for meats in sandwiches and salads because of its high fat content 😄.
Create on 1569085757081
```

## Asynchronous Code

```javascript
const textIn = fs.readFile("./txt/input.txt", "utf-8", (data, err) => console.log(data))
                .then(err => console.log(`ERROR:`, err));

console.log(`Reading file...`, textIn);
```
