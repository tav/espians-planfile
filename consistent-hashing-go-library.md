---
id: consistent-hashing-go-library
tags: REVIEW, @tav, #go, #dev
title: Consistent hashing library in Go
---

There are a number of techniques that we will be using to distribute and load-balance resources. The most simplest and elegant of these is [consistent hashing](http://en.wikipedia.org/wiki/Consistent_hashing).

A `Ring` type should be provided within the `amp/hash` package that we could
use as follows:

  ```go
  ring := hash.NewRing("server-1", "server-5")
  ring.Add("server-28")
  server := ring.Find([]byte("some-key"))
  ```

Ideally, there would also be a `Ring.FindMultiple()` method which would return
N number of distinct servers for a given key. This would allow us to store the
key on N servers so that if any one go off-line, we still have another acting
as a hot standby.