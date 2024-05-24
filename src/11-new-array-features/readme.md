- https://www.freecodecamp.org/news/how-to-create-a-javascript-utility-library-like-lodash
- [Convert from `Base64` to `byte array`](https://stackoverflow.com/questions/21797299/convert-base64-string-to-arraybuffer):

```js
function base64ToArrayBuffer(base64) {
  // Solution 1
  const binaryString = atob(base64);
  const bytes = new Uint8Array(binaryString.length);

  for (let i = 0; i < binaryString.length; i++) {
    bytes[i] = binaryString.charCodeAt(i);
  }

  return bytes.buffer;
}

function base64ToArrayBuffer2(base64) {
  // Solution 2
  return Uint8Array.from(atob(base64), (c) => c.charCodeAt(0)).buffer;
}

// Benchmark function
function benchmark(func, base64, iterations) {
  const start = performance.now();

  for (let i = 0; i < iterations; i++) {
    func(base64);
  }

  const end = performance.now();

  return end - start;
}

const base64Sample = "SGVsbG8gd29ybGQ="; // "Hello world" in base64
const iterations = 100000;

const time1 = benchmark(base64ToArrayBuffer, base64Sample, iterations);
const time2 = benchmark(base64ToArrayBuffer2, base64Sample, iterations);

console.log(`Solution 1 took: ${time1} ms`);
console.log(`Solution 2 took: ${time2} ms`);

if (time1 < time2) {
  console.log("Solution 1 is faster.");
} else if (time1 > time2) {
  console.log("Solution 2 is faster.");
} else {
  console.log("Both solutions are roughly the same speed.");
}

// Solution 1 is faster
```
