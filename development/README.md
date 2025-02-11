# Development

[[toc]]

Please follow the following guidelines for development:
[https://github.com/golang/go/wiki/CodeReviewComments](https://github.com/golang/go/wiki/CodeReviewComments)

## Installations

### Engine

```bash
git clone https://github.com/mesg-foundation/engine.git
cd engine
git checkout dev
# Optional with Docker Machine
docker-machine create --driver virtualbox mesg-dev
eval $(docker-machine env mesg-dev)
# End optional
docker swarm init
docker network create --driver overlay engine --label com.docker.stack.namespace=engine

./dev
# Go get a coffee, it will take from 5min to 30min.
```

That's it, you have the MESG Engine ready and already running.

### CLI

```bash
git clone https://github.com/mesg-foundation/cli.git
cd cli
npm install
./bin/run
```

## Test

### Run all tests with code coverage

```bash
env MESG_CORE_IMAGE=mesg/engine:local go test -cover -v ./...
```

If you use Visual Studio Code you can add the following settings (Preference > Settings)

```json
"go.testEnvFile": "${workspaceRoot}/testenv"
```

#### Debugging on OS X

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


## Development

All developments should be associated with one branch and one Pull Request.

Branch should start with the type of development followed by a description of this development:
- `feature/xxx`
- `bug/xxx`
- `refactoring/xxx`
- `perf/xxx`

All new branches should be created based on the `dev` branch, not the `master`.

Make sure to follow this pattern.

::: warning
If a development is doing multiple things, refactoring, perf and feature for example, create different branches for this with different Pull Requests. Of course, these branches can depend one to another.
:::

- Feature = Forum + Pull Request
- Bug = Github Issues + Pull Request

### Feature

Every feature needs to be discussed to avoid chaos and to make sure that they are actually relevant.

#### Product roadmap

The list of all features to implement can be found on the associated [Monday Board](https://mesg.monday.com/boards/231078139).

#### Brainstorm

To brainstorm about new features you should create a [new post on the forum](https://forum.mesg.com) on the relevant category with the tag `Proposal` and details about this feature.

<img src="/proposal.png">

You can find all proposals [here](https://forum.mesg.com/tags/proposal). Also make sure that when these proposals are accepted and merged, they are resolved on the forum.

### Bug

Bugs needs to be tracked on [Github](https://github.com/mesg-foundation/core/issues/new?labels=bug&title=Describe%20your%20bug&body=How%20to%20reproduce%20it).

#### Test to reproduce

When fixing a bug, make sure you can reproduce it. The best way is to write a test that reproduces the bug and then fix the code to have the test green. This ensures that the bug is actually fixed and no regressions will occur.

## Review

When development is mature enough, you can create a Pull Request on Github (if you want early feedback on a work in progress use the **Draft** Pull Request option).

Then select the different reviewers for this Pull Request.

Try as much as possible to have Pull Requests with fast review, it's better to have 10 small Pull Requests easy to review than one big hard to review.

::: tip
If a Pull Request has too many comments or take too long to merge, that's a good sign that this Pull Request is either too big or was not planned and will probably make the team loose a lot of time, so don't be scared to put your Pull Request `onhold` or even delete it and get back to it when there is a better understanding of what should be done.
:::

#### Review a Pull Request from the community

If you want to review a Pull Request from the community you can have a look at this guide: 
[https://github.com/TeamPorcupine/ProjectPorcupine/wiki/How-to-Test-a-Pull-Request](https://github.com/TeamPorcupine/ProjectPorcupine/wiki/How-to-Test-a-Pull-Request)

## Merge

Before merging you must make sure that all criteria is valid:
- everything is green on the Pull Request
- all discussions are resolved
- merge to the dev

## Releases

### Engine

- Create a Pull Request with the new version and the update the `CHANGELOG.md` to `dev`
- Merge the previous Pull Request in the `dev` branch
- Create a Pull Request from `dev` to `master`
- Wait for CI to finish
- Merge the previous Pull Request in the `master` branch
- Tag the `master` with the latest version of the `CHANGELOG.md` file
- Check that the new docker image is uploaded to DockerHub
- Update the Github's release note with the Changelog of this version
- Follow the [publication process](/marketing/#software-release)
- Add to the changelog and the GitHub release the link to the forum's release notes

### Help

- To query all of the latest Pull Requests to build the changelog: `is:pr is:closed merged:2018-10-05..2018-11-03 base:dev` or use [github-changelog-generator](https://github.com/github-changelog-generator/github-changelog-generator).
