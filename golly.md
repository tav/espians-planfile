---
id: golly
tags: TODO, #go
title: Golly
---

The various Go libraries that we've written should be extracted into a standalone `golly` repository which can be `go get`-ed. All libraries should also be updated to include documentation which can be rendered on [GoPkgDoc](http://go.pkgdoc.org/).

And, finally, existing projects like `bolt` and `planfile-app` should be updated to use the `golly` github repository path for imports.