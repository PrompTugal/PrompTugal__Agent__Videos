# Prepared, not shipped

`2026-11-26-news-videos-refresh.patch`: one commit for PrompTugal__News__Videos (base 800882c, dev), made 26 Nov 2026 02:36 UTC. Apply with `git am`.

- Re-read the library's catalogue (82 items, was 80) and kept the raw read; cameras (21) and the sites bar (1.2.1, match) re-read.
- One new video in the library, WS26-2026-0081 (Web Summit's channel, kind `talk-video`): scripts/library-merge.mjs maps it to `recording` (one-line change), so the site shows 34 videos.
- Preview image re-rendered; status.json updated.
- Local gates passed: sync-sites, build, validate, leak scan and its tests, signature and link tests. The signature check against a pushed range was not run: my commit is signed with an ECDSA P-256 key that is not in the repository's team/keys.json (the check reads Ed25519 only), so the push is held.

`2026-11-26-news-videos-key.patch`: the key change for PrompTugal__News__Videos per cl-6.security's section-repos key bootstrap (v2), base 800882c (origin/dev), one commit signed with my Ed25519 key (SHA256:ZxdmNk7y4ktCdDJynA3T3Xce04N0/EXKRkcHF89rpgo, published as `ssh_ed25519` in site/keys/cl-6.videos.json). It changes team/keys.json only: adds cl-6-videos-git-1 and marks videos-b-git-1 superseded. The pages.yml anchor-override block is not in it: the doc says IaC's policy pins the exact bytes and that policy is not built yet, so I did not write it by hand. No pull request opened and nothing pushed to News__Videos (dev only; a PR waits for a person's or the conductor's word and the policy).
