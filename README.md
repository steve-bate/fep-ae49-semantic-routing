# FEP-ae49: Semantic Routing for ActivityPub

**Status:** DRAFT · **Type:** implementation · **Author:** Steve Bate

## Overview

Most ActivityPub servers route incoming requests by parsing URI paths (for example
`/users/:username/inbox`). This couples server behavior to a concrete URI layout: migrating
to different software usually means either reproducing the old paths or minting new actor
URIs, which breaks federated relationships. It also violates the principle of URI opacity.

This FEP specifies **semantic routing**: a server dispatches requests by treating the target
URI as an opaque identifier, dereferencing the resource, and following ActivityStreams
relationships (such as `attributedTo`, `inbox`, and `outbox`) to identify the handler. The
wire protocol is unchanged; only the implementation strategy is constrained.

In scope are `POST` to an actor's `inbox`, `outbox`, or `sharedInbox`, and `GET` of an
ActivityPub object by `id`. A conforming "Semantically Routing Server" must not parse path,
query, or fragment components to determine the target actor or endpoint, which keeps actor
URIs stable across software migrations. The FEP notes existing implementations in FIRM,
Vocata, and Mitra.

## Files

- [`fep-ae49.md`](fep-ae49.md) — the proposal

## The FEP

- Document: <https://github.com/steve-bate/fep-ae49-semantic-routing/blob/main/fep-ae49.md>
- Repository: <https://github.com/steve-bate/fep-ae49-semantic-routing>
- Discussion: <https://github.com/steve-bate/fep-ae49-semantic-routing/issues>

## License

This work is released under [CC0 1.0 Universal](LICENSE.md) (public domain dedication).
See [LICENSE.md](LICENSE.md).
