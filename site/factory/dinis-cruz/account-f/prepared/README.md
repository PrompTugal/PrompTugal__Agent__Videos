# Prepared, not shipped

`2026-11-26-news-videos-refresh.patch`: one commit for PrompTugal__News__Videos (base 800882c, dev), made 26 Nov 2026 02:36 UTC. Apply with `git am`.

- Re-read the library's catalogue (82 items, was 80) and kept the raw read; cameras (21) and the sites bar (1.2.1, match) re-read.
- One new video in the library, WS26-2026-0081 (Web Summit's channel, kind `talk-video`): scripts/library-merge.mjs maps it to `recording` (one-line change), so the site shows 34 videos.
- Preview image re-rendered; status.json updated.
- Local gates passed: sync-sites, build, validate, leak scan and its tests, signature and link tests. The signature check against a pushed range was not run: my commit is signed with an ECDSA P-256 key that is not in the repository's team/keys.json (the check reads Ed25519 only), so the push is held.
