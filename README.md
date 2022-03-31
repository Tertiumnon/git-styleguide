# Git Styleguide

## Branches

`master` - "production" environment
|_ `develop` - "preproduction" (test) environment
  |_ `release/0.1.0` - "development" environment
    |_ `NP-1` - "local" environment
    
All mergings must be made via pull requests.

## Releases

x.y.z - 1.1.1

x - major - 1.0.0 - Changes that break backward compatibility
y - minor - 0.1.0 - Backward compatible new features
z - hotfix - 0.0.1 - Backward compatible bug fixes

### References

[About semantic versioning](https://docs.npmjs.com/about-semantic-versioning)

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

### References

[Conventional commits](https://www.conventionalcommits.org/en/v1.0.0)

[Commitizen - tool for commits](https://commitizen-tools.github.io/commitizen)

## Release tags (release management)

Create a tag after merging `develop` into `master` branch. For example you need to create a tag `v1.1.1`.

Only release engineer can create tags.

```bash
git checkout master
git pull
git tag v1.1.1 {{commit}}
git push --tags
```

Or create the tag using UI.
