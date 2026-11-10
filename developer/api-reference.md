---
title: Generating the API reference
description: How the API reference is generated from QDoc comments with docbook2markdown6, and how to check it before publishing.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-doctools (src/docbook2markdown/main.cpp, converter.h, CMakeLists.txt), sonicde-builder (generate-api-docs, check-api-docs, scripts/api_docs.py, scripts/api_docs_check.py, config/qdoc/); written from the code, not run"
---

# Generating the API reference

The [API reference](/docs/api) isn't written by hand. It's generated from the documentation comments in
each library's source, so to fix a mistake in it, fix the comment in the source and generate it again.
Never edit `api/` in sonic-docs: it's replaced on every generation.

## Documenting a library

A library takes part when its CMake calls `ecm_generate_qdoc()` with a `.qdocconf` file, as the
frameworks do. Write the comments in QDoc's syntax (`/*! … */`, `\class`, `\fn`, `\brief` and so on),
next to the declarations or in the module's `.qdoc` files. Sonic Logging, Sonic IPC and Sonic Init Info
are small, complete examples: their `src/*.qdoc` and `src/*.qdocconf` files and their headers.

## Generating it

From sonicde-builder, after a build (`./build-all`, or `./build-repo` for the libraries you changed):

```sh
./generate-api-docs
```

It finds every library with a `prepare_docs_<target>` target in `build/sonicde/` and runs QDoc with
exactly the settings ECM set up for it, but with one shared index and output directory:

1. `qdoc --prepare` for every module, which writes the `.index` files.
2. `qdoc --generate` with DocBook output for every module, with every module's index available, so
   links between libraries resolve.
3. `docbook2markdown6` for every module, into one fresh Markdown directory.

That directory then replaces `api/` in the builder's sonic-docs checkout (`src/sonicde/sonic-docs`).
Committing and pushing sonic-docs is up to you. A module that fails is logged and named in the summary,
keeps the pages it had before, and is tried again next time; the command exits with 1.

Runs are incremental: a module is prepared again only when its repository's source changed, and
generated and converted again when its source or the index of a module it depends on changed. A
different QDoc, Qt documentation, QDoc templates or converter redoes what they affect.

| Option | What it does |
| --- | --- |
| `--repo NAME` | Only this repository. Repeat it for several. |
| `--output DIR` | Write the reference here instead of the sonic-docs checkout. The folder must be empty or hold an earlier reference. |
| `--work DIR` | Where indexes, DocBook, Markdown and logs go (default `state/api-docs`). |
| `--build-root DIR` | The builds to read (default `build/sonicde`). |
| `--kde-docs DIR` | The QDoc templates used for `$KDE_DOCS` in the `.qdocconf` files. By default `$KDE_DOCS`, else Qt's templates with SonicDE's `config/qdoc/module-use.qdocinc`. |
| `--converter PATH` | The `docbook2markdown6` to run. By default the one built in this checkout, else an installed one. |
| `--jobs N`, `-j N` | How many modules to process at once. |
| `--full` | Redo every module, not only the changed ones. |

## Checking it

Before publishing, run:

```sh
./check-api-docs
```

It runs offline and checks that:

- every internal link and every `toc.yaml` entry points to a generated page, and its anchor exists;
- every link into Qt's documentation names a page and anchor that exist in the installed Qt
  documentation;
- every class, struct and union in a module's QDoc index has a page and an all-members page, and is
  listed on its module page and in `toc.yaml`.

Other external links are only counted, because sites block automated requests. The summary also lists
QDoc's warnings about undocumented symbols and the members the converter left out. It exits with 1 when
a check fails. `--reference`, `--work`, `--qt-docs` and `--build-root` point it at other folders.

## docbook2markdown6

`docbook2markdown6`, in `sonic-frameworks-doctools`, converts one module's QDoc DocBook output into
Markdown pages for the website. `generate-api-docs` runs it for you; you only need it directly to work
on the converter itself.

```sh
docbook2markdown6 --module <name> [--index <file>] [--qt-docs-dir <dir>] [--qt-docs-url <url>] <docbook-dir> <output-dir>
```

- `--module` (required): the module's folder name, such as `kconfigcore`.
- `--index`: the module's `.index` file from QDoc's prepare step. QDoc's DocBook leaves the pages of
  structs and unions untitled, and the index supplies their names.
- `--qt-docs-dir`: Qt's module documentation and `.index` files, for links into Qt (default
  `/usr/share/qt6-doc`).
- `--qt-docs-url`: the base URL for those links (default `https://doc.qt.io/qt-6/`).

For each page it writes `<module>/<page>.md`; classes also get `<page>-members.md`, and
`<page>-obsolete.md` when they have deprecated members. It copies the module's images and writes
`<module>/module.json`. Run it once per module with the same output directory: each run also rewrites
`toc.yaml`, `index.md` and the all-members pages for every module converted there, because all-members
pages include members inherited from other modules.

It logs through [Sonic Logging](libraries/sonic-logging.md) and mirrors its messages to stderr even when
that's a pipe, so a failing step in a script or CI still says why. The converter's own API is in the
[KDocTools reference](/docs/api/kdoctools/kdoctools-index).
