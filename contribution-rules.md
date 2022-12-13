- [Introduction](#introduction)
- [Code Formatting](#code-formatting)
- [Commit Messages](#commit-messages)
- [Unit Testing](#unit-testing)
- [Documentation](#documentation)
- [Versioning](#versioning)
- [Branching](#branching)
- [Merge Requests](#merge-requests)
- [Code Review](#code-review)

## Introduction

This document contains a set of rules and principles that every contributor must follow while working on our projects. These rules apply to every project regardless of size, development stage or delivery method. Doing so will allow us to prepare tools and guides to reduce the set up time for new projects, automate release/deployment workflows, reduce communication overhead and ultimately increase productivity.

## Code Formatting
The code style across all files of the same type should be consistent. Please do not leave code formatting to the contributor or their editor. Enforce code formatting by defining a Git hook to format staged files before committing. Doing so will ease reviewing merge requests and the project's history. It is also important to stick to the conventions while configuring your code formatter.

**Setup code formatting for JS/TS projects:**
1. Install [Husky](https://typicode.github.io/husky/) for Git hooks:
  ```bash
  yarn add -D husky
  ```
2. Install [Prettier](https://www.npmjs.com/package/prettier) and [Pretty Quick](https://www.npmjs.com/package/pretty-quick) for code formatting:
  ```bash
  yarn add -D prettier pretty-quick && \ 
  npm pkg set scripts.prepare="husky install" && \
  npm pkg set scripts.prettier="pretty-quick" && \
  npm pkg set scripts.prettier:staged="pretty-quick --staged"
  ```
2. Create a hook:
  ```bash
  npx husky add .husky/pre-commit "yarn prettier:staged"
  ```
3. Create a config file for Prettier:
```bash
echo """{
  "tabWidth": 2,
  "semi": false,
  "singleQuote": true,
  "trailingComma": "all"
}""" > .prettierrc
```
## Commit Messages
**Use [conventional commit](https://www.conventionalcommits.org/en/v1.0.0/) messages:**
Writing conventional commit messages should be enforced as it is essential for automated semantic versioning. It also helps contributors to quickly understand changes the commit introduces.

**Write short meaningful commit messages that describe an atomic change:**
As a rule of thumb, reverting a commit should not result in side effects other than those expected from the commit message. 
A commit message should be short; if it describes more than one distinct change, your commit is not atomic. In this case, you need to break it into multiple commits. To provide more context, add a link to an issue on the remote server by adding `refs #[issue]` or `closes #[issue]` to the commit message.

**Tools:**
- [Commitizen](https://github.com/commitizen/cz-cli): enforce conventional commits.

## Unit Testing
**Each project should have a configured unit testing framework:**
Set up a unit testing framework when you start a new project, and create a template unit test to help and encourage contributors to write tests.

**Write unit tests for your changes in the same commit:**
It's good practice to write tests for your changes in the same commit to demonstrate they're working correctly.

## Documentation
**Update the documentation according to your changes in the same commit:**
Update the documentation **before** committing changes; this way, you won't forget to do it later. Also, it's good practice to have the documentation in sync with the code in each commit, and it will minimize potential issues when reverting changes. 

## Versioning
All of our projects will use [semantic versioning](https://semver.org/). Since we use conventional commit messages, a version could be determined at any point based on the history of commits. 

A summary from the referenced website:
> Given a version number MAJOR.MINOR.PATCH, increment the:
>
> - MAJOR version when you make incompatible API changes
> 
> - MINOR version when you add functionality in a backwards compatible manner
> 
> - PATCH version when you make backwards compatible bug fixes
>
> Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

## Branching
Branches deployed to primary predefined environments(e.g., staging, production) and the branches you will cut releases from should all be **protected**, and no one should be allowed to push to them directly.

Specify the branch type by choosing a prefix from this list:
- `topic-` for features, issues, chores
- `hotfix-` for hotfixes

## Merge Requests
**Merge only tested and successfully built changes:**
Always ensure all changes will build successfully and pass all the tests. Depending on the project's branching strategy, it might be required to run build and test scripts against all commits.

**Do NOT squash commits:**
Since we rely on conventional commits, squashing commits upon merging can break our workflow. It might also make finding the reason behind a particular change challenging. Note that it's not the maintainer's job to clean up the contributor's work history; the maintainer should ask for another pull request.

**Review the changes before merging:**
Merging should only be allowed with a review or approval from the project's maintainer(s).

## Code Review
**Ensure the changes are aligned with the contribution rules:**
It's the maintainer's responsibility to ensure all changes in a merge request are aligned with our contribution rules described in this document and the project's branching strategy.

**Ask to add missing unit tests:** 
It's the maintainer's responsibility to ensure no necessary important unit test is missing. 
