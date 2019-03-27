## Development

Please follow the following guideline for development:
https://github.com/golang/go/wiki/CodeReviewComments

```
mkdir -p $GOPATH/src/github.com/mesg-foundation/core
cd $GOPATH/src/github.com/mesg-foundation/core
git clone https://github.com/mesg-foundation/core.git ./
```
### Install dependencies
```
go get -v -t -u ./...
```
### Start MESG Core
```
./dev-core
```
### Access MESG Core through the CLI
```
./dev-cli
```

## Test

### Run all tests with code coverage
```
env MESG_CORE_IMAGE=mesg/core:local go test -cover -v ./...
```

If you use Visual Studio Code you can add the following settings (Preference > Settings)

```
"go.testEnvFile": "${workspaceRoot}/testenv"
```

### Debugging on OS X
```
xcode-select --install
go get -u github.com/derekparker/delve/cmd/dlv
```

If the debugger still doesn't work, try the following:

```
cd $GOPATH/src/github.com/derekparker/delve
make install
```

[Source](https://github.com/derekparker/delve/blob/master/Documentation/installation/osx/install.md)


## Review

### Validate a pull request from the community

https://github.com/TeamPorcupine/ProjectPorcupine/wiki/How-to-Test-a-Pull-Request

## Merge