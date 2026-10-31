# Unread

Counts what came in for you next to the chat, place, board or channel in Places, until you open it on any of your devices. Messages to you count (direct messages, @mentions, replies to you, chat in your posts); its rules say, for a person, a place or a board, whether something counts.

A hint service Weave ships (docs/v2-stage20.md): it folds `weave.notice` (what your node works out is for you) and `weave.seen` (what you opened, sealed to you), and answers for spaces, boards and channels. Its settings are its rules: `{"rules": [{"who"?, "space"?, "board"?, "count", "notify"}]}`, the most specific one winning.

## Where it lives

This repository is its only source. Weave ships it by pinning one of its releases (Weave's
`packages/shipped/pinned.json`: this repository, a tag and the archive's SHA-256), so what Weave ships and what
its project releases are the same file. A new version: tag it here, release it in its Weave project, then move
the pin in Weave.

## Building and releasing

```
npm install
npm run build              # → unread.wasm
```

A tag `v*` builds it on GitHub and attaches `weave-unread.tar.gz` (the component, `weave.app.json` and this README) to a
release (`.github/workflows/release.yml`). In Weave, `weave app release <tag> --asset wasm=weave-unread.tar.gz -p <project>`
records it in a project, with its SHA-256.

`wit/service.wit` is Weave's service interface (`packages/sdk/wit` in Weave's repository), copied here to build against.
