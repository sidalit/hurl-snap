# Hurl snap

[![hurl](https://snapcraft.io/hurl/badge.svg)](https://snapcraft.io/hurl)

Snap packaging for [Hurl](https://github.com/Orange-OpenSource/hurl), HTTP/API testing with repeatable requests and response assertions. The snap includes both `hurl` and `hurlfmt` (run as `hurl.hurlfmt`).

Unofficial build, not affiliated with or endorsed by the Hurl project.

## Build

```bash
snapcraft pack
```

## Install and try

<a href="https://snapcraft.io/hurl"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install hurl                   # or a local build: ./hurl_8.0.1_*.snap --dangerous
sudo snap connect hurl:removable-media   # optional: /media, /mnt
printf 'GET https://hurl.dev\nHTTP 200\n' > hello.hurl
hurl --test hello.hurl
hurl.hurlfmt --in-place hello.hurl
```

## Known limitations

### hurlfmt is named hurl.hurlfmt

Snaps can only expose their own name as a plain command, so `hurlfmt` is installed as `hurl.hurlfmt`. To call it `hurlfmt`, add an alias:

```bash
sudo snap alias hurl.hurlfmt hurlfmt
```

### ~/.netrc is not read

`hurl --netrc` looks for `.netrc` in the snap's own home (`~/snap/hurl/current`), not in your real home folder. Strict confinement also blocks hidden files directly in `$HOME`. Copy the file somewhere visible and pass it explicitly:

```bash
cp ~/.netrc ~/hurl.netrc
hurl --netrc-file ~/hurl.netrc session.hurl
```

### Unix sockets

`--unix-socket` works with sockets in your home folder. Sockets of system services elsewhere (for example `/var/run/docker.sock`) are blocked by strict confinement.

## Update to a new upstream release

Change `version` and `source-tag` in `snap/snapcraft.yaml`, then rebuild.

## License

The packaging is MIT-licensed (see `LICENSE`). Hurl is Apache-2.0-licensed; its dependencies carry their own licenses.
