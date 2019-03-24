# Notes on Go

Here are some notes about the udemy go course

## Introduction

Go was created by the same guys that helped do C, Unix, and UTF8; Robert Griesemer, Rob Pike and Ken Thompson.

The reason was that Google did not find a language that met their needs.

Purpose was to have it takes advantage of multiple cores, and parallel computing.

- efficient compilation
- efficient execution
- ease of programming

What Go is good for:

- web services at scale
- networking
  - http, tcp, udp
- concurrency / parallelism
- systems
- automation, command line tools.
- crypto
- image processing
- mobile applications
- load balancers
- ...many more...

Some features:

- procedural, modular, object-oriented, statically-typed, compiled language.
- clean syntax
- powerful standard library
- garbage colected
- it is portable
- open source
- efficient concurrency 
  - perl, ruby, js, python very bad
  - c, c++, java as good as Go

How to **succeed at learning go**.

1. Number One factor of success is grit, persistance. Train every day and work on that. *(I think high IQ does not hurt either)*

2. Time on Task. Must be able to focus and do it every day.

3. Prioritize, put first thing first. In this case, focus on learning go.

Interesting Quotes:

``` md
Look closely at the seeds you plant today, they are the crop of tomorrow.
```

``` md
If you want to be successfull get in front of what is coming and let it hit you.
```

``` md
Being a programmer is to always operate at the edge of not knowing.
```

``` md
Drop by drop, the bucket gets filled
```

## Overview

Check pinned bookmarks On Firefox. Documentation is also there.

Development can be done in <https://play.golang.org/> too.

Visual Studio seems to be the best for now, but IntelliJ has a "pro" Golang IDE that could be set.

### Go Workspace

Go has a convention for folder structureswith three directories:

``` md
.
├── bin    (holds compiled commands)
├── pkg    (holds installed package objects)
└── src    (holds the source code. Can hold github repositories)
```

### Environment variables

`$ go env` has the following output.

```bash
GOARCH="amd64"
GOBIN=""
GOCACHE="/Users/ejajimn/Library/Caches/go-build"
GOEXE=""
GOFLAGS=""
GOHOSTARCH="amd64"
GOHOSTOS="darwin"
GOOS="darwin"
GOPATH="/Users/ejajimn/go"
GOPROXY=""
GORACE=""
GOROOT="/usr/local/Cellar/go/1.12.1/libexec"
GOTMPDIR=""
GOTOOLDIR="/usr/local/Cellar/go/1.12.1/libexec/pkg/tool/darwin_amd64"
GCCGO="gccgo"
CC="clang"
CXX="clang++"
CGO_ENABLED="1"
GOMOD=""
CGO_CFLAGS="-g -O2"
CGO_CPPFLAGS=""
CGO_CXXFLAGS="-g -O2"
CGO_FFLAGS="-g -O2"
CGO_LDFLAGS="-g -O2"
PKG_CONFIG="pkg-config"
GOGCCFLAGS="-fPIC -m64 -pthread -fno-caret-diagnostics -Qunused-arguments -fmessage-length=0 -fdebug-prefix-map=/var/folders/fd/cg4t07ld0gd2dnqxyp048lk40000gn/T/go-build612109292=/tmp/go-build -gno-record-gcc-switches -fno-common"
```

### Choosing the right IDE

I use VS Code, works well, but there are many other options:

- _VS Code_
- Goland by IntelliJ
- Atom
- Sublime
- Vim

### Basic Commands in Go

`go version` current version of go (e.g. `go version go1.12.1 darwin/amd64`)

`go fmt ./...` formats the code. It prints the names of the files that are modified. On VS the code is formatted with every save.

`go help` to see list of topics.

`go help env` to get help on a specific topic.

`go env` to check the Go environment.

`go env GOPATH` is used to see the current GOPATH. GOPATH resolves import statements. For me GOPATH = /Users/ejajimn/go

**`go get`** is used to get packages from other sources. It downloads the packages named by the import paths, along with their dependencies. It then installs the named packages.

`go clean` removes object files from package source directories. The go command builds most objects in a temporary directory, so go clean is mainly concerned with object files left by other tools or by manual invocations of go build.

**`go run *.go`** compiles and runs the named main Go package.

`go install <folder>` compiles and installs the packages named by the import paths. The -i flag installs the dependencies of the named packages as well.

`go clean -i github.com/name/etc` removes the installed packages.

`go test` automates testing the packages named by the import paths. It recompiles each package along with any files with names matching
the file pattern `*_test.go`. These additional files can contain test functions, benchmark functions, and example functions. It prints a summary of the test results in the format:

``` md
    ok   archive/tar   0.011s
    FAIL archive/zip   0.022s
    ok   compress/gzip 0.033s
```

### Github general usage notes

Started to do version control on linux when they were told to pay. Linus created `git`. Github and gitlab are the most popular. It is used for social coding.`

#### Working with repos

**`git clone <url.git>`** clone an exsisting repository into a new directory.

`git init` create an empty Git repository or reinitialize an existing one.

#### Staging

`git status` shows modified files in working directory, staged for your next commit

**`git add [file]`** add a file as it looks now to your next commit (stage).

`git reset [file]` unstage a file while retaining the changes in working directory.

`git diff` diff of what is changed but not staged.

`git diff --staged` diff of what is staged but not yet committed.

**`git commit -m “[descriptive message]”`** commit your staged content as a new commit snapshot.

#### Branch & Merge

`git branch` list your branches. a * will appear next to the currently active branch.

**`git branch [branch-name]`** create a new branch at the current commit.

`git checkout` switch to another branch and check it out into your working directory.

**`git merge [branch]`** merge the specified branch’s history into the current one.

`git log` show all commits in the current branch’s history.

#### Share and Update

`git remote add [alias] [url]` add a git URL as an alias.

`git fetch [alias]` fetch down all the branches from that Git remote.

`git merge [alias]/[branch]` merge a remote branch into your current branch to bring it up to date.

**`git push [alias] [branch]`** transmit local branch commits to the remote repository branch.

**`git pull`** fetch and merge any commits from the tracking remote branch.

#### Rewrite History

`git rebase [branch]` apply any commits of current branch ahead of specified one.

`git reset --hard [commit]` clear staging area, rewrite working tree from specified commit.

#### Temporary Commits

**`git stash`** save modified and staged changes.

`git stash list` list stack-order of stashed file changes

`git stash drop` discard  the changes from top of stash stack.