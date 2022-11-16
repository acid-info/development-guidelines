- [Introduction](#introduction)
- [Branch Types](#branch-types)
  - [Trunk Branch](#trunk-branch)
  - [Topic Branches](#topic-branches)
- [Contribution Rules](#contribution-rules)
- [Instructions](#instructions)
  - [Create a New Feature](#create-a-new-feature)
  - [Manage Hotfixes](#manage-hotfixes)
  - [Undo Mistakes](#undo-mistakes)
  - [Manage Releases](#manage-releases)
- [Limitations](#limitations)
  - [Parallel release branches are not supported.](#parallel-release-branches-are-not-supported)

## Introduction
We take a similar approach to [GitHub flow](https://githubflow.github.io/) for our projects that are delivered through releases.

## Branch Types
There are two branch types:
- trunk
- topic

### Trunk Branch
The trunk is your development branch, the only long-lived branch in your remote server. Use `main` for the name of this branch across all projects for consistency. It will contain your recent well-tested merged changes and must always be release-ready. No one is allowed to push to this branch directly.

### Topic Branches
Contributors will work on short-lived branches and push their changes to the remote server on a branch with the same name. They should then create a request for merging the branch into the trunk. The maintainer(s) may accept the request after reviewing the changes and when all the tests are passed to ensure nothing will break on the trunk branch by merging.

## Contribution Rules
You should strictly follow the [Contribution Rules document](/contribution-rules.md). 

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
We treat a hotfix the same as other topic branches; see the instruction for [creating a new feature](#create-a-new-feature).

### Undo Mistakes
TODO.

### Manage Releases 
There are two types of releases:
- pre-release
- release 

You must automate the process of creating releases and publishing them to repository servers. But triggering the release action should be done manually by the project's maintainer(s), whether by running a script locally or using CI services like GitHub Actions. 

By triggering a release, a script will:
1. Decide on a version name based on the commits history since the last release
2. Update the changelog file
3. Update the code with the new version name and the local dependencies in monorepos.
4. Run tests and build the software/packages to make sure everything works well
5. Commit changes on the trunk 
6. Create a tag off the trunk with the new version name
7. Push the trunk and the new tag to the remote repository 
8. Publish packages to repository servers.

## Limitations

### Parallel release branches are not supported.
Developing multiple versions is not supported in this strategy; as a consequence, you will not be able to release a patch for older major and minor versions, so keep in mind to avoid introducing breaking changes as far as possible.
