```js
for (let i = 0; i < 5; i++) {
  setTimeout(() => console.log(i), i * 1000);
}
```

or

```js
for (var i = 0; i < 5; i++) {
  setTimeout((capturedI) => console.log(capturedI), i * 1000, i);
}
```

or

```js
for (var i = 0; i < 5; i++) {
  ((capturedI) => setTimeout(() => console.log(capturedI), i * 1000))(i);
}
```
