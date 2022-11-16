- [Introduction](#introduction)
- [The Problem](#the-problem)
- [Strategy Definition Document](#strategy-definition-document)
- [Strategies](#strategies)
- [Useful Links](#useful-links)

## Introduction
This document describes the problem that branching strategies should resolve, what a strategy definition document should be like, and provides links to our current defined strategies. We will continuously review and revise this document and the strategy definitions to ensure they serve their purpose. If you have any suggestions, please make a pull request, or create an issue.

## The Problem
As our projects and team grow, it becomes easier for our codebases and repositories to get messy, making the process of managing changes and delivering the software too complicated or even a nightmare. A well-defined branching strategy will help us keep things organized and consistent, avoid conflicts and increase the team's productivity as long as every contributor abides by it.

We initially planned to seek a strategy that accommodates all types of projects we currently do and may work on in the future. But after doing some research, we found that many other companies have attempted to do the same, but none of them have found a single solution. Therefore, we decided to look into the top commonly used strategies and choose the best fit for each type of project we are currently working on. Then, we adopt that strategy and may slightly change it according to our needs, but in a way that doesn't impose any unnecessary overhead on new contributors; we should try our best to keep it as close as possible to common practices.

## Strategy Definition Document
A strategy definition document should cover the following:

- Introduction
- Branch Types
- Development instructions:
  - Create a new feature
  - Manage hotfixes
  - Undo mistakes
  - Create a release
  - Create a deployment 
- Benefits and Limitations 
- Resources
  - Examples
  - CI/CD setup instruction

## Strategies
Choose a strategy based on the project's type or delivery method.

- [Release delivery](/release-delivery.md)
- [Continuous delivery](/continuous-delivery.md)


## Useful Links
- [Gitflow](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub Flow](https://githubflow.github.io/)
- [Gitlab Flow](https://docs.gitlab.com/ee/topics/gitlab_flow.html)
- [Trunk-Based Development](https://trunkbaseddevelopment.com/)
- [OneFlow](https://www.endoflineblog.com/oneflow-a-git-branching-model-and-workflow)
- [War of the Git Flows](https://dev.to/scottshipp/war-of-the-git-flows-3ec2)
