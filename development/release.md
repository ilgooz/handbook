- Create a pull request with the new version and the update the `CHANGELOG.md` to `dev`
- Merge the pull requests in the `dev` branch
- Create a pull request from `dev` to `master`
- Wait for CI to finish
- Merge the pull request in the `master` branch
- Tag the `master` with the new version in the `CHANGELOG.md` file
- When the new binaries are uploaded to GitHub, update the release with the Changelog of this version
- Post a topic on the [Forum](https://forum.mesg.com)

Query to find all latest Pull Requests to build the changelog: `is:pr is:closed merged:2018-10-05..2018-11-03 base:dev` or use [github-changelog-generator](https://github.com/github-changelog-generator/github-changelog-generator).