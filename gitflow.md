---
layout: default
permalink: /gitflow/
---

# Gitflow

Giflow is an alternative Git branching model that involves the use of feature branches and multiple primary branches. Compared to trunk-based development, Giflow has numerous, longer-lived branches and larger commits. 
Under this model, developers create a feature branch and delay merging it to the main trunk branch until the feature is complete. These long-lived feature branches require more collaboration to merge and have a higher risk of deviating from the trunk branch. They can also introduce conflicting updates.

Gitflow can be used for projects that have a scheduled release cycle and for the DevOps best practice of continuous delivery. This workflow doesn’t add any new concepts or commands beyond what’s required for the Feature Branch Workflow. Instead, it assigns very specific roles to different branches and defines how and when they should interact.
In addition to feature branches, it uses individual branches for preparing, maintaining, and recording releases. 
Of course, you also get to leverage all the benefits of the Feature Branch Workflow: pull requests, isolated experiments, and more efficient collaboration.

## Summary

The overall flow is as follow :

- A develop branch is created from master.
- A release branch is created from develop.
- Feature, Doc, Test and Build branches are created from develop.
- When a feature is complete it is merged into the develop branch.
- When the release branch is done it is merged into develop then master on release date.
- If an issue in master is detected a hotfix branch is created from master.
- Once the hotfix is complete it is merged to both develop and master.

![Gitflow](/assets/images/gitflow.png "Gitflow chart")


# Workflow

## Branches

- **master**: For production releases.
- **develop**: For next release development.
- Available branch prefixes for developers :
  - **feature**: For new feature to develop.
  - **release**: When release cycle is over. Features ready to ship are kept here. Freeing develop branch for next cycle.
  - **bugfix**: For new bug to fix.
  - **hotfix**: For production bug to fix ASAP on master branch.
  - **refactor**: To improve or update code and structure.
  - **doc**: To improve or update developer documentation.
  - **test**: To add or update unit tests or E2E tests.
  - **build**: To improve the workflow of the project.

## Feature branch

From : **develop**

Each new feature should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When a feature is complete and tested, it gets merged back into develop. Features never interact directly with master.

When a feature is way behind develop because of a long development process, merge develop into the feature branch to stay tuned.

### example

```bash
git checkout develop
git checkout -b feature/csv-export
```

## Release branch

From : **develop**

Once develop has acquired enough features for a release or a predetermined release date is approaching, you fork a release branch off of develop.

Creating this branch starts the next release cycle, so no new features can be added after this point, only bug fixes, documentation generation, and other release-oriented tasks should go in this branch.

Once it's ready to ship, the release branch gets merged into master and tagged with a version number. In addition, it should be merged back into develop, which may have progressed since the release was initiated.

Using a dedicated branch to prepare releases makes it possible for one team to polish the current release while another team continues working on features for the next release. It also creates well-defined phases of development.

### example

```bash
git checkout develop
git checkout -b release/0.1.0
```

## Bugfix branch

From : **develop**

Each new bug should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When a bugfux is complete and tested, it gets merged back into develop. Bugfixes never interact directly with master.

### example

```bash
git checkout develop
git checkout -b bugfix/#456/export-button-color
```

## Hotfix branch

From : **master**

Used to quickly patch production releases.

This is the only branch that should fork directly off of master. As soon as the fix is complete, it should be merged into both master and develop (or the current release branch), and master should be tagged with an updated version number.

Having a dedicated line of development for bug fixes lets your team address issues without interrupting the rest of the workflow or waiting for the next release cycle.

### example

```bash
git checkout master
git checkout -b hotfix/#344/wrong-email-regex
```

## Refactor branch

From : **develop**

Useful technical debt reduction, ESlint/SonarQube fix,

Each refactor should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When refactor is complete and tested, it gets merged back into develop. Tests never interact directly with master.

### example

```bash
git checkout develop
git checkout -b refactor/export-csv-class
```

## Doc branch

From : **develop**

Each documentation update should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

Doc branch is only for developer documentation in order to improve collabortation in the team.
User documentation update has to be developed in a feature branch.

When documentation is complete, it gets merged back into develop. Documentations never interact directly with master.

### example

```bash
git checkout develop
git checkout -b doc/husky-pre-commit
```

## Test branch

From : **develop**

Each test update should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When test is complete, it gets merged back into develop. Tests never interact directly with master.

### example

```bash
git checkout develop
git checkout -b test/csv-export
```

## Build branch

From : **develop**

Each build update should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When build is complete and tested, it gets merged back into develop. Builds never interact directly with master.

### example

```bash
git checkout develop
git checkout -b build/gitbranchvalidator
```


# Conventional commits

Following those rules bring great advantages to a project :

- Automatic CHANGELOGs.
- Automatic semantic version bump (based on the types of commits landed).
- Communicate the nature of changes to teammates, the public, and other stakeholders.
- Trigger build and publish processes.
- Make it easier for people to contribute to the project, by allowing them to explore a more structured commit history.

The message is structured as follows:

```
<type>([optional scope]): <description>

[optional body]

[optional footer]
```

### Types

They are based on the [Angular convention](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines) and must be one of the following:

- **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
- **ci**: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
- **docs**: Documentation only changes
- **feat**: A new feature
- **fix**: A bug fix
- **perf**: A code change that improves performance
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
- **test**: Adding missing tests or correcting existing tests
- **chore**: Changes to the build process or auxiliary tools and libraries
- **revert**: Revert a previous commit. In this case it should begin with "revert:", followed by the header of the reverted commit. In the body it should say: This reverts commit <hash>., where the hash is the SHA of the commit being reverted.

### Scope

The scope should be the name of the updated component.

### Subject

The subject contains a succinct description of the change:

- Use the imperative, present tense: "change" not "changed" nor "changes"
- Don't capitalize the first letter
- No dot (.) at the end

### Body

Just as in the subject, use the imperative, present tense: "change" not "changed" nor "changes". The body should include the motivation for the change and contrast this with previous behavior.

### Footer

The footer should contain any information about Breaking Changes and is also the place to reference GitHub issues that this commit Closes.

### Rules

A commit can contain the following structural elements :

- **Fix:** Patches a bug in your codebase (this correlates with PATCH in semantic versioning).
- **Feat:** Introduces a new feature to the codebase (this correlates with MINOR in semantic versioning).
- **Additional types** are not mandated by the conventional commits specification, and have no implicit effect in semantic versioning (unless they include a BREAKING CHANGE).
- **BREAKING CHANGE:** A commit that has a footer "BREAKING CHANGE:" introduces a breaking API change (correlating with MAJOR in semantic versioning). A BREAKING CHANGE can be part of commits of any type.
- **footers** other than "BREAKING CHANGE: <description>" may be provided and follow a convention similar to git trailer format.
- **A scope** may be provided to a commit’s type, to provide additional contextual information and is contained within parenthesis (ex : feat(parser): add ability to parse arrays).

### examples

```bash
$ git commit -am "feat(lang): added polish language"
```

```bash
$ git commit -am 'feat(config): allow provided config object to extend other configs
BREAKING CHANGE: extends key in config file is now used for extending other config files'
```

### Wizard

You can use npm and Commitizen to help you write conventional commit messages :

```bash
$ npm run commit
```

### Automation

- [Husky](https://github.com/typicode/husky) :
  Prevents bad git commit, git push with git hooks. It will stop you if your commit message is not valid.
- [Commitizen](https://github.com/commitizen/cz-cli) :
  Launch commitizen Wizard to commit your work. It will guide you to write good conventional commits easily.