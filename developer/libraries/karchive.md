---
title: KArchive
description: Read and write archives and compressed data.
source_url: https://develop.kde.org/docs/features/karchive/
source_authors: [Rohan Garg, Carl Schwan, Chris Holland, Mikhail Zolotukhin, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-archive (src, examples/bzip2gzip); the code on this page was built against SonicDE's KArchive and run
---

# KArchive

How do you store a lot of data in an archive easily from your code? [KArchive](/docs/api/karchive/karchive-index), in `sonic-frameworks-archive` (`find_package(KF6Archive)`, `KF6::Archive`), makes it quick and easy in Qt applications.

KArchive supports many archive formats: 7-Zip ([K7Zip](/docs/api/karchive/k7zip)), ZIP ([KZip](/docs/api/karchive/kzip)), tar ([KTar](/docs/api/karchive/ktar)), ar ([KAr](/docs/api/karchive/kar)) and Qt resource files ([KRcc](/docs/api/karchive/krcc)), so you can choose the format that suits your project.

## Creating and opening an archive

An archive consists of:

- a root directory
- optional directories inside it
- files in any directory

[KArchive::writeDir()](/docs/api/karchive/karchive#writeDir) creates directories, and [KArchive::writeFile()](/docs/api/karchive/karchive#writeFile) creates files, along with any directories in their path.

Both take paths: `writeDir("emptydir/emptysubdir")` and `writeFile("somedir/subdir/world")` create this structure:

```text
hello.zip
├── emptydir/
│   └── emptysubdir/
└── somedir/
    └── subdir/
        └── world
```

Creating an archive with this structure is simple:

```cpp
// Create a zip archive
KZip archive(QStringLiteral("hello.zip"));

// Open our archive for writing
if (archive.open(QIODevice::WriteOnly)) {
    // The archive is open, we can now write data
    archive.writeDir("emptydir/emptysubdir");
    archive.writeFile(QStringLiteral("somedir/subdir/world"), // File name
                      QByteArray("The whole world inside a hello."), // Data
                      0100644, // Permissions
                      QStringLiteral("owner"), // Owner
                      QStringLiteral("users")); // Group

    // Don't forget to close!
    archive.close();
}
```

If you know the path of the file, open the archive and read it like this:

```cpp
if (archive.open(QIODevice::ReadOnly)) {
    const KArchiveDirectory *dir = archive.directory(); // the root directory
    const KArchiveFile *file = dir->file("somedir/subdir/world");
    if (!file) {
        qInfo() << "File not found!";
        return -1;
    }
    QByteArray data(file->data());
    qInfo() << data; // the file contents
}
```

> **Tip:** `data()` reads the whole file into memory. To read it piece by piece, use [createDevice()](/docs/api/karchive/karchivefile#createDevice) instead; you own the device it returns and must delete it:
>
> ```cpp
> std::unique_ptr<QIODevice> device(file->createDevice());
> while (!device.get()->atEnd()) {
>     qDebug() << device->readLine();
> }
> ```

If you don't know the archive's structure in advance, use [KArchiveEntry](/docs/api/karchive/karchiveentry), the base class of [KArchiveDirectory](/docs/api/karchive/karchivedirectory) and [KArchiveFile](/docs/api/karchive/karchivefile).

With it you can check whether an entry is a file or a directory:

```cpp
// This example does not represent a full-fledged implementation.
if (archive.open(QIODevice::ReadOnly)) {
    const KArchiveDirectory *dir = archive.directory();
    const KArchiveEntry *entry = dir->entry("somedir/subdir/world");
    if (!entry) {
        qInfo() << "Entry not found!";
        return -1;
    }
    if (entry->isFile()) {
        const KArchiveFile *file = static_cast<const KArchiveFile *>(entry);
        QByteArray data(file->data());
        qDebug() << data;
    }
    // ...
}
```

## Advanced uses

### Working with compressed data

Besides archives, KArchive reads and writes compressed data on any device, such as a buffer or a socket, with [KCompressionDevice](/docs/api/karchive/kcompressiondevice). For example, you can save bandwidth when sending data over a network. It supports gzip, bzip2, xz, zstd and lzip compression.

This example, from `sonic-frameworks-archive/examples/bzip2gzip`, recompresses a bzip2 file with gzip (`file` is the opened input file, `info` its QFileInfo):

```cpp
// Open the input archive
KCompressionDevice input(&file, false, KCompressionDevice::BZip2);
if (!input.open(QIODevice::ReadOnly)) {
    return 1;
}

QString outputFile = (info.completeBaseName() + QLatin1String(".gz"));

// Open the new output file
KCompressionDevice output(outputFile, KCompressionDevice::GZip);
if (!output.open(QIODevice::WriteOnly)) {
    return 1;
}

while (!input.atEnd()) {
    // Read and uncompress the data
    QByteArray data = input.read(512);

    // Write data like you would to any other QIODevice
    output.write(data);
}

input.close();
output.close();
```

`KCompressionDevice::open()` must have its result checked (the compiler warns otherwise).
