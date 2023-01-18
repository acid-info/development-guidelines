- [Introduction](#introduction)
  - [Directory Structure](#directory-structure)
    - [Common Structure](#common-structure)
      - [:file\_folder: components/](#file_folder-components)
      - [:file\_folder: containers/](#file_folder-containers)
      - [:file\_folder: layouts/](#file_folder-layouts)
      - [:file\_folder: styles/](#file_folder-styles)
      - [:file\_folder: types/](#file_folder-types)
      - [:file\_folder: lib/](#file_folder-lib)
      - [:file\_folder: utils/](#file_folder-utils)
    - [Modules](#modules)
  - [Data Fetching](#data-fetching)
  - [State Management](#state-management)

# Introduction

## Directory Structure
We categorize files based on the type of functionality they provide. We group them into directories at the root of the source code directory on the project/module level(e.g., /src/\*, /src/modules/some-module/\*). 

We separate code files into 7 directories common across all of our React projects: **containers, components, layouts, styles, types, lib, and utils**. You may also have other categories defined within your project's scope(e.g., pages, stores, configs, constants, data, and models.)

In the following section, we'll explain the aforementioned common categories in detail.

### Common Structure 

#### :file_folder: components/
Components are reusable and styled React components agnostic to the project's data structure. They must not make any API calls or directly read query responses; instead, data and the callbacks needed by a component must be passed down by a parent component. The only global state or variables they may access are provided for styling purposes.

:heavy_check_mark: **What a component can DO:**
- Render other components.
- Access theme and CSS variables.
- Use utility functions and hooks.

:x: **What a component can NOT do:**
- Access global states.
- Render containers. 
- Make network calls.

Place a component file inside a directory with the same name as the component in PascalCase. Then, create an index file inside that directory and export the component and its property type:

```html
├── components
|   ...
│   ├──Button 
│   │   └── index.ts # exports { Button, ButtonProps }
│   │   ├── Button.tsx # exports { Button, ButtonProps }
│   │   ├── Button.module.scss
|   ...
```

#### :file_folder: containers/
Containers are used to provide global states and APIs through React contexts. They may render a composition of components or other containers, and are responsible for handling state logic, making network requests, etc. There's no restriction on containers having styles and providing layout.

:heavy_check_mark: **What a container can DO:**
- Anything a component can do.
- Render other containers.
- Read, modify, and provide global states.
- Make network calls.

:x: **What a container can NOT do:** Nil.

The structure of `containers` directory is the same as that of `components` directory.

```html
├── containers
|   ...
│   ├── LoginPage
│   │   └── index.ts # exports { LoginPage, LoginPageProps }
│   │   ├── LoginPage.tsx # exports { LoginPage, LoginPageProps }
│   │   ├── LoginPage.module.scss
|   ...
```

#### :file_folder: layouts/ 
Layouts are React components in which pages will be rendered. Layout components must be rendered by and registered in the same top-level component that renders pages.

The directory structure is similar to the `components` and the `containers`, except the name of the file containing the layout component, must consist of the name of the layout — not the component — followed by a `.layout<.ext>` suffix; like:

```html
├── layouts 
│   ├── DefaultLayout
│   │   └── index.ts # exports { DefaultLayout, DefaultLayoutProps }
│   │   ├── Default.layout.tsx # exports { DefaultLayout, DefaultLayoutProps }
│   │   ├── DefaultLayout.module.scss
│   ...
```

#### :file_folder: styles/
Files living in the styles directory contain global styles, variable definitions, and utility functions.

Below is an example of the `styles` directory:

```html
├── styles 
│   ├── _animate.scss # Contains CSS animation mixins. 
│   ├── global.scss # Contains global styles. 
│   ├── _utils.scss # Contains common SCSS utility mixins(e.g., responsive, typography, etc.) 
│   ├── _vars.scss # Contains SCSS variable definitions such as breakpoints, font sizes, etc.
|   ├── ...
```

#### :file_folder: types/
A type file contains custom local Typescript type declarations for the project/module. The declarations are mostly derived from external types — like custom query results — and will be used mostly by the containers. 

The declarations must be defined within a Typescript namespace, and the name of the namespace must be the same as the file's name in PascalCase followed by a `Types` suffix.

A type's file name is defined in camelCase with a `.types` suffix followed by the file's extension. Below is an example of the `types` directory:

```html
├── types 
│   ├── auth.types.ts # exports { AuthTypes } 
│   ├── product.types.ts # exports { ProductTypes } 
|   ├── ...
```

#### :file_folder: lib/
The `lib` folder contains the project's or the module's local libraries, like API clients, queries, workers, i18n, database connectors, etc.

#### :file_folder: utils/
Utilities are mainly small functions and are decoupled from and agnostic to the project's data structure and should be portable to other projects with minimum effort. In most cases, they're React hooks(e.g., `useWindowSize`, `useElementSize`, `useTranslator`, `useFileInput`, etc).

Below is an example of the `utils` directory:

```html
├── types 
│   ├── fileInput.utils.ts
│   ├── useBlockRouteChange.util.ts
│   ├── useDisableScrollbar.util.ts
│   ├── useFileInput.util.ts
│   ├── useWindowSize.util.ts
│   ... 
```

### Modules
As in big projects, the root directories can get easily bloated and messy, and thus, hard to read and develop, we break the project into multiple modules based on features, with each module having the common structure described in the previous section(having directories like `containers`, `components`, `styles`, etc.) A module named `common` will contain the project's shared code like basic components, hooks, API client, etc.

In addition, we use Typescript alias paths for shorter and a more clear import statements:
```ts
// SomeComponent.tsx
import { Button } from '@common/components/Button'
```
```json
// tsconfig.json
{
  "compilerOptions": {
    "paths": {
      "@common/*": ["./src/modules/common/*"],
    }
  }
}
```

----

## Data Fetching
We use [React Query](https://react-query-v3.tanstack.com/) for client-side data fetching.

----

## State Management
We use [Hookstate.js](https://hookstate.js.org/docs/getting-started) — and in some cases together with React context — to manage global states, as it's very minimal and yet it comes with a powerful and flexible API. Additionally, we use it when a component involves dealing with a large state, as Hookstate empowers Proxies to track nested state changes to ensure only necessary components will rerender (Read more [here](https://hookstate.js.org/docs/scoped-state)). However, in the cases of complex and heavily event-driven applications, we use [Rematch](https://rematchjs.org/docs/) with [Redux-Saga](https://redux-saga.js.org/) as an alternative solution.
