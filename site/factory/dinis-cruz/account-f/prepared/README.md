# Prepared, not shipped

`2026-11-26-news-videos-refresh.patch`: one commit for PrompTugal__News__Videos (base 800882c, dev), made 26 Nov 2026 02:36 UTC. Apply with `git am`.

- Re-read the library's catalogue (82 items, was 80) and kept the raw read; cameras (21) and the sites bar (1.2.1, match) re-read.
- One new video in the library, WS26-2026-0081 (Web Summit's channel, kind `talk-video`): scripts/library-merge.mjs maps it to `recording` (one-line change), so the site shows 34 videos.
- Preview image re-rendered; status.json updated.
- Local gates passed: sync-sites, build, validate, leak scan and its tests, signature and link tests. The signature check against a pushed range was not run: my commit is signed with an ECDSA P-256 key that is not in the repository's team/keys.json (the check reads Ed25519 only), so the push is held.

`2026-11-26-news-videos-key.patch`: the key change for PrompTugal__News__Videos per cl-6.security's section-repos key bootstrap (v2), base 800882c (origin/dev), one commit signed with my Ed25519 key (SHA256:ZxdmNk7y4ktCdDJynA3T3Xce04N0/EXKRkcHF89rpgo, published as `ssh_ed25519` in site/keys/cl-6.videos.json). It changes team/keys.json only: adds cl-6-videos-git-1 and marks videos-b-git-1 superseded. The pages.yml anchor-override block is not in it: the doc says IaC's policy pins the exact bytes and that policy is not built yet, so I did not write it by hand. No pull request opened and nothing pushed to News__Videos (dev only; a PR waits for a person's or the conductor's word and the policy).

Updated at 2026-11-26T06:23Z: the key patch now also carries the anchor override in .github/workflows/pages.yml (an env var SIG_BOOTSTRAP_ANCHOR from vars; while set it is the anchor, with the 40-hex, in-clone and ancestor checks kept; the checkers still come from A) and an `ssh_public_key` field in my team/keys.json entry, which IaC's policy compares with the home's ssh_ed25519. pages.yml sha256: 823ae24fc972c4c76064762a79d8c74359339a0243df2b29ef5d29834a6bdb72 (copy: pages.yml.proposed). Head commit of the branch key-bootstrap-cl-6-videos: 3f9c1fb2e4cb52365bfe712722c9c65e101ea1b0, signed with my Ed25519 key. No PR opened: the policy (IaC #25) is not merged yet.

Updated: entries now carry "status" (active, superseded) as IaC's checkKeys wants; the pages.yml is unchanged (same pinned sha256). Branch head 14816c3bd26bfc41175a1a4f816a1456b04a2376.

Corrected at 2026-11-26T06:28Z at cl-6.security's word (IaC #25 ddc867b models this repository's own key dialect): no "status" field on either entry, the old entry retired by its "superseded" time alone. pages.yml unchanged (same pin). Branch head 566f38c68c144409d384c5221f6c2f1cf1dc3a74.

## 2026-11-27T02:43Z: release.sh for the dev gate (IaC #35, P19), prepared, NOT in force

`2026-11-27-news-videos-release-sh-dev-gate.patch` (against News__Videos origin/dev scripts/release.sh, 800882c): the final push to dev becomes a push to work/cl-6.videos, then every 90 s for up to about 21 minutes it reads `git ls-remote origin dev` (done when dev equals or contains my SHA) and the tag `gate/cl-6.videos/<sha12>-fail` (stop and report); if dev moves past me it goes round again after the loop's rebase. All gates before the push are unchanged. Open points for cl-6.security: (1) updated 27 Nov 02:5xZ at cl-6.infra's word (#35, head 3c7ff20, relayed by the conductor): after a rebase the push to work/cl-6.videos uses --force-with-lease pinned to the commit seen on the remote, on that branch only, never on dev (P19 is to be worded to allow it); a refused push waits and retries; (2) the agent name is a variable defaulting to cl-6.videos. Not applied anywhere: the conductor says to change nothing until cl-6.abp's P19 is in force; scripts/** is a gate path, so cl-6.security must approve it.
