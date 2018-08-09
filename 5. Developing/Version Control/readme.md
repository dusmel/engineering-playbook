# Version Control

>We always use source code control. It's like a time machine. We can work in parallel universes of our source code, experimenting without fear of losing work, rolling back if something goes wrong.

We use [Git](https://git-scm.com/) as our defacto software versioning system (SVS), and [Github](https://github.com) for our hosting.

## Git Workflow

We use [Gitflow Workflow as documented here](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow), with [our own conventions](../Conventions) on branch naming, commit messages and PR format.

## Advanced Git Features

> TBD - this is work in progress, submit a PR for suggestions on this

Our guidelines around:

- `Pre-commit` hooks
- When and how to `rebase` feature branch
- Release management (release branches, etc)
- [Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
- When and how to [`cherry-pick`](https://git-scm.com/docs/git-cherry-pick)

## Github - Pivotal Tracker Integration

We use Pivotal Tracker (PT) as our defacto project management tool. It has a very nice integration with Github [that is explained in detail here](https://www.pivotaltracker.com/integrations/GitHub/). With this, you can:

- Automatically attach pull requests, branches, and commits to a PT story.
- You can still connect one PT board to multiple repositories. Very useful especially when working with n-tier and microservice architectures where one project will have multiple repos.
