---
layout: default
title: Conventional commits
permalink: /gitflow/commit/

---

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