- [Introduction](#introduction)
- [Code Formatting](#code-formatting)
- [Unit Test](#unit-test)
- [Commits](#commits)
- [Versioning](#versioning)
- [Branching](#branching)
- [Merge Requests](#merge-requests)

## Introduction

This document contains a set of rules and principles that every contributor has to follow while working on our projects. These rules apply to every project regardless of size, development stage, or delivery method. Doing this will allow us to prepare tools and guides to reduce the time to set up new projects, automate release/deployment workflow, reduce communication overhead, and ultimately increase productivity.

## Code Formatting
The code style across all files of the same type should be consistent. Please do not leave the code formatting to the contributor or their editor. Enforce code formatting by defining a Git hook to format staged files before committing. Doing this will ease reviewing merge requests and the project's history. Another important thing is to stick with the conventions while configuring your code formatter.

**For our preferred tech stack:**
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

## Unit Test
TODO.

## Commits
General rules and principles regarding commits:
- **Use [conventional commit](https://www.conventionalcommits.org/en/v1.0.0/) messages**:
  Enforce conventional commit messages as it is essential for automated semantic versioning. It also helps to understand what's changed by the commit quickly.
- **Short meaningful commit messages that describe an atomic change**:
  As a rule of thumb, reverting a commit should not result in side effects other than what you'd expect from the commit message. 
  A commit message should be short; if it describes more than one distinct change, your commit is not atomic. In this case, you need to break it into multiple commits. To provide more context, add a link to an issue on the remote server by adding `refs #[issue]` or `closes #[issue]` to the commit message.
- **Each commit should contain tests**:
  It's good practice to write tests for your changes in the same commit to demonstrate they're working properly. 
- **Each commit should contain the updated documentation**
  Update the documentation before committing your changes; this way, you won't forget to do it later. Also, it's good to have the documentation in sync with the codes in each commit, and it will prevent causing extra troubles when reverting changes. 

## Versioning
All of our projects will use [semantic versioning](https://semver.org/). Since we use conventional commit messages, a version could be determined at any point based on the history of commits. 

A summary from the referenced website:
> Given a version number MAJOR.MINOR.PATCH, increment the:
>
> MAJOR version when you make incompatible API changes
> MINOR version when you add functionality in a backwards compatible manner
> PATCH version when you make backwards compatible bug fixes
>
> Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

## Branching
Branches deployed to primary pre-defined environments(e.g., staging, production) and the branches you will cut releases from should all be **protected**, and no one should be allowed to push to them directly.

Specify the branch type by choosing a prefix from this list:
- `topic-` for features, issues, chores
- `hotfix-` for hotfixes

## Merge Requests
**Merge only tested and successfully built changes**: 
Always ensure all changes will build successfully and pass all the tests. Depending on the project's branching strategy, it might be required to run build and test scripts against all commits.

**Review the changes before merging**: 
Merging shouldn't be allowed without at least one review by the project's maintainer(s).
