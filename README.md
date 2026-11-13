# Relux Works APT repository

This repository holds the signed APT index for Relux Works and Swarma binaries. It is served through GitHub Pages.

The packages are the `.deb` files from each project's GitHub Release, built by the shared Relux release workflow
(owner: the curator-run lane). This repository only holds the index (`dists/`) and the package pool (`pool/`).

## Status

**Not published yet.** The index is signed with the Relux Works APT key. Ivan places that key himself as the org
secrets `APT_GPG_PRIVATE_KEY` and `APT_GPG_PASSPHRASE`. Until he does, the publishing step stays disabled and this
repository holds no packages.

## Planned use

```sh
curl -fsSL https://relux-works.github.io/apt/relux-works.gpg | sudo tee /usr/share/keyrings/relux-works.gpg >/dev/null
echo "deb [signed-by=/usr/share/keyrings/relux-works.gpg] https://relux-works.github.io/apt stable main" \
  | sudo tee /etc/apt/sources.list.d/relux-works.list
sudo apt update && sudo apt install curator-run
```

Before you trust the key, check its fingerprint against the one published in the release notes of each project.
