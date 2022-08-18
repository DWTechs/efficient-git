---

---

Following those rules to write your commit messages will bring great advantages to a project :

- Automatic CHANGELOGs capability.
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
- **doc**: Documentation only changes
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

### Description

The description contains the ticket id and a succinct description of the change:

- Use the imperative, present tense: "change" not "changed" nor "changes"
- Don't capitalize the first letter
- No dot use (.) at the end

### Rules

A commit can contain the following structural elements :

- **Fix:** Patches a bug in your codebase (this correlates with PATCH in semantic versioning).
- **Feat:** Introduces a new feature to the codebase (this correlates with MINOR in semantic versioning, or MAJOR in case of a BTRAKING CHANGE).
- **Additional types** are not mandated by the conventional commits specification, and have no implicit effect in semantic versioning (unless they include a BREAKING CHANGE).
- **BREAKING CHANGE:** A commit that has a "BREAKING:" introduces a breaking API change (correlating with MAJOR in semantic versioning). A BREAKING CHANGE can be part of commits of any type.
- **A scope** gives additional contextual information and is contained within parenthesis.

```bash
git commit -m "feat(lang): [#346] added polish language"
git commit -m "feat(parser): [#546] add ability to parse arrays"
git commit -m 'feat(config): [neo-118] BREAKING: allow provided config object to extend other configs
```
