### Table of Content
***

1. [Introduction](#introduction)
2. [File Naming](#file-naming)
3. [Branch Naming](#branch-naming)
4. [Commit Message](#commit-message)
    1. [Message Header](#message-header)
    2. [Message Body](#message-body)
    3. [Message Footer](#message-footer)
    4. [Message Example](#message-example)
5. [Pull Request](#pull-request)
    1. [PR Title](#pr-title)
    2. [PR Description Template](#pr-description-template)
    3. [PR Example](#pr-example)
    4. [PR Etiquette](#pr-etiquette)
6. [Jira Issue](#jira-issue)
    1. [Story Issue](#story)
    2. [Bug Issue](#bug)
    3. [Task Issue](#task)
7. [Repo Readme](#repo-readme)

### Introduction
***
The following are rules guiding our coding process. Linting and prettier standards are not listed here because different projects and languages may have different formatting preferences. Each project should embed linting and prettier standards within its codebase such that linting and prettier issues are automagically resolved if engineers inadvertently attempt to commit non-compliant work.

### File Naming
***
We favour the `dot separated` + `kebab-case` convention. Files created should be named using the following format:

```
{file title}.{file subtype}.{file type}.{file extension}
```

`file title` - Indicates what the file is about. Examples include `permission-type`, `employee`, `permission`, `role`, etc.

`file subtype` - The subtype of the file. The file may be an interface of a repository. In this case, the subtype is `repository`. A file can have more than one subtype, but they must all be separated by the period [.].

`file type` - Indicates the type of the file. These could be `controller`, `dto` `service`, `repository`, `interface`, etc. A file should have only one type.

`file extension` - Denotes the extension of the file, eg, `js`, `ts`, `json`, etc.

For example, an ExampleFile controller would be broken down thus:

```
file title: example-file
file type: controller
file extension: ts
```

Giving us `example-file.controller.ts`.
NOTE that in the example above, there's no file subtype.

If a file has subtypes, all subtypes should be listed in their respective positions with the file type listed last just before the file extension. For example, an interface for ExampleFile service should be named with the following parts:

```
file title: example-file
file subtype: service
file type: interface
file extension: ts
```

Giving us `example-file.service.interface.ts`.

### Branch Naming
***
Branches created should be named using the following format:

```
{issue type}/{Jira issue ID}-{issue summary}
```

`issue type` - Indicates the context of the branch and should be one of:

- story
- bug
- task

`Jira Issue ID` - The ID of the Jira issue associated with the commit

`issue summary` - Short 2-3 words summary about what the branch contains

NOTE: The `issue type` is the same even for subtasks belonging to any of the issue types.

**Example**

```
story/DT-1048-resources-rest-endpoints
```

### Commit Message
***
A commit message consists of a **header**, a **body** and a **footer**, separated by a blank line.

Any line of the commit message cannot be longer than **100 characters!** This allows the message to be easier to read on github as well as in various git tools.
```
<issue ID><type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```
These rules are adopted from [the AngularJS commit convention](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/).

#### Message Header
***
The message header is a single line that contains succinct description of the change containing an **issue ID**, a **type**, an optional **scope** and a **subject**.

`issue ID` - this is to provide the advantage of immediately seeing the related Jira issue at the very top of the commit message. This becomes really useful when one does `git log --oneline` which doesn't show as far down to the footer of the commit message.

#####`<type>`
This describes the kind of change that this commit is providing. It also applies to subtasks belonging to any of the Jira issue types..
* story (story)
* fix (bug fix)
* docs (documentation)
* style (formatting, missing semi colons, …)
* refactor
* test (when adding missing tests)
* task (maintain)

#####`<scope>`
Scope can be anything specifying place of the commit change. For example **events**, **kafka**, **userModel**, **authorization**, **authentication**, **loginPage**, etc...

#####`<subject>`
This is a very short description of the change.
* use imperative, present tense: “change” not “changed” nor “changes”
* don't capitalize first letter
* no dot (.) at the end

#### Message Body
***
* just as in `subject` use imperative, present tense: “change” not “changed” nor “changes”
* includes motivation for the change and contrasts with previous behavior

http://365git.tumblr.com/post/3308646748/writing-git-commit-messages

http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html

#### Message Footer
***
Finished, fixed or delivered issue types should be listed on a separate line in the footer prefixed with "Finishes", "Fixes" , or "Delivers" keyword like this:
```
[(Finishes|Fixes|Delivers) JIRA_ISSUE_ID]
```

#### Message Example
***
```
DT-1048-story(kafka): implement exactly once delivery

- ensure every event published to kafka is delivered exactly once
- implement error handling for failed delivery

[Delivers DT-1048]
```

### Pull Request
***

#### PR Title
***
The PR title should be named using the following format:

```
[JIRA_ISSUE_ID] [Story description]
```

#### PR Description Template
***
The description of the PR should contain the following headings and corresponding content in Markdown format.

```md
#### Description
#### Type of change
#### How Has This Been Tested?
#### Checklist:
#### JIRA
```

#### PR Example
***
![](https://github.com/andela/engineering-playbook/blob/34ce58d365b64f8950c4b2164473f628b681657d/assets/pr-sample.png)

#### PR Etiquette
***
It is our belief that PR reviews should not negatively impact a team's ability to deliver features.
PRs that take too much time to get reviewed can hinder on a team's progress. As such, we practice the following behaviours when raising PRs:

- When I raise a PR, I specifically assign a developer or [engineering team](https://github.com/orgs/andela/teams/technology/teams) as reviewer
- When I raise a PR, I notify the reviewer(s) on Slack in a public channel
- The reviewer(s) can re-assign the PR to someone else (e.g. TTL re-assigning to a Senior Engineer)
- The reviewer(s) has a **3 hours SLA** to review the PR
- If SLA is not met, I can merge the unreviewed PR if and only if:
    - All the PR checks are passing (CircleCI, CodeClimate, Test Coverage)
    - I communicate in #technology Slack channel that I am merging an unreviewed PR
    - I immediately take ownership of fixing any issues that arise from merging the PR




### Jira Issues
***
#### Story
***
A Story issue should contain the following information

**Title:** one line describing the story

**Description:** a detailed description of the story. The description should include acceptance criteria

Example
```
Title:
As a Director of Success (DoS), I should be able to initiate a "Share with Fellows" action for engagements with "Completed" needs assessments to Fellows who are not externally placed.

Description:
* As a DoS, I should be able to select and share engagements with "Completed" Needs Assessment status
* After sharing an engagement, it shows up in the open engagement view
```

**Note:** Every story title should include the word ‘should’ as opposed to ‘can’. e.g. It’s unclear whether the story “User can delete comment” is a feature or a bug. “User should be able to delete comment” or “User should not be able to delete comment” are much clearer: the former is a feature, the latter a bug.

#### Bug
***
A Bug issue should contain the following information:

**Title:** A short description of the bug.

**Description:** What is currently happening? What should be happening?

**Steps To Reproduce:** Outline the steps to reproduce/show the bug.

**Resources:** Include screenshots and other assets to help explain/show the bug.

Example
```
Title:
Unwanted spaces should not appear between widgets.

Description:
The number of widgets showing per row is inconsistent.
When users view their dashboard, each row should contain 2 widgets per row.

Steps To Reproduce:
- Login to Skilltree dashboard.
- Some rows display unwanted spaces in between the widgets.

Resources:
Attach a screenshot of the error caused by the bug if applicable.
```

#### Task
***
A Task issue should include the following information:

**Title:** A short description of what needs to be done.

**Description:** Why is it needed? Does it help the team go faster or is it a dependency that could cause problems in the codebase if it’s not done?

**Acceptance Criteria:** These should include conditions that must be met for the chore to be accepted.

Example
```
Title:
Setup CI for user management service

Description:
Stable CI setup will make it easy to integrate our code while ensuring that all defined tests are passing per integration.

Acceptance Criteria:
Working CI integration with circle CI.
```

### Repo Readme
***
There's a lot we can do to encourage code reuse, sharing and onboarding of new team members. For instance, Every github repo should fill in the short description and website link at the top. Also, a github repository needs a proper Readme to best help out our teammates.

The belief here is that a repo should have a few defining traits to make it easy for anyone to understand it's purpose, set it up, run it's tests, and work towards contributing to it.

Each Repo's readme should follow this basic structure:

```
## Repo Name [codeclimate badge] [testing badge]

1 sentence tag line

# Description

3-5 sentences describing the code and what it's purpose is

## Documentation

List of endpoints exposed by the service

## Setup

Step by step instructions on how to get the code setup locally. This may include:

### Dependencies

List of libraries, tools, etc needed (e.g. yarn, node.js, python, etc)

### Getting Started

List of steps to get started (e.g. clone repo, submodule, .env file, etc)

### Run The Service

List of steps to run the service (e.g. docker commands)

### Microservices

List out the microservices if any that this repo uses

## Testing

Step by step instructions on how to run the tests so that the developer can be sure they've set up the code correctly

## Contribute

Any instructions needed to help others contribute to this repository

## Deployment

Step by step instructions so that the developer can understand how code gets updated
```
