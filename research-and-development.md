- [Introduction](#introduction)
  - [Contribution Rules](#contribution-rules)
    - [Repository Naming](#repository-naming)
    - [Repository Access Management](#repository-access-management)
  - [Technology Stack](#technology-stack)
  - [Branching Strategy](#branching-strategy)
  - [Deployment](#deployment)

## Introduction
Follow the guidelines and rules in this document during the research and development stage of the projects. The guidelines are a limited version of the ones described in the main parts of the development guidelines — which can be ignored and are arbitrary to follow unless explicitly stated in the following sections — and they must be applied only to small R&D and exploration projects that don't require long-term development or extensive collaboration with other contributors.

### Contribution Rules

#### Repository Naming
Use `rnd` as a prefix and name the repository according to the [main contribution rules document](/contribution-rules.md#repository-naming); for instance:
- rnd-bdp-figma-rest-api-exploration
- rnd-bdp-storybook-exploration

#### Repository Access Management
All repositories **must be private** and only accessible to the members of Acid.info.

### Technology Stack
Even though programs developed in the R&D stage are not necessarily going to production, you need to keep the possibility in mind and make them as portable as possible. Therefore, your R&D project's stack must be aligned with what's described in the [main technology stack document](/technology-stack.md) depending on the case whenever possible.

The following are some instances to help you further:

- **Exploring third-party web services:**
  - Typescript is essential.
  - If a web server is needed, then NestJS would be the best choice, but a plain node or express.js server will also suffice.
  - If a web front is required, it should be created with NextJS.

### Branching Strategy
No particular branching strategy is required to be applied unless it's needed for deployments, which should be chosen according to the defined [branching strategies](/branching-strategy.md#strategies).


### Deployment
TBD.
