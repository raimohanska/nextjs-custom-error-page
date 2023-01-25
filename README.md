Demonstrates how Next.js custom 404 page is broken when there is a Middleware present.

In this case the middleware "does nothing", i.e. consist of

```js
export function middleware(request) {
  return NextResponse.next();
}
```

## How the problem manifests

Yet, if you

```
yarn
yarn dev
```

... and navigate to http://localhost:3000/page-not-found, you'll be presented with an error `Error: Invariant: attempted to hard navigate to the same URL /page-not-found http://localhost:3000/page-not-found`.

## How the problem manifests

Yet, if you

```
yarn
yarn build && yarn start
```

... and navigate to http://localhost:3000/page-not-found, you can see that the custom 404 page was rendered with missing static props.

Very bad.

## My other application

In my _actual application_ which is not open-source and is a bit more involved as you might guess, the problem looks a bit different.

- When running `yarn dev` the 404 page keeps constantly reloading in the browser
- When running `yarn build && yarn start` the 404 page is fine - except it was rendered without the `getStaticProps`

I hope though that this repository serves to demostrate that something is definitely wrong with Next.js 13.1.5.
