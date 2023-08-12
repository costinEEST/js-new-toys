- https://github.com/supabase-community/vercel-ai-chatbot/blob/main/lib/utils.ts#L14

- The [`URL`](https://developer.mozilla.org/en-US/docs/Web/API/URL/port) constructor function, strips the default port even if it’s explicitly provided:

```js
const { port } = new URL("http://localhost:80"); // ""
```
