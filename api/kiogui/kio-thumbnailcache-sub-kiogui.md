---
title: "KIO::ThumbnailCache Namespace"
description: "Network transparent access to files and data."
---

# KIO::ThumbnailCache Namespace

Network transparent access to files and data.

## Function Documentation {#function-documentation}

### short ThumbnailCache::cacheSize(const QSize &*size*) {#cacheSize}

The size a thumbnail of `size` is generated and cached at: 128, 256, 512 or 1024.

### bool ThumbnailCache::contains(const QString &*localPath*, const QString &*thumbRoot*) {#contains}

Whether the local file `localPath` lies in the cache rooted at `thumbRoot`, however either path is spelled. Such a file is a thumbnail itself and must not get one in turn.

### QString ThumbnailCache::filePath(const QByteArray &*uri*, const QString &*thumbRoot*, const QSize &*size*, qreal *devicePixelRatio*) {#filePath}

Cache file path for the encoded `uri`, empty when no directory holds thumbnails of that size.

### bool ThumbnailCache::isCurrent(const QImage &*thumb*, qint64 *sourceMTimeSecs*, KIO::filesize\_t *sourceSize*) {#isCurrent}

Whether `thumb` was made from the file as it stands now.

### QImage ThumbnailCache::load(const QString &*path*, qreal *devicePixelRatio*) {#load}

Reads the thumbnail at `path`, tagging it with `devicePixelRatio`, or a null image.

### bool ThumbnailCache::matches(const QImage &*thumb*, const QByteArray &*uri*, qint64 *sourceMTimeSecs*, KIO::filesize\_t *sourceSize*, const QSize &*requestSize*, qreal *devicePixelRatio*, bool *requireSufficientResolution* = true) {#matches}

Whether `thumb` was made from the file `uri` names, of this modification time and size. With `requireSufficientResolution` a thumbnail smaller than the request is rejected as well, which a job wants and a lookup that shows what there is right now does not.

### QString ThumbnailCache::rootPath() {#rootPath}

Root of the cache, holding one directory per thumbnail size.

### QImage ThumbnailCache::scaledToFit(const QImage &*thumb*, const QSize &*size*) {#scaledToFit}

Scales `thumb` down to fit `size`, honouring its ratio, or returns it as it is.

### QImage ThumbnailCache::thumbnailFor(const QByteArray &*uri*, const QString &*thumbRoot*, const QSize &*size*, qreal *devicePixelRatio*, qint64 *sourceMTimeSecs*, KIO::filesize\_t *sourceSize*) {#thumbnailFor}

The cached thumbnail for the file `uri` names, ready to be shown at `size`, or a null image when nothing usable is cached. Takes what it needs by value, so it can run on any thread.

### QString ThumbnailCache::tierDir(short *cacheSize*, qreal *devicePixelRatio*) {#tierDir}

The directory ("normal/", "large/", ...) that holds thumbnails of `cacheSize` at `devicePixelRatio`, empty when none of them is large enough. A thumbnailer multiplies what it is asked for by the ratio, so that product is what decides the directory.
