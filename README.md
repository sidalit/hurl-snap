<div align="center">

<img src="snap/gui/hurl.png" alt="Hurl logo" width="128" />

# Hurl

**Run and test HTTP requests defined in plain text files**

[![hurl](https://snapcraft.io/hurl/badge.svg)](https://snapcraft.io/hurl)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [Hurl](https://hurl.dev), a command-line tool for chaining HTTP requests and checking responses. Includes the Hurl file formatter as `hurl.hurlfmt`.

</div>

---

## Getting Started

<a href="https://snapcraft.io/hurl"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install hurl
hurl session.hurl
hurl.hurlfmt --in-place session.hurl
```

## Configure

Use Hurl files and command-line options. There are no `snap set` options. See the [upstream manual](https://hurl.dev/docs/manual.html) for request, authentication and reporting settings.

```bash
sudo snap connect hurl:removable-media   # optional: /media, /mnt
sudo snap alias hurl.hurlfmt hurlfmt     # optional: upstream formatter command
```

## Limitations

- Files must be in accessible home directories or connected removable storage.
- Your host `~/.netrc` is inaccessible. Use `--netrc-file` with an accessible file, or place `.netrc` in `~/snap/hurl/current/`.
- Access to Unix sockets of host services, such as `/var/run/docker.sock`, is blocked by strict confinement.

## Build

```bash
git clone https://github.com/sidalit/hurl-snap.git
cd hurl-snap
sudo snap install snapcraft --classic
snapcraft pack
```

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/hurl-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/Orange-OpenSource/hurl/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/hurl-snap/blob/main/LICENSE).
