<p align="center">
  <a href="https://matrix.to/#/!uBhYhtcoNlyEbzfYAW:matrix.org">
    <img src="https://img.shields.io/matrix/crev:matrix.org.svg?server_fqdn=matrix.org&style=flat-square" alt="crev matrix channel">
  </a>
  <a href="https://gitter.im/dpc/crev">
    <img src="https://img.shields.io/gitter/room/dpc/crev.svg?style=flat-square" alt="crev gitter channel">
  </a>
  <br>
</p>

# Crev - Code REView system that we desperately need

## Implementations

* [cargo-crev: Crev for Rust/cargo](https://github.com/crev-dev/cargo-crev) - ready and working
* [npm-crev: Crev for Node/NPM](https://www.npmjs.com/package/crev) - baby steps
* [pip-crev: Crev for Python/PIP](https://github.com/crev-dev/pip-crev) - still early
* Crev for Julia/Pkg - in plans; ask around on [Crev Matrix channel](https://matrix.to/#/#crev:matrix.org)
* other languages/ecosystems - join [Crev Matrix channel](https://matrix.to/#/#crev:matrix.org), tell us about your interest and find help

## Introduction

You're ultimately responsible for vetting your dependencies.

But in a world of NPM/PIP/Cargo/RubyGems - how do you do that? Can you keep up with ever-changing ecosystem?

Crev is an actual *code review* system as opposed to typically practiced *code-change review* system.

Crev is scalable, distributed, and social. Users publish and circulate results of their reviews: potentially warning about problems, malicious code, or just encouraging high quality by peer review.

Crev allows building a personal web of trust in other people and the code they use and review.

Crev [is a][f] [tool][e] [we][d] [desperately][c] [need][b] [yesterday][a]. It protects against compromised dev accounts, intentional malicious code, typosquatting, compromised package registries, or just plain poor quality.

[a]: https://www.csoonline.com/article/3214624/security/malicious-code-in-the-node-js-npm-registry-shakes-open-source-trust-model.html

[b]: https://thenewstack.io/npm-attackers-sneak-a-backdoor-into-node-js-deployments-through-dependencies/

[c]: https://news.ycombinator.com/item?id=17513709

[c]: https://www.theregister.co.uk/2018/11/26/npm_repo_bitcoin_stealer/

[d]: https://www.zdnet.com/article/twelve-malicious-python-libraries-found-and-removed-from-pypi/

[e]: https://www.itnews.com.au/news/rubygems-in-recovery-mode-after-site-hack-330819

[f]: https://users.rust-lang.org/t/security-advisory-for-crates-io-2017-09-19/12960

## Vision

We would like Crev to become a general, language, and ecosystem agnostic
system for establishing trust in Open Source code. We would like to have
frontends integrated with all the major Open Source package managers and ecosystems,
and many independent and interoperable tools building on top of it.

## Overview

At it's core Crev defines a simple, human-readable data format to communicate
trust in code (results of code review) and people (reputation).

Using tools implementing Crev, you can generate cryptographically signed artifacts (*Proofs*).

Here is an example of a *Package Review Proof* that describes results of reviewing a whole package (library, crate, etc.):

```
-----BEGIN CREV PACKAGE REVIEW-----
version: -1
date: "2018-12-16T00:09:27.905713993-08:00"
from:
  id-type: crev
  id: 8iUv_SPgsAQ4paabLfs1D9tIptMnuSRZ344_M-6m9RE
  url: "https://github.com/dpc/crev-proofs"
package:
  source: "https://crates.io"
  name: default
  version: 0.1.2
  digest: RtL75KvBdj_Zk42wp2vzNChkT1RDUdLxbWovRvEm1yA
review:
  thoroughness: high
  understanding: high
  rating: positive
comment: "I'm the author, and this crate is trivial"
-----BEGIN CREV PACKAGE REVIEW SIGNATURE-----
QpigffpvOnK7KNdDzQSNRt8bkOFYP_LOLE-vOZ2lu6Je5jvF3t4VZddZDDnPhxaY9zEQurozqTiYAHX8nXz5CQ
-----END CREV PACKAGE REVIEW-----
```

*Proofs* are published and exchanged in a similar way that Open Source code is, for other people to benefit from.

## Fundamental beliefs of Crev design:

* Trust is about people and community, not automatic scans,
  arbitrary metrics, process, or bureaucracy. You can't replace a human judgment
  with an algorithm. Tools can only help make such a judgment.
* Code quality, risk management, and trust requirements are subjective, contextual, and personal.
  Islands of Trust must grow organically.
* Not many people can review all their dependencies, but if every user
  at least skimmed through a couple of them, and shared that information with
  others, we would be in a much better situation.
* Trust should be spread redundantly between many people, so one compromised or malicious
  actor can't abuse the system.
* Crev does not have to be perfect. Instead it should be robust, simple and flexible, so
  it can evolve to be good enough.

## Further reading

For more concrete information, see [cargo-crev - first and currently most advanced implementation of Crev](https://github.com/crev-dev/cargo-crev).
