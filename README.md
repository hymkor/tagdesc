TagDesc
=======

An emurator of `git describe --tags` on the DVCS [Jujutsu](https://martinvonz.github.io/jj/) ( [github.com/martinvonz/jj](https://github.com/martinvonz/jj) )

It reads and parses the output of `jj log --no-graph -r "latest(tags())::"`

PowerShell version
------------------

Copy tagdesc.ps1 to your work directory and write On Makefile(GNU):

```
VERSION:=$(shell powershell -noprofile -ex unrestricted -file tagdesc.ps1)
```

#### Example

```
$ cd ../gmnlisp.git/
$ tagdesc.ps1
v0.4.1-19-gfd091d1
$ cd ../gmnlisp.jj/
$ tagdesc.ps1
v0.4.1-19-mwlxturo
```

+ `gmnlisp.git` is the directory managed by Git.
+ `gmnlisp.jj` is the directory managed by Jujutsu.

Go version
----------

Copy tagdesc.go to your work directory and write the following line on Makefile(GNU):

```
VERSION:=$(shell go run tagdesc.go)
```

`tagdesc.go` is ignored by `go build` because `tagdesc.go` has the header `//go:build run` .

### Example

```
$ cd ../gmnlisp.git/
$ git describe --tags
v0.4.1-19-gfd091d1
$ go run ../tagdesc/tagdesc.go
v0.4.1-19-gfd091d1
$ cd ../gmnlisp.jj
$ go run ../tagdesc/tagdesc.go
v0.4.1-19-mwlxturo
```

+ `gmnlisp.git` is the directory managed by Git.
+ `gmnlisp.jj` is the directory managed by Jujutsu.
