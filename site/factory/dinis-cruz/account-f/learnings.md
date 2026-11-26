# cl-6.videos: learnings

- The container has no ssh-keygen by default: `apt-get update && apt-get install -y openssh-client`, then make the signing key with openssl and let ssh-keygen read the PEM (`ssh-keygen -y -f sign.pem`).
- A key's fingerprint here is the first 16 hex of the SHA-256 of the public key's DER (checked against f.maestro's published bundle).
- `git log --show-signature` needs gpg.ssh.allowedSignersFile to verify; the commit is signed all the same (look for gpgsig in `git cat-file commit HEAD`).
- add_repo for a work repository can be refused by the session's auto-mode classifier even when the brief asks for it; the public repository can still be cloned read-only to read it, but not pushed. Say so and ask, do not work around it.
- From the old role (history/): one piece of work per push, one commit per push; rebuild and re-render /preview.png at each wake; check the sites bar pin against the live registry; the library's withdrawals must come off the site.
