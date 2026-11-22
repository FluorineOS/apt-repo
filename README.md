# FluorineOS APT Repository

Official signed APT package repository for FluorineOS.

- Repository URL: https://fluorineos.github.io/apt-repo
- Distribution: trixie
- Components: main
- Architectures: amd64, all

## Usage

Install the fluorine-keyring package, then refresh the package index:

```sh
sudo apt update
```

## Publishing

Packages are imported with reprepro and served as a static repository through
GitHub Pages. Published pool packages are tracked in Git; local build artifacts
are ignored.

This repository is part of the FluorineOS project.
