- [Introduction](#introduction)
- [Languages](#languages)
  - [Typescript](#typescript)
    - [Use Cases](#use-cases)
  - [CSS/SCSS](#cssscss)
    - [Use Cases](#use-cases-1)
- [Libraries](#libraries)
  - [React](#react)
    - [Use Cases](#use-cases-2)
- [Frameworks](#frameworks)
  - [Next.js](#nextjs)
    - [Use Cases](#use-cases-3)
  - [NestJS](#nestjs)
    - [Use Cases](#use-cases-4)
  - [Docusaurus](#docusaurus)
    - [Use Cases](#use-cases-5)
- [CI/CD](#cicd)
  - [GitHub Actions](#github-actions)
    - [Use Cases](#use-cases-6)
- [Cloud Platforms](#cloud-platforms)
  - [Vercel](#vercel)
    - [Use Cases](#use-cases-7)
## Introduction
This document will introduce the programming languages, frameworks, tools, and services we prefer to build and ship software with. It also provides links to tools and guides to help you implement [contribution rules](/contribution-rules.md) and a [branching strategy](/branching-strategy.md) when setting up a new project.  

Choosing the right tech stack depends on multiple factors, such as the software type, functionalities, and requirements. It's impossible to cover all possibilities, nor is it our intention. But we encourage contributors to choose their stack as close as possible to what is covered here, so that other contributors would be familiar with it. Also, this will allow us to prepare guides and tools for implementing our development workflow once and use them in multiple projects.

## Languages

### Typescript
We use javascript because its ecosystem lets us build almost any software; this is important for the reasons we explained in the [introduction](#introduction). 

Not being a type-safe language, Javascript increases the chance of runtime errors and makes it extremely hard to read and maintain the project as it or the team working on it gets bigger. We prefer Typescript over Javascript because it has solved these issues, ensuring that we deliver safer software.

#### Use Cases

### CSS/SCSS
#### Use Cases 

## Libraries
### React
#### Use Cases 

## Frameworks

### Next.js
[Next.js](https://nextjs.org/) is an open-source [React](https://reactjs.org/) framework created by [Vercel](http://vercel.com/). We build frameworks on top of it to speed up our website development process.
#### Use Cases 
- A framework that empowers Logos brands to build websites under the design system of Logos. See [here](https://github.com/acid-info/logos-site-builder).

### NestJS
#### Use Cases 

### Docusaurus
[Docusaurus](https://github.com/facebook/docusaurus) is an open-source [React](https://reactjs.org/) framework created by Facebook for building documentation websites, which supports i18n, versioning, custom pages, MDX documents, customized themes, etc.

#### Use Cases 
- Create highly customized documentation websites for Logos business units. (see [codex.storage](https://codex.storage), [here](http://github.com/acid-info/logos-documentation-website-template), and [here](https://github.com/acid-info/logos-docusaurus-plugins))

## CI/CD
### GitHub Actions
#### Use Cases

## Cloud Platforms

### Vercel
We only intend to use Vercel for demo and test cases, but we're also temporarily deploying multiple Logos brands' websites on it.

#### Use Cases 
- Quickly deploy websites for demo & test cases 
- Setup CI/CD pipelines and deploy Logos brands websites ([vac.dev](http://vac.dev/), [waku.org](https://waku.org/), [codex.storage](https://codex.storage))