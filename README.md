# Git Style Guide

## Branches

```text
master - "production" environment
|_ develop - "preproduction" (test) environment
  |_ release/0.1.0 - "development" environment
    |_ NP-1 - "local" environment
```

All mergings must be made via pull requests!

### Hotfix

```text
master
|_ hotfix/0.1.1 - no environment
  |_ NP-2 - "local" environment
```

## Commits

- build: Build related changes (eg: npm related/ adding external dependencies)
- chore: A code change that external user won't see (eg: change to .gitignore file or .prettierrc file)
- feat: A new feature
- fix: A bug fix
- docs: Documentation related changes
- refactor: A code that neither fix bug nor adds a feature. (eg: You can use this when there is semantic changes like renaming a variable/ function name)
- perf: A code that improves performance
- style: A code that is related to styling
- test: Adding new test or making changes to existing test

It's preffered to use special tools like [Commitizen CLI](https://github.com/commitizen/cz-cli). But if you want to create commits manually there is an example:

```bash
[NP-1] feat: add method to calc orders count
```

### Examples

[Angular](https://github.com/angular/angular/commits/master)

### References

[Conventional commits](https://www.conventionalcommits.org/en/v1.0.0)

[Commitizen - tool for commits](https://commitizen-tools.github.io/commitizen)

## Releases

x.y.z - 1.1.1

```text
x - major - 1.0.0 - Changes that break backward compatibility
y - minor - 0.1.0 - Backward compatible new features
z - hotfix - 0.0.1 - Backward compatible bug fixes
```

### References

[About semantic versioning](https://docs.npmjs.com/about-semantic-versioning)

## Release managment

After merging `develop` into `master` release tag must be created.

### Release tags

For example you need to create a tag `v1.1.1`. Don't forget prefix `v`.

```bash
git checkout master
git pull
git tag v1.1.1 {{commit}}
git push --tags
```

Or create the tag using UI and then:

```bash
git pull --tags
```

### After merging into master

Refresh `develop`:

```bash
git checkout master
git pull
git checkout develop
git merge master
git push
```

Refresh next `release` (if exists):

```bash
git checkout develop
git pull
git checkout release/0.2.0
git merge release/0.2.0
git push
```

Refresh dev branch `NP-3` (if exists):

```bash
git checkout release/0.2.0
git pull
git checkout NP-3
git rebase origin/release/0.2.0 # or merge
git push -f
```
