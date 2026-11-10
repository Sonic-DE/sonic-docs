---
title: Building Sonic-DE
description: Fetch and build every Sonic-DE repository from source with sonicde-builder.
---

# Building Sonic-DE

Sonic-DE is built with [sonicde-builder](https://github.com/Sonic-DE/sonicde-builder), a
Python and CMake superbuild that fetches every active Sonic-DE repository and builds them in
dependency order.

## Requirements

- Python 3 with PyYAML (`pip install pyyaml`).
- A working Qt 6 from your operating system. The builder deliberately doesn't fetch or build Qt.
- CMake 3.28 or newer.
- The system packages listed by `./install-deps` (see [Dependencies](dependencies.md)).

## Fetch the sources

Clone sonicde-builder, then fetch every active repository:

```sh
./fetch-all
```

To fetch a single repository, without its dependencies:

```sh
./fetch sonic-browser-integration
```

Both commands accept `--dry-run` to show what they would do. Existing checkouts keep their
branch, index and working tree.

## Build

```sh
./build-all
```

Packages are built for the system prefix (`/usr` by default; change it with `--prefix PATH`)
and installed privately into `state/install-stage`, where later packages find them. Nothing is
installed on the live system during the build.

Useful options:

| Option | Meaning |
| --- | --- |
| `--parallel N`, `-j N` | Maximum concurrent compiler jobs inside one package |
| `--verbose`, `-v` | Verbose build output |
| `--clean-first` | Clean before building |
| `--install` | Install to the system after the full build succeeds |

## Leaving Night Light out of SonicWin

SonicWin (`sonic-win`) builds Night Light, with its `org.kde.KWin.NightLight` D-Bus
interface, when the CMake option `KWIN_BUILD_NIGHTLIGHT` is on, which is the default. It
then needs `KNightTime` from `sonic-night-light`.

A slimmer system can leave Night Light out by adding `-DKWIN_BUILD_NIGHTLIGHT=OFF` to
`cmake-extra-args` in `config/sonicde/packages/sonicde/sonic-win.yaml`. SonicWin then doesn't
look for `KNightTime`, and the software brightness test, which needs Night Light, isn't run.

## Install

`./build-all --install` deploys only after every package has built. Only the deployment step
asks for elevated rights; configuring and compiling run as your user.

To install the last successful build without rebuilding:

```sh
./install
```
