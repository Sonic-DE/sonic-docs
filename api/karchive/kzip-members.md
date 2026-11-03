---
title: "List of All Members for KZip"
description: "Every member of KZip, including inherited members."
parent: "karchive/kzip"
---

# List of All Members for KZip

This is the complete list of members for [KZip](kzip.md), including inherited members.

- [KZip(QIODevice \*)](kzip.md#KZip)
- [KZip(const QString &)](kzip.md#KZip-1)
- [~KZip()](kzip.md#dtor.KZip)
- [addLocalDirectory(const QString &, const QString &) : bool](karchive.md#addLocalDirectory)
- [addLocalFile(const QString &, const QString &) : bool](karchive.md#addLocalFile)
- [close() : bool](karchive.md#close)
- [closeArchive() : bool](karchive.md#closeArchive)
- [compression() const : KZip::Compression](kzip.md#compression)
- [createDevice(QIODevice::OpenMode) : bool](karchive.md#createDevice)
- [device() const : QIODevice \*](karchive.md#device)
- [directory() const : const KArchiveDirectory \*](karchive.md#directory)
- [doFinishWriting(qint64) : bool](karchive.md#doFinishWriting)
- [doPrepareWriting(const QString &, const QString &, const QString &, qint64, mode\_t, const QDateTime &, const QDateTime &, const QDateTime &) : bool](karchive.md#doPrepareWriting)
- [doWriteData(const char \*, qint64) : bool](karchive.md#doWriteData)
- [doWriteDir(const QString &, const QString &, const QString &, mode\_t, const QDateTime &, const QDateTime &, const QDateTime &) : bool](karchive.md#doWriteDir)
- [doWriteSymLink(const QString &, const QString &, const QString &, const QString &, mode\_t, const QDateTime &, const QDateTime &, const QDateTime &) : bool](karchive.md#doWriteSymLink)
- [errorString() const : QString](karchive.md#errorString)
- [extraField() const : KZip::ExtraField](kzip.md#extraField)
- [fileName() const : QString](karchive.md#fileName)
- [findOrCreate(const QString &) : KArchiveDirectory \*](karchive.md#findOrCreate)
- [finishWriting(qint64) : bool](karchive.md#finishWriting)
- [isOpen() const : bool](karchive.md#isOpen)
- [mode() const : QIODevice::OpenMode](karchive.md#mode)
- [open(QIODevice::OpenMode) : bool](karchive.md#open)
- [openArchive(QIODevice::OpenMode) : bool](karchive.md#openArchive)
- [prepareWriting(const QString &, const QString &, const QString &, qint64, mode\_t, const QDateTime &, const QDateTime &, const QDateTime &) : bool](karchive.md#prepareWriting)
- [rootDir() : KArchiveDirectory \*](karchive.md#rootDir)
- [setCompression(KZip::Compression)](kzip.md#setCompression)
- [setDevice(QIODevice \*)](karchive.md#setDevice)
- [setErrorString(const QString &)](karchive.md#setErrorString)
- [setExtraField(KZip::ExtraField)](kzip.md#setExtraField)
- [setRootDir(KArchiveDirectory \*)](karchive.md#setRootDir)
- [writeData(QByteArrayView) : bool](karchive.md#writeData)
- [writeData(const char \*, qint64) : bool](karchive.md#writeData-1)
- [writeDir(const QString &, const QString &, const QString &, mode\_t, const QDateTime &, const QDateTime &, const QDateTime &) : bool](karchive.md#writeDir)
- [writeFile(const QString &, QByteArrayView, mode\_t, const QString &, const QString &, const QDateTime &, const QDateTime &, const QDateTime &) : bool](karchive.md#writeFile)
- [writeSymLink(const QString &, const QString &, const QString &, const QString &, mode\_t, const QDateTime &, const QDateTime &, const QDateTime &) : bool](karchive.md#writeSymLink)
