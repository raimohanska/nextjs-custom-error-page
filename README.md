Demonstrates how Next.js custom 404 page is broken when there is a Middleware present.

In this case the middleware "does nothing", i.e. consist of

```js
export function middleware(request) {
  return NextResponse.next();
}
```

Yet, if you

```
yarn
yarn dev
```

... and navigate to http://localhost:3000/page-not-found, you'll be presented with an error.
