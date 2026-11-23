# Relux Works APT Repository

Signed Debian and Ubuntu APT repository for [Relux Works](https://github.com/relux-works) CLI packages (`amd64` and `arm64`).

## Quick Start

Add the signing key and repository source:

```sh
curl -fsSL https://apt.relux.works/relux-works.gpg \
  | sudo tee /usr/share/keyrings/relux-works.gpg >/dev/null

echo "deb [signed-by=/usr/share/keyrings/relux-works.gpg] https://apt.relux.works stable main" \
  | sudo tee /etc/apt/sources.list.d/relux-works.list

sudo apt update
sudo apt install weightspace
```

## Available Packages

| Package | Description | Architectures | Project |
|---|---|---|---|
| `weightspace` | Weightspace Index CLI & interactive TUI (installs `weightspace` and `wsp`) | `amd64`, `arm64` | [weightspaceindex.com](https://weightspaceindex.com) |

## Signing Key Verification

Before trusting the keyring, verify its fingerprint:

```sh
gpg --show-keys --with-fingerprint /usr/share/keyrings/relux-works.gpg
```

- **Key ID:** `F904AFA13300813C`
- **Fingerprint:** `AB55 B321 5DE7 5BB8 5481 53AA F904 AFA1 3300 813C`
- **UID:** `Relux Works APT <ivan@relux.works>`
- **Downloads:** [relux-works.gpg](https://apt.relux.works/relux-works.gpg) (binary keyring for APT) · [relux-works.asc](https://apt.relux.works/relux-works.asc) (ASCII-armored)

## Repository Layout

- `dists/stable/InRelease`, `dists/stable/Release`, `dists/stable/Release.gpg` — GPG-signed APT metadata
- `dists/stable/main/binary-{amd64,arm64}/Packages{,.gz}` — per-architecture package indexes
- `pool/main/` — `.deb` packages published from tagged GitHub Releases
