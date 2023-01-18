- [Introduction](#introduction)
  - [Directory Structure](#directory-structure)
  - [Layouts](#layouts)
  - [Data Fetching \& State Management](#data-fetching--state-management)
    - [HOWTOs:](#howtos)
      - [HOWTO: SSR + Hookstate.js](#howto-ssr--hookstatejs)
      - [HOWTO: SSR + Rematch](#howto-ssr--rematch)

# Introduction

## Directory Structure
Use [the src directory](https://nextjs.org/docs/advanced-features/src-directory) and follow the [React Guidelines - Directory Structure](/react-guidelines.md#directory-structure).

## Layouts
Dynamically import layouts and render them in the `App` component as this prevents the layout component to lose its state upon navigation.

Set the desired layout name and properties on object properties of the page component:
```tsx
// pages/index.tsx

setLayout(HomePage, "SomeLayout", { props: { foo: 'bar' } })
```

You can then retrieve the layout component and properties in the `App` component:
```tsx
// pages/app.tsx

export default function App({ Component, pageProps }: AppProps) {
  const [Layout, layoutProps] = usePageLayout(Component)

  return (
    <Layout {...layoutProps} >
      <Component {...pageProps} />
    </Layout>
  )
}
```

## Data Fetching & State Management
Please read [React Guidelines](/react-guidelines.md#state-management) first.

### HOWTOs:

#### HOWTO: SSR + Hookstate.js
TODO.

#### HOWTO: SSR + Rematch
TODO.
