# Development

[[toc]]

Please follow the following guideline for development:
[https://github.com/golang/go/wiki/CodeReviewComments](https://github.com/golang/go/wiki/CodeReviewComments)

## Setup

```bash
mkdir -p $GOPATH/src/github.com/mesg-foundation/core
cd $GOPATH/src/github.com/mesg-foundation/core
git clone https://github.com/mesg-foundation/core.git ./
```

### Install dependencies

```bash
go get -v -t -u ./...
```

### Start MESG Core

```bash
./dev-core
```

### Access MESG Core through the CLI

```bash
./dev-cli
```

## Test

### Run all tests with code coverage

```bash
env MESG_CORE_IMAGE=mesg/core:local go test -cover -v ./...
```

If you use Visual Studio Code you can add the following settings (Preference > Settings)

```json
"go.testEnvFile": "${workspaceRoot}/testenv"
```

### Debugging on OS X

```bash
xcode-select --install
go get -u github.com/derekparker/delve/cmd/dlv
```

If the debugger still doesn't work, try the following:

```bash
cd $GOPATH/src/github.com/derekparker/delve
make install
```

[Source](https://github.com/derekparker/delve/blob/master/Documentation/installation/osx/install.md)


## Feature
### Trello roadmap
### Brainstorm

## Bug
### Test to reproduce

## Review

### Validate a pull request from the community

[https://github.com/TeamPorcupine/ProjectPorcupine/wiki/How-to-Test-a-Pull-Request](https://github.com/TeamPorcupine/ProjectPorcupine/wiki/How-to-Test-a-Pull-Request)

## Merge

## Release

- Create a pull request with the new version and the update the `CHANGELOG.md` to `dev`
- Merge the pull requests in the `dev` branch
- Create a pull request from `dev` to `master`
- Wait for CI to finish
- Merge the pull request in the `master` branch
- Tag the `master` with the new version in the `CHANGELOG.md` file
- When the new binaries are uploaded to GitHub, update the release with the Changelog of this version
- Follow the [marketing process](/marketing/#software-release)

Query to find all latest Pull Requests to build the changelog: `is:pr is:closed merged:2018-10-05..2018-11-03 base:dev` or use [github-changelog-generator](https://github.com/github-changelog-generator/github-changelog-generator).