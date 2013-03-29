---
id: sha-3-library-in-go
tags: #go, TODO
title: SHA-3 Library in Go
---

Now that NIST have officially selected [<span style="font-variant: small-caps">Keccak</span>](http://keccak.noekeon.org/) as the [winner of the SHA-3 Competition](http://www.nist.gov/itl/csd/sha-100212.cfm), we can start implementing a `sha3` library which provides the standard [hash.Hash interface](http://golang.org/pkg/hash/#Hash). Since <span style="font-variant: small-caps">Keccak</span> allows for custom digest lengths, the constructor should support it being specified:

```go
func New(size int) hash.Hash
```

Do bear in mind that for the final SHA-3 spec, NIST will most likely eliminate this generality and define outputs matching the existing SHA-2 lengths. So we should have matching constructors, i.e.

```go
func New224() hash.Hash
func New256() hash.Hash
func New384() hash.Hash
func New512() hash.Hash
```

There's a small chance that NIST may do otherwise or even change some parameters like the number of rounds used, so we should pay close attention to the final spec which would [probably be published](http://csrc.nist.gov/publications/PubsFIPS.html) as an update to [FIPS 180-4](http://csrc.nist.gov/publications/fips/fips180-4/fips-180-4.pdf), the Secure Hash Standard (SHS).

Though not performant, the following implementations could prove helpful:

* http://www.mjos.fi/dist/readable_keccak.tgz
* https://bitbucket.org/ede/sha3