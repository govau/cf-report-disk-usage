# cf-report-disk-usage

CloudFoundry CLI plugin report on disk usage vs requested in a CloudFoundry installation

## Usage

```bash
cf report-disk-usage
```

## Development

```bash
dep ensure
go install . && \
    cf install-plugin $GOPATH/bin/cf-report-disk-usage-f && \
    cf report-disk-usage
```

## Building a new release

```bash
PLUGIN_PATH=$GOPATH/src/github.com/govau/cf-report-disk-usage
PLUGIN_NAME=$(basename $PLUGIN_PATH)

GOOS=linux GOARCH=amd64 go build -o ${PLUGIN_NAME}.linux64 main-report-disk-usage.go
GOOS=linux GOARCH=386 go build -o ${PLUGIN_NAME}.linux32 main-report-disk-usage.go
GOOS=windows GOARCH=amd64 go build -o ${PLUGIN_NAME}.win64 main-report-disk-usage.go
GOOS=windows GOARCH=386 go build -o ${PLUGIN_NAME}.win32 main-report-disk-usage.go
GOOS=darwin GOARCH=amd64 go build -o ${PLUGIN_NAME}.osx main-report-disk-usage.go

shasum -a 1 ${PLUGIN_NAME}.*
```
