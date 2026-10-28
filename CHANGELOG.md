# 0.6.0

## Changes

- Updated dependencies:
  - `libp2p` to `v0.57`
  - `arti-client`, `tor-rtcompat`, `tor-hsservice`, `tor-cell`, `tor-proto` to `v0.47`
  - `thiserror` to `v2`; dev: `tracing-subscriber` to `v0.3`
- `Transport::dial` takes libp2p's `DialOpts`; `dial_as_listener` and `address_translation` are gone from the trait (libp2p-core 0.44). Tor neither hole-punches nor reuses ports, so the options are ignored.
- `TorClient::launch_onion_service` returns `None` when onion services are disabled in the Tor client's configuration: `add_onion_service` now returns an error for it.
- `onion_name()` replaced by `onion_address()`; an onion address is formatted with `safelog`'s `display_unredacted()` (new optional dependency of `listen-onion-service`).
- Fixed: dialing an onion address leaked its domain string (`Box::leak`) on every dial.
- Example `ping-onion`: the swarm now uses the same key Noise authenticates with (it used a fresh identity, so its peer id did not match), and is built with `Swarm::new` and a 60 s connection timeout — `SwarmBuilder::build` caps a connection at 10 s, which an onion circuit from far away often exceeds.

Upgraded by [Satlights](https://github.com/Satlights), tested over the live Tor network (onion services both ways, between servers in Switzerland and a computer in India).

# 0.4.1

- Remove double features: See [PR 21]
- Correct typo in `src/lib.rs`: See [PR 21]
- Update `CHANGELOG.md`: See [PR 21]

[PR 21]: https://github.com/umgefahren/libp2p-tor/pull/21

# 0.4.0

## Changes

- Updated dependencies: See [PR 18]
  - [`arti-client` to `v0.24.0`]
  - [`libp2p` to `v0.53.0`]
  - [`tor-rtcompat` to `v0.24.0`]
- Add tracing: See [PR 18]
- Update CI: See [PR 20]
  - `actions/checkout` to `v4`
  - Remove `arduino/setup-protoc`

## First time contributor

- @binarybaron

Thanks! :rocket:

[PR 18]: https://github.com/umgefahren/libp2p-tor/pull/18
[PR 20]: https://github.com/umgefahren/libp2p-tor/pull/20


# 0.3.0-alpha

- Updated dependencies: See [PR 6].
  - [`arti-client` to `v0.8`
  
- Updated dependencies: See [PR 8].
  - `libp2p-core` to `v0.39`
  - `libp2p` to `0.51`

[PR 6]: https://github.com/umgefahren/libp2p-tor/pull/6
[PR 8]: https://github.com/umgefahren/libp2p-tor/pull/8

# 0.2.0-alpha

- Updated dependencies:
  - [`libp2p` to `v0.50.0`](#2)
  - [`libp2p-core` to `v0.38.0`](#3)
