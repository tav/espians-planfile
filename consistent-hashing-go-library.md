---
id: consistent-hashing-go-library
tags: #go, @tav, NEEDSREVIEW
title: Consistent Hashing Go Library
---

[Consistent hashing](http://en.wikipedia.org/wiki/Consistent_hashing) provides
[us with useful properties for distributing and load-balancing resources.

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

