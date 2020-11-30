# changelog-test
changelog test

# Ready
- Fork Repository
- `git flow init -d`
- `npm install`

# Trial
- `git checkout develop`
- `git flow feature start ${BRANCH}`
- Create Pull Request.
    - Add label
        - https://github.com/lerna/lerna-changelog#usage
- Merge Pull Request to develop.
- `git flow release start "v$(semver $(git tag) -i patch)"`
- `GITHUB_AUTH=${TOKEN} lerna-changelog --nextVersion="v$(semver $(git tag) -i patch)" | cat - CHANGELOG.md > CHANGELOG_TEMP.md; mv CHANGELOG_TEMP.md CHANGELOG.md`
    - `lerna-changelog` is required first tag.
- `git add CHANGELOG.md && git commit -m "Update CHANGELOG.md"`
- `git flow release finish -p -m $(GITHUB_AUTH=${TOKEN} lerna-changelog --nextVersion=v$(semver $(git tag) -i patch))`
