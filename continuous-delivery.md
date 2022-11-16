- [Introduction](#introduction)
- [Branch Types](#branch-types)
  - [Environment Branches](#environment-branches)
  - [Feature Branches](#feature-branches)
  - [Hotfix Branches](#hotfix-branches)
- [Contribution Rules](#contribution-rules)
- [Instructions](#instructions)
  - [Create a New Feature](#create-a-new-feature)
  - [Manage Hotfixes](#manage-hotfixes)
  - [Create a Deployment](#create-a-deployment)

## Introduction
This branching strategy is based on [Gitlab Flow](https://docs.gitlab.com/ee/topics/gitlab_flow.html). We will use this strategy for projects that require continuous delivery.

## Branch Types
There are three types of branches:
- Environment
- Feature
- Hotfix

All environment branches should be protected; no one should be able to push commits directly to them.
All non-protected branches are created by developers working on specific tasks and should be deleted once merged. 

### Environment Branches
You will have two environment branches on your server:
- `main`
- `production`

Any update to the `main` branch will trigger a deployment to the staging environment, and any update to the `production` branch will trigger a deployment to the production environment. The `production` branch should never be ahead of the `main` branch.

Updates to the `main` branch should trigger a CI action to create a request for merging the `main` with the `production` branch. This merge request may contain a list of tasks for requirements such as manual testing, which should all be marked as done for the maintainer(s) to be able to accept the request.

### Feature Branches
Contributors will mainly work on feature branches. After their work is finished, they will request a merge with the `main` branch. 

```mermaid
%%{init: { 'theme': 'base', 'gitGraph': {'showCommitLabel':false,'mainBranchOrder': 1}} }%%
      gitGraph
      commit
      commit
      branch production
      branch feat-1 order: 2
      checkout feat-1
      commit
      commit
      checkout main
      merge feat-1
      checkout production
      merge main
      checkout main
```

### Hotfix Branches
A hotfix branch should be first merged with the `main` branch and then cherry-picked into `production`.

```mermaid
%%{init: { 'theme': 'base', 'gitGraph': {'showCommitLabel':false,'mainBranchOrder': 1}} }%%
      gitGraph
      commit
      commit
      branch production
      branch feat-1 order: 2
      checkout feat-1
      commit
      commit
      checkout main
      merge feat-1
      checkout production
      merge main
      checkout main
      branch feat-2 order: 3
      commit
      checkout main
      merge feat-2
      checkout production
      branch hotfix-1 order: 4
      commit
      checkout main
      merge hotfix-1
      checkout production
      merge hotfix-1
      merge main
```

## Contribution Rules
See the [contribution rules](/contribution-rules.md) document.

## Instructions

### Create a New Feature
1. Create a local branch:
```bash
$ git checkout -b feat-foo main
```

2. Push your changes to a remote branch with the same name:
```bash
$ git push origin feat-foo 
```

3. Create a merge request from your new branch to the `main` branch.

4. Delete your branch after your merge request is approved.

### Manage Hotfixes 
1. Create a local branch from the `production` branch:
```bash
$ git checkout -b hotfix-bug production
```

2. Push your changes to a remote branch with the same name:
```bash
$ git push origin hotfix-bug
```

3. Create a merge request from your hotfix branch to the `main` branch.

4. A developer with sufficient permissions may accept the request after all tests are passed and successfully deployed to the staging environment.

5. Create a merge request from your hotfix branch with the `production` branch.

6. A developer with sufficient permissions may accept the request.

7. Delete the hotfix branch on the remote repository once merged.

### Create a Deployment 
Updating the `production` and the `main` branches will trigger a deployment.
