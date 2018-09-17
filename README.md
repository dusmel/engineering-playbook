### What is Engineering at Andela?
***
The **Technology Department** is the engine of scale at Andela with a strategic focus on capturing data, putting things into systems and increasing productivity.

The **Engineering Team** at Andela drives the implementation and delivery of improvements to that engine, and focuses on delivering solutions faster and in a scalable way.

The **Apprenticeship Program**, owned by the Talent Development Department, is a full time, 3 month program where D0B Fellows (who have successfully completed Simulations) learn through building real products for real end users on internal or external teams. Find more about the Apprenticeship Program [here](https://github.com/andela/learning/tree/Apprenticeship-Advancement/Apprenticeships).

The **Apprenticeship Engineering Team** at Andela aims to provide meaningful and real work experience opportunities for Andela apprentices (D0Bs) while delivering technical solutions that improve our in-house processes and workflows.

### Contributing

#### Issues
Issues are always very welcome - after all, they are a big part of making our engineering processes better. Please be sure to follow the [issue template](https://github.com/andela/engineering-playbook/issues/new).

#### Pull requests
We're glad to get pull request if anything is missing or something is buggy. However, there are a couple of things you can do to make life easier for the maintainers:

- Explain the issue that your PR is solving - or link to an existing issue
- Follow the repository structure, and new sections in the corresponding folders

>**Git Conventions**
>Make sure you adhere to [our convention](https://github.com/andela/engineering-playbook/tree/master/5.%20Developing/Conventions#commit-message) for your commits and PR.
>The following is how we categorize the commits/work:
>
> - _Feature_ - a new guideline we've added (Predix, `feat:`)
> - _Fix_ - some corrections, something that was overlooked but not a new change in standards, that will be a feature too eg. typo, etc (Prefix, `fix:`)
> - _Chore_ - I think they will be rare here but could be something like formatting, re-arranging content, etc. (Prefix, `chore:`)

### Releases

This is a living document, therefore there will be continuous improvements made on it from time to time, both major and minor. Here are some of the guidelines on how to make releases for this document.

#### How to Release

- Create release notes as per the [guide here](https://help.github.com/articles/creating-releases/), you can [see previous releases here](https://github.com/andela/engineering-playbook/releases).
- See [release template here](.github/RELEASE_TEMPLATE.md).
- **Versioning:** our versioning will following the [Semantic Versioning](http://semver.org) convention:
  ```
  Given a version number MAJOR.MINOR.PATCH, increment the:

  MAJOR version when you make incompatible API changes,
  MINOR version when you add functionality in a backwards-compatible manner, and
  PATCH version when you make backwards-compatible bug fixes.
  ```
- Once the release note is created, these changes are supposed to be communicated to the teams via the major communication channels: Email (list) and Slack.

#### When to Release

- The recommended frequency for releases is **quarterly**, but this is not cast in stone.
