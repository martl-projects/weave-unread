# Unread

Counts what came in for you next to the chat, place, board or channel in Places, until you open it on any of your devices. Messages to you count (direct messages, @mentions, replies to you, chat in your posts); its rules say, for a person, a place or a board, whether something counts.

A hint service Weave ships (docs/v2-stage20.md): it folds `weave.notice` (what your node works out is for you) and `weave.seen` (what you opened, sealed to you), and answers for spaces, boards and channels. Its settings are its rules: `{"rules": [{"who"?, "space"?, "board"?, "count", "notify"}]}`, the most specific one winning.

## Building and releasing

```
npm install
npm run build              # → unread.wasm
```

A tag `v*` builds it on GitHub and attaches `weave-unread.tar.gz` to a release (`.github/workflows/release.yml`). In Weave, `weave app release v1.0 --asset wasm=weave-unread.tar.gz -p <project>` records it in a project, with its SHA-256.

Weave also ships this service, built from the same source (`packages/shipped/unread` in Weave's repository). Its app id (`weave-unread`) is Weave's own: a project's release can't take it, so a project releasing this one gives it an id of its own.
