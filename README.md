# FluorineOS APT Repository

`Debian 13 Trixie | amd64`

> **Looking for the FluorineOS ISO?** Official installation images are published in the
> main repository:
> [FluorineOS/fluorine Releases](https://github.com/FluorineOS/fluorine/releases/latest).

The FluorineOS APT repository is a signed reprepro archive served as static files through
GitHub Pages. It carries `fluorine-desktop`, `fluorine-artwork`, and `fluorine-keyring`
for the `trixie` suite.

## Repository Layout

| Path | Contents |
| --- | --- |
| `dists/trixie/InRelease` | Clearsigned archive metadata |
| `dists/trixie/Release` | Detached archive metadata |
| `dists/trixie/Release.gpg` | Detached signature for `Release` |
| `dists/trixie/main/binary-amd64/Packages` | Package index |
| `pool/main/f/` | Package pool |

## Usage

Install `fluorine-keyring` to add the signing key and source definition, then refresh the
package index:

```sh
sudo apt-get update
# fluorine-desktop needs Hyprland from trixie-backports; see the
# fluorine-desktop README for the required APT pin
sudo apt-get install fluorine-desktop
```

The source definition installed by `fluorine-keyring` is:

```ini
Types: deb
URIs: https://fluorineos.github.io/apt-repo
Suites: trixie
Components: main
Architectures: amd64
Signed-By: /usr/share/keyrings/fluorineos-archive-keyring.gpg
```

## Verify

APT verifies the `InRelease` signature against the keyring during `apt-get update`. To
inspect the signing key directly:

```sh
gpg --show-keys fluorineos-archive-keyring.asc
```

The primary key fingerprint is
`DCF8D117141143E65F930B55206E495540B36253`.

## Publishing

Packages are imported with `reprepro`, the `Release` metadata is signed with the
FluorineOS archive key, and the resulting tree is committed to this repository and served
through GitHub Pages. Pool packages and indexes are tracked in Git; local build artifacts
are ignored.

## License

Released under the MIT License. See [LICENSE](LICENSE) for the full text.

Source: [FluorineOS/apt-repo](https://github.com/FluorineOS/apt-repo)
