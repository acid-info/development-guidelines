- [Summary](#summary)
- [Starting a New Project](#starting-a-new-project)
- [Development Workflow](#development-workflow)

## Summary 
The development process takes place after a product's functionalities and specifications are determined and the development team's requirements to begin this process are arranged. These requirements may include designs or user flows, access to third-party services, etc. The development team's first step is to decide on the software's architecture and structure and set up a development environment. Then, the implementation stage begins; how the team will plan to proceed in this stage depends on multiple factors, such as the software's delivery method, business requirements, and timeline.

The following sections will walk you through
- Initial steps for starting a new project
- Development and maintenance workflow 

## Starting a New Project
The following are the initial steps you will need to take when starting a new project. Ideally, you will follow the steps as they are described below. Still, depending on the project's timeline and other unpredictable circumstances, you might proceed differently or repeat the steps as the project's plan and its requirements change. 

**1. Software architecture:**
The team's requirements to start working on the project are arranged at this stage. The project's lead developer(s) will decide on the software architecture.

**2. Decide a tech stack:**
The project's lead developer will decide on a tech stack at this step by taking the team's experience into account but generally should try to keep it as close as possible to [our preferred stack](/technology-stack.md).

**3. Adopt a branching strategy:**
The team will adopt a branching strategy based on the software's delivery method from the [Branching Strategy](/branching-strategy.md#strategies) document.

**4. Setup a development environment:**
The project's lead developer will assign a developer who most likely has the most experience with the chosen tech stack and branching strategy to set up a development environment. The developer will prepare the project's initial code and tools and collaborates with the infrastructure team to set up the repository rules and CI/CD pipelines. 

## Development Workflow
This section only describes our development workflow abstractly; your project branching strategy may introduce some additional steps.

```mermaid
graph LR
    A(Submit Change) --> B[Perform Tests]
    --> B1{Pass}
    B1-- Yes --> C[Code Review]
    B1-- No --> A
    C--> C1{Acceptance}
    C1-- No --> C2[Request for Change] --> A
    C1-- Yes --> D[Merge]
```

**1. Submit Changes:**
Contributors will always submit their work through merge requests.

**2. Testing:**
Upon creating/updating a merge request, tests will be run against the changes to ensure they won't break anything and the software will build successfully. The request will go to the next step if all the tests are passed.

**3. Code Review:**
The project's maintainer is responsible for reviewing merge requests and ensuring all the changes are aligned with our [contribution rules](/contribution-rules.md).

**4. Release/Deploy:**
Managing releases and deployments are either automated or done manually by the project's maintainer(s) according to the project's branching strategy.
