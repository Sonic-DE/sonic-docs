---
title: "KExiv2Iface::KExiv2 Class"
description: "Todo."
---

# KExiv2Iface::KExiv2 Class

Todo. [More...](#details)

- **Header:** `#include <KExiv2/KExiv2>`
- **CMake:** `find_package(KExiv2Qt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE KExiv2Qt6)`

[List of all members, including inherited members](kexiv2iface-kexiv2-members.md)

## Public Types

- [KExiv2::AltLangMap](#AltLangMap-typedef)
- [enum KExiv2::ImageColorWorkSpace](#ImageColorWorkSpace-enum)
- [enum KExiv2::ImageOrientation](#ImageOrientation-enum)
- [KExiv2::MetaDataMap](#MetaDataMap-typedef)
- [enum KExiv2::MetadataWritingMode](#MetadataWritingMode-enum)
- [KExiv2::TagsMap](#TagsMap-typedef)
- [enum KExiv2::XmpTagType](#XmpTagType-enum)

## Public Functions

- [KExiv2()](#KExiv2)
- [KExiv2(const KExiv2Iface::KExiv2Data &data)](#KExiv2-2)
- [KExiv2(const QString &filePath)](#KExiv2-3)
- [KExiv2(const KExiv2Iface::KExiv2 &metadata)](#KExiv2-1)
- [~KExiv2()](#dtor.KExiv2)
- [bool addToXmpTagStringBag(const char \*xmpTagName, const QStringList &entriesToAdd, bool setProgramName) const](#addToXmpTagStringBag)
- [bool applyChanges() const](#applyChanges)
- [bool clearComments() const](#clearComments)
- [bool clearExif() const](#clearExif)
- [bool clearIptc() const](#clearIptc)
- [bool clearXmp() const](#clearXmp)
- [QString createExifUserStringFromValue(const char \*exifTagName, const QVariant &val, bool escapeCR = true)](#createExifUserStringFromValue)
- [KExiv2Iface::KExiv2Data data() const](#data)
- [QByteArray getComments() const](#getComments)
- [QString getCommentsDecoded() const](#getCommentsDecoded)
- [QDateTime getDigitizationDateTime(bool fallbackToCreationTime = false) const](#getDigitizationDateTime)
- [QString getExifComment() const](#getExifComment)
- [QByteArray getExifEncoded(bool addExifHeader = false) const](#getExifEncoded)
- [QByteArray getExifTagData(const char \*exifTagName) const](#getExifTagData)
- [QString getExifTagDescription(const char \*exifTagName)](#getExifTagDescription)
- [bool getExifTagLong(const char \*exifTagName, long &val) const](#getExifTagLong)
- [bool getExifTagLong(const char \*exifTagName, long &val, int component) const](#getExifTagLong-1)
- [bool getExifTagRational(const char \*exifTagName, long &num, long &den, int component = 0) const](#getExifTagRational)
- [QString getExifTagString(const char \*exifTagName, bool escapeCR = true) const](#getExifTagString)
- [QString getExifTagTitle(const char \*exifTagName)](#getExifTagTitle)
- [QVariant getExifTagVariant(const char \*exifTagName, bool rationalAsListOfInts = true, bool escapeCR = true, int component = 0) const](#getExifTagVariant)
- [KExiv2::MetaDataMap getExifTagsDataList(const QStringList &exifKeysFilter = QStringList(), bool invertSelection = false) const](#getExifTagsDataList)
- [QImage getExifThumbnail(bool fixOrientation) const](#getExifThumbnail)
- [QString getFilePath() const](#getFilePath)
- [bool getGPSAltitude(double \*const altitude) const](#getGPSAltitude)
- [bool getGPSInfo(double &altitude, double &latitude, double &longitude) const](#getGPSInfo)
- [bool getGPSLatitudeNumber(double \*const latitude) const](#getGPSLatitudeNumber)
- [QString getGPSLatitudeString() const](#getGPSLatitudeString)
- [bool getGPSLongitudeNumber(double \*const longitude) const](#getGPSLongitudeNumber)
- [QString getGPSLongitudeString() const](#getGPSLongitudeString)
- [KExiv2Iface::KExiv2::ImageColorWorkSpace getImageColorWorkSpace() const](#getImageColorWorkSpace)
- [QDateTime getImageDateTime() const](#getImageDateTime)
- [QSize getImageDimensions() const](#getImageDimensions)
- [KExiv2Iface::KExiv2::ImageOrientation getImageOrientation() const](#getImageOrientation)
- [bool getImagePreview(QImage &preview) const](#getImagePreview)
- [QByteArray getIptc(bool addIrbHeader = false) const](#getIptc)
- [QStringList getIptcKeywords() const](#getIptcKeywords)
- [QStringList getIptcSubCategories() const](#getIptcSubCategories)
- [QStringList getIptcSubjects() const](#getIptcSubjects)
- [QByteArray getIptcTagData(const char \*iptcTagName) const](#getIptcTagData)
- [QString getIptcTagDescription(const char \*iptcTagName)](#getIptcTagDescription)
- [QString getIptcTagString(const char \*iptcTagName, bool escapeCR = true) const](#getIptcTagString)
- [QString getIptcTagTitle(const char \*iptcTagName)](#getIptcTagTitle)
- [KExiv2::MetaDataMap getIptcTagsDataList(const QStringList &iptcKeysFilter = QStringList(), bool invertSelection = false) const](#getIptcTagsDataList)
- [KExiv2::TagsMap getIptcTagsList() const](#getIptcTagsList)
- [QStringList getIptcTagsStringList(const char \*iptcTagName, bool escapeCR = true) const](#getIptcTagsStringList)
- [KExiv2Iface::KExiv2::TagsMap getMakernoteTagsList() const](#getMakernoteTagsList)
- [QString getMimeType() const](#getMimeType)
- [QSize getPixelSize() const](#getPixelSize)
- [KExiv2Iface::KExiv2::TagsMap getStdExifTagsList() const](#getStdExifTagsList)
- [QByteArray getXmp() const](#getXmp)
- [QStringList getXmpKeywords() const](#getXmpKeywords)
- [QStringList getXmpSubCategories() const](#getXmpSubCategories)
- [QStringList getXmpSubjects() const](#getXmpSubjects)
- [QString getXmpTagDescription(const char \*xmpTagName)](#getXmpTagDescription)
- [QString getXmpTagString(const char \*xmpTagName, bool escapeCR = true) const](#getXmpTagString)
- [QStringList getXmpTagStringBag(const char \*xmpTagName, bool escapeCR) const](#getXmpTagStringBag)
- [QString getXmpTagStringLangAlt(const char \*xmpTagName, const QString &langAlt, bool escapeCR) const](#getXmpTagStringLangAlt)
- [KExiv2::AltLangMap getXmpTagStringListLangAlt(const char \*xmpTagName, bool escapeCR = true) const](#getXmpTagStringListLangAlt)
- [QStringList getXmpTagStringSeq(const char \*xmpTagName, bool escapeCR = true) const](#getXmpTagStringSeq)
- [QString getXmpTagTitle(const char \*xmpTagName)](#getXmpTagTitle)
- [QVariant getXmpTagVariant(const char \*xmpTagName, bool rationalAsListOfInts = true, bool stringEscapeCR = true) const](#getXmpTagVariant)
- [KExiv2::MetaDataMap getXmpTagsDataList(const QStringList &xmpKeysFilter = QStringList(), bool invertSelection = false) const](#getXmpTagsDataList)
- [KExiv2::TagsMap getXmpTagsList() const](#getXmpTagsList)
- [bool hasComments() const](#hasComments)
- [bool hasExif() const](#hasExif)
- [bool hasIptc() const](#hasIptc)
- [bool hasXmp() const](#hasXmp)
- [bool initializeGPSInfo(const bool setProgramName)](#initializeGPSInfo)
- [bool isEmpty() const](#isEmpty)
- [bool load(const QString &filePath) const](#load)
- [bool loadFromData(const QByteArray &imgData) const](#loadFromData)
- [int metadataWritingMode() const](#metadataWritingMode)
- [bool removeExifTag(const char \*exifTagName, bool setProgramName = true) const](#removeExifTag)
- [bool removeExifThumbnail() const](#removeExifThumbnail)
- [bool removeFromXmpTagStringBag(const char \*xmpTagName, const QStringList &entriesToRemove, bool setProgramName) const](#removeFromXmpTagStringBag)
- [bool removeGPSInfo(const bool setProgramName = true)](#removeGPSInfo)
- [bool removeIptcTag(const char \*iptcTagName, bool setProgramName = true) const](#removeIptcTag)
- [bool removeXmpKeywords(const QStringList &keywordsToRemove, bool setProgramName = true)](#removeXmpKeywords)
- [bool removeXmpSubCategories(const QStringList &categoriesToRemove, bool setProgramName = true)](#removeXmpSubCategories)
- [bool removeXmpSubjects(const QStringList &subjectsToRemove, bool setProgramName = true)](#removeXmpSubjects)
- [bool removeXmpTag(const char \*xmpTagName, bool setProgramName = true) const](#removeXmpTag)
- [bool rotateExifQImage(QImage &image, KExiv2Iface::KExiv2::ImageOrientation orientation) const](#rotateExifQImage)
- [bool save(const QString &filePath) const](#save)
- [bool setComments(const QByteArray &data) const](#setComments)
- [void setData(const KExiv2Iface::KExiv2Data &data)](#setData)
- [bool setExif(const QByteArray &data) const](#setExif)
- [bool setExifComment(const QString &comment, bool setProgramName = true) const](#setExifComment)
- [bool setExifTagData(const char \*exifTagName, const QByteArray &data, bool setProgramName = true) const](#setExifTagData)
- [bool setExifTagLong(const char \*exifTagName, long val, bool setProgramName = true) const](#setExifTagLong)
- [bool setExifTagRational(const char \*exifTagName, long num, long den, bool setProgramName = true) const](#setExifTagRational)
- [bool setExifTagString(const char \*exifTagName, const QString &value, bool setProgramName = true) const](#setExifTagString)
- [bool setExifTagVariant(const char \*exifTagName, const QVariant &data, bool rationalWantSmallDenominator = true, bool setProgramName = true) const](#setExifTagVariant)
- [bool setExifThumbnail(const QImage &thumb, bool setProgramName = true) const](#setExifThumbnail)
- [void setFilePath(const QString &path)](#setFilePath)
- [bool setGPSInfo(const double altitude, const QString &latitude, const QString &longitude, const bool setProgramName = true)](#setGPSInfo)
- [bool setGPSInfo(const double altitude, const double latitude, const double longitude, const bool setProgramName = true)](#setGPSInfo-1)
- [bool setGPSInfo(const double \*const altitude, const double latitude, const double longitude, const bool setProgramName = true)](#setGPSInfo-2)
- [bool setImageColorWorkSpace(KExiv2Iface::KExiv2::ImageColorWorkSpace workspace, bool setProgramName = true) const](#setImageColorWorkSpace)
- [bool setImageDateTime(const QDateTime &dateTime, bool setDateTimeDigitized = false, bool setProgramName = true) const](#setImageDateTime)
- [bool setImageDimensions(const QSize &size, bool setProgramName = true) const](#setImageDimensions)
- [bool setImageOrientation(KExiv2Iface::KExiv2::ImageOrientation orientation, bool setProgramName = true) const](#setImageOrientation)
- [bool setImagePreview(const QImage &preview, bool setProgramName = true) const](#setImagePreview)
- [bool setImageProgramId(const QString &program, const QString &version) const](#setImageProgramId)
- [bool setIptc(const QByteArray &data) const](#setIptc)
- [bool setIptcKeywords(const QStringList &oldKeywords, const QStringList &newKeywords, bool setProgramName = true) const](#setIptcKeywords)
- [bool setIptcSubCategories(const QStringList &oldSubCategories, const QStringList &newSubCategories, bool setProgramName = true) const](#setIptcSubCategories)
- [bool setIptcSubjects(const QStringList &oldSubjects, const QStringList &newSubjects, bool setProgramName = true) const](#setIptcSubjects)
- [bool setIptcTagData(const char \*iptcTagName, const QByteArray &data, bool setProgramName = true) const](#setIptcTagData)
- [bool setIptcTagString(const char \*iptcTagName, const QString &value, bool setProgramName = true) const](#setIptcTagString)
- [bool setIptcTagsStringList(const char \*iptcTagName, int maxSize, const QStringList &oldValues, const QStringList &newValues, bool setProgramName = true) const](#setIptcTagsStringList)
- [void setMetadataWritingMode(const int mode)](#setMetadataWritingMode)
- [bool setTiffThumbnail(const QImage &thumb, bool setProgramName = true) const](#setTiffThumbnail)
- [void setUpdateFileTimeStamp(bool on)](#setUpdateFileTimeStamp)
- [void setUseXMPSidecar4Reading(const bool on)](#setUseXMPSidecar4Reading)
- [void setWriteRawFiles(const bool on)](#setWriteRawFiles)
- [bool setXmp(const QByteArray &data) const](#setXmp)
- [bool setXmpKeywords(const QStringList &newKeywords, bool setProgramName = true) const](#setXmpKeywords)
- [bool setXmpSubCategories(const QStringList &newSubCategories, bool setProgramName = true) const](#setXmpSubCategories)
- [bool setXmpSubjects(const QStringList &newSubjects, bool setProgramName = true) const](#setXmpSubjects)
- [bool setXmpTagString(const char \*xmpTagName, const QString &value, bool setProgramName = true) const](#setXmpTagString)
- [bool setXmpTagString(const char \*xmpTagName, const QString &value, KExiv2Iface::KExiv2::XmpTagType type, bool setProgramName = true) const](#setXmpTagString-1)
- [bool setXmpTagStringBag(const char \*xmpTagName, const QStringList &bag, bool setProgramName = true) const](#setXmpTagStringBag)
- [bool setXmpTagStringLangAlt(const char \*xmpTagName, const QString &value, const QString &langAlt, bool setProgramName = true) const](#setXmpTagStringLangAlt)
- [bool setXmpTagStringListLangAlt(const char \*xmpTagName, const KExiv2::AltLangMap &values, bool setProgramName) const](#setXmpTagStringListLangAlt)
- [bool setXmpTagStringSeq(const char \*xmpTagName, const QStringList &seq, bool setProgramName = true) const](#setXmpTagStringSeq)
- [bool updateFileTimeStamp() const](#updateFileTimeStamp)
- [bool useXMPSidecar4Reading() const](#useXMPSidecar4Reading)
- [bool writeRawFiles() const](#writeRawFiles)
- [KExiv2Iface::KExiv2 &KExiv2::operator=(const KExiv2Iface::KExiv2 &metadata)](#operator-eq)

## Static Public Members

- [QString Exiv2Version()](#Exiv2Version)
- [bool canWriteComment(const QString &filePath)](#canWriteComment)
- [bool canWriteExif(const QString &filePath)](#canWriteExif)
- [bool canWriteIptc(const QString &filePath)](#canWriteIptc)
- [bool canWriteXmp(const QString &filePath)](#canWriteXmp)
- [bool cleanupExiv2()](#cleanupExiv2)
- [bool convertFromGPSCoordinateString(const QString &gpsString, double \*const coordinate)](#convertFromGPSCoordinateString)
- [bool convertFromGPSCoordinateString(const QString &coordinate, long \*const numeratorDegrees, long \*const denominatorDegrees, long \*const numeratorMinutes, long \*const denominatorMinutes, long \*const numeratorSeconds, long \*const denominatorSeconds, char \*const directionReference)](#convertFromGPSCoordinateString-1)
- [QString convertToGPSCoordinateString(const bool isLatitude, double coordinate)](#convertToGPSCoordinateString)
- [QString convertToGPSCoordinateString(const long numeratorDegrees, const long denominatorDegrees, const long numeratorMinutes, const long denominatorMinutes, const long numeratorSeconds, long denominatorSeconds, const char directionReference)](#convertToGPSCoordinateString-1)
- [void convertToRational(const double number, long \*const numerator, long \*const denominator, const int rounding)](#convertToRational)
- [void convertToRationalSmallDenominator(const double number, long \*const numerator, long \*const denominator)](#convertToRationalSmallDenominator)
- [bool convertToUserPresentableNumbers(const QString &coordinate, int \*const degrees, int \*const minutes, double \*const seconds, char \*const directionReference)](#convertToUserPresentableNumbers)
- [void convertToUserPresentableNumbers(const bool isLatitude, double coordinate, int \*const degrees, int \*const minutes, double \*const seconds, char \*const directionReference)](#convertToUserPresentableNumbers-1)
- [QString detectLanguageAlt(const QString &value, QString &lang)](#detectLanguageAlt)
- [bool hasSidecar(const QString &path)](#hasSidecar)
- [bool initializeExiv2()](#initializeExiv2)
- [bool registerXmpNameSpace(const QString &uri, const QString &prefix)](#registerXmpNameSpace)
- [QString sidecarFilePathForFile(const QString &path)](#sidecarFilePathForFile)
- [QString sidecarPath(const QString &path)](#sidecarPath)
- [QUrl sidecarUrl(const QString &path)](#sidecarUrl)
- [QUrl sidecarUrl(const QUrl &url)](#sidecarUrl-1)
- [bool supportMetadataWritting(const QString &typeMime)](#supportMetadataWritting)
- [bool supportXmp()](#supportXmp)
- [bool unregisterXmpNameSpace(const QString &uri)](#unregisterXmpNameSpace)
- [QString version()](#version)

## Protected Functions

- [bool setProgramId(bool on = true) const](#setProgramId)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### KExiv2::AltLangMap {#AltLangMap-typedef}

A map used to store a list of Alternative Language values.

The map key is the language code following RFC3066 notation (like "fr-FR" for French), and the map value the text.

### enum KExiv2::ImageColorWorkSpace {#ImageColorWorkSpace-enum}

The image color workspace values given by Exif metadata.

| Constant |   |
| --- | --- |
| `KExiv2Iface::KExiv2::WORKSPACE_UNSPECIFIED` | `0` |
| `KExiv2Iface::KExiv2::WORKSPACE_SRGB` | `1` |
| `KExiv2Iface::KExiv2::WORKSPACE_ADOBERGB` | `2` |
| `KExiv2Iface::KExiv2::WORKSPACE_UNCALIBRATED` | `65535` |

### enum KExiv2::ImageOrientation {#ImageOrientation-enum}

The image orientation values given by Exif metadata.

| Constant |   |
| --- | --- |
| `KExiv2Iface::KExiv2::ORIENTATION_UNSPECIFIED` | `0` |
| `KExiv2Iface::KExiv2::ORIENTATION_NORMAL` | `1` |
| `KExiv2Iface::KExiv2::ORIENTATION_HFLIP` | `2` |
| `KExiv2Iface::KExiv2::ORIENTATION_ROT_180` | `3` |
| `KExiv2Iface::KExiv2::ORIENTATION_VFLIP` | `4` |
| `KExiv2Iface::KExiv2::ORIENTATION_ROT_90_HFLIP` | `5` |
| `KExiv2Iface::KExiv2::ORIENTATION_ROT_90` | `6` |
| `KExiv2Iface::KExiv2::ORIENTATION_ROT_90_VFLIP` | `7` |
| `KExiv2Iface::KExiv2::ORIENTATION_ROT_270` | `8` |

### KExiv2::MetaDataMap {#MetaDataMap-typedef}

A map used to store Tags Key and Tags Value.

### enum KExiv2::MetadataWritingMode {#MetadataWritingMode-enum}

The image metadata writing mode, between image file metadata and XMP sidecar file, depending on the context.

| Constant | Value | Description |
| --- | --- | --- |
| `KExiv2Iface::KExiv2::WRITETOIMAGEONLY` | `0` | Write metadata to image file only. |
| `KExiv2Iface::KExiv2::WRITETOSIDECARONLY` | `1` | Write metadata to sidecar file only. |
| `KExiv2Iface::KExiv2::WRITETOSIDECARANDIMAGE` | `2` | Write metadata to image and sidecar files. |
| `KExiv2Iface::KExiv2::WRITETOSIDECARONLY4READONLYFILES` | `3` | Write metadata to sidecar file only for read only images such as RAW files for example. |

*See also* [metadataWritingMode](kexiv2iface-kexiv2.md#metadataWritingMode)()

### KExiv2::TagsMap {#TagsMap-typedef}

A map used to store Tags Key and a list of Tags properties:

- name
- title
- description

### enum KExiv2::XmpTagType {#XmpTagType-enum}

Xmp tag types, used by setXmpTag, only first three types are used.

| Constant |   |
| --- | --- |
| `KExiv2Iface::KExiv2::NormalTag` | `0` |
| `KExiv2Iface::KExiv2::ArrayBagTag` | `1` |
| `KExiv2Iface::KExiv2::StructureTag` | `2` |
| `KExiv2Iface::KExiv2::ArrayLangTag` | `3` |
| `KExiv2Iface::KExiv2::ArraySeqTag` | `4` |

## Member Function Documentation {#member-function-documentation}

### KExiv2::KExiv2() {#KExiv2}

Standard constructor.

### KExiv2::KExiv2(const KExiv2Iface::KExiv2Data &*data*) {#KExiv2-2}

Constructor to load from parsed `data`.

### KExiv2::KExiv2(const QString &*filePath*) {#KExiv2-3}

Contructor to load metadata from an image in `filePath`.

### KExiv2::KExiv2(const KExiv2Iface::KExiv2 &*metadata*) {#KExiv2-1}

Copy constructor.

### \[virtual noexcept\] KExiv2::~KExiv2() {#dtor.KExiv2}

Standard destructor.

### \[static\] QString KExiv2::Exiv2Version() {#Exiv2Version}

Returns a string version of Exiv2 release in format "major.minor.patch".

### bool KExiv2::addToXmpTagStringBag(const char \**xmpTagName*, const QStringList &*entriesToAdd*, bool *setProgramName*) const {#addToXmpTagStringBag}

Sets an XMP tag content `xmpTagName` using a list of strings defined by the `entriesToAdd`.

The existing entries are preserved.

This method will compare all new entries with all already existing entries to prevent duplicates in the image.

Returns `true` if the entries have been added to metadata.

### bool KExiv2::applyChanges() const {#applyChanges}

The same as [save](kexiv2iface-kexiv2.md#save)(), but it applies to the current image.

Returns `true` if the metadata has been saved into file.

### \[static\] bool KExiv2::canWriteComment(const QString &*filePath*) {#canWriteComment}

Returns `true` if Comments can be written in file in the given `filePath`.

### \[static\] bool KExiv2::canWriteExif(const QString &*filePath*) {#canWriteExif}

Returns `true` if Exif can be written to the file in the given `filePath`.

### \[static\] bool KExiv2::canWriteIptc(const QString &*filePath*) {#canWriteIptc}

Returns `true` if IPTC can be written to file in the given `filePath`.

### \[static\] bool KExiv2::canWriteXmp(const QString &*filePath*) {#canWriteXmp}

Returns `true` if XMP can be written to file in `filePath`.

### \[static\] bool KExiv2::cleanupExiv2() {#cleanupExiv2}

Returns `true` if Exiv2 library memory allocations are cleaned properly.

This method must be called after using libkexiv2 with multithreading.

It cleans up memory used by Adobe XMP SDK.

See B.K.O \#166424 for details.

### bool KExiv2::clearComments() const {#clearComments}

Clears the Comments metadata container in memory.

### bool KExiv2::clearExif() const {#clearExif}

Clears the Exif metadata container in memory.

### bool KExiv2::clearIptc() const {#clearIptc}

Clears the IPTC metadata container in memory.

### bool KExiv2::clearXmp() const {#clearXmp}

Clears the XMP metadata container in memory.

### \[static\] bool KExiv2::convertFromGPSCoordinateString(const QString &*gpsString*, double \*const *coordinate*) {#convertFromGPSCoordinateString}

Converts a GPSCoordinate string as defined by XMP to a double floating point number in degrees where the sign determines the direction ref (North + / South - ; East + / West -).

Returns `true` if the conversion was successful.

### \[static\] bool KExiv2::convertFromGPSCoordinateString(const QString &*coordinate*, long \*const *numeratorDegrees*, long \*const *denominatorDegrees*, long \*const *numeratorMinutes*, long \*const *denominatorMinutes*, long \*const *numeratorSeconds*, long \*const *denominatorSeconds*, char \*const *directionReference*) {#convertFromGPSCoordinateString-1}

Converts a GPSCoordinate string as defined by XMP to three rationals and the direction reference.

Returns `true` if the conversion was successful.

If minutes is given in the fractional form, a denominator of 1000000 for the minutes will be used.

### \[static\] QString KExiv2::convertToGPSCoordinateString(const bool *isLatitude*, double *coordinate*) {#convertToGPSCoordinateString}

Converts a GPS position stored as double floating point number in degrees to the form described as GPSCoordinate in the XMP specification.

### \[static\] QString KExiv2::convertToGPSCoordinateString(const long *numeratorDegrees*, const long *denominatorDegrees*, const long *numeratorMinutes*, const long *denominatorMinutes*, const long *numeratorSeconds*, long *denominatorSeconds*, const char *directionReference*) {#convertToGPSCoordinateString-1}

Converts a GPS position stored as rationals in Exif to the form described as GPSCoordinate in the XMP specification, either in the from "256,45,34N" or "256,45.566667N"

### \[static\] void KExiv2::convertToRational(const double *number*, long \*const *numerator*, long \*const *denominator*, const int *rounding*) {#convertToRational}

Converts `number` to a rational value, returned in the `numerator` and `denominator` parameters.

Set the precision using the `rounding` parameter.

Use this method if you want to retrieve a most exact rational for a number without further properties, without any requirements for the denominator.

### \[static\] void KExiv2::convertToRationalSmallDenominator(const double *number*, long \*const *numerator*, long \*const *denominator*) {#convertToRationalSmallDenominator}

Converts a `number` to a rational value, returned in the `numerator` and `denominator` parameters.

This method will be able to retrieve a rational number from a double.

If you constructed your double with 1.0 / 4786.0, this method will retrieve 1 / 4786.

If your number is not expected to be rational, use [convertToRational](kexiv2iface-kexiv2.md#convertToRational)() which is just as exact with rounding = 4 and more exact with rounding \> 4.

### \[static\] bool KExiv2::convertToUserPresentableNumbers(const QString &*coordinate*, int \*const *degrees*, int \*const *minutes*, double \*const *seconds*, char \*const *directionReference*) {#convertToUserPresentableNumbers}

Converts a GPSCoordinate string to user presentable numbers, integer degrees and minutes and double floating point seconds, and a direction reference ('N' or 'S', 'E' or 'W').

### \[static\] void KExiv2::convertToUserPresentableNumbers(const bool *isLatitude*, double *coordinate*, int \*const *degrees*, int \*const *minutes*, double \*const *seconds*, char \*const *directionReference*) {#convertToUserPresentableNumbers-1}

Converts a double floating point number to user presentable numbers, integer degrees and minutes and double floating point seconds, and a direction reference ('N' or 'S', 'E' or 'W').

This method needs to know for the direction reference if the latitude or the longitude is meant by the double parameter.

### QString KExiv2::createExifUserStringFromValue(const char \**exifTagName*, const QVariant &*val*, bool *escapeCR* = true) {#createExifUserStringFromValue}

Takes a [QVariant](https://doc.qt.io/qt-6/qvariant.html) value `val` as it could have been retrieved by [getExifTagVariant](kexiv2iface-kexiv2.md#getExifTagVariant)() with the given `exifTagName`, and returns its value properly converted to a string (including translations from Exiv2).

This is equivalent to calling [getExifTagString](kexiv2iface-kexiv2.md#getExifTagString)() directly.

If escapeCR is `true` CR characters will be removed from the result.

### KExiv2Iface::KExiv2Data KExiv2::data() const {#data}

*See also* [setData](kexiv2iface-kexiv2.md#setData)()

### \[static\] QString KExiv2::detectLanguageAlt(const QString &*value*, QString &*lang*) {#detectLanguageAlt}

Language Alternative autodetection.

Returns a [QString](https://doc.qt.io/qt-6/qstring.html) without language alternative header.

Header is saved into `lang`. If no language alternative is found, `value` is returned as well and `lang` is set to a null string.

### QByteArray KExiv2::getComments() const {#getComments}

Returns a Qt byte array copy of Comments container acquired from the current image.

Comments are a JFIF section of JPEG images.

Look at the Exiv2 API for more information.

Returns a null Qt byte array if there is no Comments metadata in memory.

### QString KExiv2::getCommentsDecoded() const {#getCommentsDecoded}

Returns a Qt string object of Comments from the current image decoded using detectEncodingAndDecode().

Returns a null string if there is no Comments metadata available.

### QDateTime KExiv2::getDigitizationDateTime(bool *fallbackToCreationTime* = false) const {#getDigitizationDateTime}

Returns the digitization timestamp of the image.

First Exif information is checked, then IPTC.

If no digitization timestamp is found, [getImageDateTime](kexiv2iface-kexiv2.md#getImageDateTime)() is called if `fallbackToCreationTime` is `true`, or a null [QDateTime](https://doc.qt.io/qt-6/qdatetime.html) is returned if `fallbackToCreationTime` is `false`.

### QString KExiv2::getExifComment() const {#getExifComment}

Returns a [QString](https://doc.qt.io/qt-6/qstring.html) copy of Exif user comments.

Returns a null string if user comments cannot be found.

### QByteArray KExiv2::getExifEncoded(bool *addExifHeader* = false) const {#getExifEncoded}

Returns the Exif data encoded to a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) in a form suitable for storage in a JPEG image.

> **Note:** This encoding is a lossy operation.

Set `addExifHeader` to `true` to add an Exif header to the Exif metadata.

Returns a null Qt byte array if there is no Exif metadata in memory.

### QByteArray KExiv2::getExifTagData(const char \**exifTagName*) const {#getExifTagData}

Gets an Exif tag content `exifTagName` as a byte array.

Returns an empty byte array if the Exif tag cannot be found.

### QString KExiv2::getExifTagDescription(const char \**exifTagName*) {#getExifTagDescription}

Returns the Exif Tag description for the `exifTagName` or a null string.

### bool KExiv2::getExifTagLong(const char \**exifTagName*, long &*val*) const {#getExifTagLong}

Gets an Exif tag content `exifTagName` as a long value `val`.

Returns `true` if the Exif tag is found.

### bool KExiv2::getExifTagLong(const char \**exifTagName*, long &*val*, int *component*) const {#getExifTagLong-1}

Gets an Exif tag content `exifTagName` as a long value `val`.

Returns `true` if the Exif tag be found.

### bool KExiv2::getExifTagRational(const char \**exifTagName*, long &*num*, long &*den*, int *component* = 0) const {#getExifTagRational}

Gets the `component` index of an Exif tags content `exifTagName` as a rational value with the numerator `num` and denominator `den`.

Returns `true` if the Exif tag is found.

### QString KExiv2::getExifTagString(const char \**exifTagName*, bool *escapeCR* = true) const {#getExifTagString}

Gets an Exif tags content `exifTagName` as a string.

If `escapeCR` is `true`, the CR characters will be removed.

Returns a null string if the Exif tag cannot be found.

### QString KExiv2::getExifTagTitle(const char \**exifTagName*) {#getExifTagTitle}

Returns the Exif Tag title for the `exifTagName` or a null string.

### QVariant KExiv2::getExifTagVariant(const char \**exifTagName*, bool *rationalAsListOfInts* = true, bool *escapeCR* = true, int *component* = 0) const {#getExifTagVariant}

Gets an Exif tags content `exifTagName` as a [QVariant](https://doc.qt.io/qt-6/qvariant.html).

Returns a null [QVariant](https://doc.qt.io/qt-6/qvariant.html) if the Exif tag cannot be found.

For string and integer values the matching [QVariant](https://doc.qt.io/qt-6/qvariant.html) types will be used, for date and time values QVariant::DateTime.

Rationals will be returned as QVariant::List with two integer QVariants (numerator, denominator) if `rationalAsListOfInts` is `true`, as double if `rationalAsListOfInts` is `false`.

An exif tag of numerical type may contain more than one value; set `component` to the desired index.

### KExiv2::MetaDataMap KExiv2::getExifTagsDataList(const QStringList &*exifKeysFilter* = QStringList(), bool *invertSelection* = false) const {#getExifTagsDataList}

Returns a map of Exif tags name/value found in the metadata sorted by Exif keys given by `exifKeysFilter`.

The `exifKeysFilter` is a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) of Exif keys.

For example, if you use the string list given below:

"Iop"

"Thumbnail"

"Image"

"Photo"

The list can be empty to not filter output.

Given the above example, this method will return a map of all Exif tags which:

- will include "Iop", or "Thumbnail", or "Image", or "Photo" in the Exif tag keys if `invertSelection` is `false`.
- will not include "Iop", or "Thumbnail", or "Image", or "Photo" in the Exif tag keys if `invertSelection` is `true`.

### QImage KExiv2::getExifThumbnail(bool *fixOrientation*) const {#getExifThumbnail}

Returns a QImage copy of the Exif thumbnail image.

Returns a null image if the thumbnail cannot be found.

The `fixOrientation` parameter will rotate the thumbnail automatically if Exif orientation tags information is attached to the thumbnail.

### QString KExiv2::getFilePath() const {#getFilePath}

Returns the file path of the current image.

### bool KExiv2::getGPSAltitude(double \*const *altitude*) const {#getGPSAltitude}

Gets GPS altitude information, in meters, relative to sea level (positive sign above sea level).

### bool KExiv2::getGPSInfo(double &*altitude*, double &*latitude*, double &*longitude*) const {#getGPSInfo}

Gets all GPS location information set in the image.

Returns `true` if all information can be found.

### bool KExiv2::getGPSLatitudeNumber(double \*const *latitude*) const {#getGPSLatitudeNumber}

Gets GPS location information set in the image, as a double floating point number as in degrees where the sign determines the direction ref (North + / South - ; East + / West -).

Returns `true` if the information is available.

### QString KExiv2::getGPSLatitudeString() const {#getGPSLatitudeString}

Gets GPS location information set in the image, in the GPSCoordinate format as described in the XMP specification.

Returns a null string if the information cannot be found.

### bool KExiv2::getGPSLongitudeNumber(double \*const *longitude*) const {#getGPSLongitudeNumber}

Gets GPS location information set in the image, as a double floating point number as in degrees where the sign determines the direction ref (North + / South - ; East + / West -).

Returns `true` if the information is available.

### QString KExiv2::getGPSLongitudeString() const {#getGPSLongitudeString}

Gets GPS location information set in the image, in the GPSCoordinate format as described in the XMP specification.

Returns a null string in the information cannot be found.

### KExiv2Iface::KExiv2::ImageColorWorkSpace KExiv2::getImageColorWorkSpace() const {#getImageColorWorkSpace}

Returns the image color-space set in Exif metadata.

The makernotes of the image are also parsed to get this information.

*See also* [ImageColorWorkSpace](kexiv2iface-kexiv2.md#ImageColorWorkSpace-enum)

### QDateTime KExiv2::getImageDateTime() const {#getImageDateTime}

Returns the timestamp of the image.

First Exif information is checked, then IPTC if the image don't have Exif information.

If no timestamp is found, a null date is returned.

### QSize KExiv2::getImageDimensions() const {#getImageDimensions}

Returns the size of the image in pixels using Exif tags.

Returns a null dimension if size cannot be found.

### KExiv2Iface::KExiv2::ImageOrientation KExiv2::getImageOrientation() const {#getImageOrientation}

Returns the image orientation set in Exif metadata.

The makernotes of image are also parsed to get this information.

*See also* [ImageOrientation](kexiv2iface-kexiv2.md#ImageOrientation-enum)

### bool KExiv2::getImagePreview(QImage &*preview*) const {#getImagePreview}

Returns a QImage copy of the IPTC `preview` image.

Returns a null image if the preview cannot be found.

### QByteArray KExiv2::getIptc(bool *addIrbHeader* = false) const {#getIptc}

Returns a Qt byte array copy of the IPTC container acquired from the current image.

Set `addIrbHeader` to `true` to add an Irb header to IPTC metadata.

Returns a null [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) if there is no IPTC metadata in memory.

### QStringList KExiv2::getIptcKeywords() const {#getIptcKeywords}

Returns a strings list of IPTC keywords from the image.

Returns an empty list if no keywords are set.

### QStringList KExiv2::getIptcSubCategories() const {#getIptcSubCategories}

Returns a strings list of IPTC subcategories from the image.

Returns an empty list if no subcategory is set.

### QStringList KExiv2::getIptcSubjects() const {#getIptcSubjects}

Returns a strings list of IPTC subjects from the image.

Returns an empty list if no subjects are set.

### QByteArray KExiv2::getIptcTagData(const char \**iptcTagName*) const {#getIptcTagData}

Gets an IPTC tag content `iptcTagName` as a byte array.

Returns an empty byte array if the IPTC tag cannot be found.

### QString KExiv2::getIptcTagDescription(const char \**iptcTagName*) {#getIptcTagDescription}

Returns the IPTC Tag description for `iptcTagName` or a null string.

### QString KExiv2::getIptcTagString(const char \**iptcTagName*, bool *escapeCR* = true) const {#getIptcTagString}

Gets an IPTC tag content `iptcTagName` as a string.

If `escapeCR` is set to `true`, the CR characters will be removed.

Returns a null string if the IPTC tag cannot be found.

### QString KExiv2::getIptcTagTitle(const char \**iptcTagName*) {#getIptcTagTitle}

Returns the IPTC Tag title for `iptcTagName` or a null string.

### KExiv2::MetaDataMap KExiv2::getIptcTagsDataList(const QStringList &*iptcKeysFilter* = QStringList(), bool *invertSelection* = false) const {#getIptcTagsDataList}

Returns a map of IPTC tags name/value found in the metadata sorted by IPTC keys given by `iptcKeysFilter`.

`iptcKeysFilter` is a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) of IPTC keys.

For example, if you use the string list given below:

"Envelope"

"Application2"

List can be empty to not filter output.

Given the above example, this method will return a map of all IPTC tags which:

- will include "Envelope", or "Application2" in the IPTC tag keys if `invertSelection` is `false`.
- will not include "Envelope", or "Application2" in the IPTC tag keys if `invertSelection` is `true`.

### KExiv2::TagsMap KExiv2::getIptcTagsList() const {#getIptcTagsList}

Returns a map of all standard IPTC tags supported by Exiv2.

### QStringList KExiv2::getIptcTagsStringList(const char \**iptcTagName*, bool *escapeCR* = true) const {#getIptcTagsStringList}

Gets the values of all IPTC tags with the given tag name `iptcTagName` in a string list.

Returns an empty list if no tag is found.

(In IPTC, there can be multiple tags with the same name)

If `escapeCR` is set to `true`, the CR characters will be removed.

### KExiv2Iface::KExiv2::TagsMap KExiv2::getMakernoteTagsList() const {#getMakernoteTagsList}

Returns a map of all non-standard Exif tags (makernotes) supported by Exiv2.

### QString KExiv2::getMimeType() const {#getMimeType}

Returns the mime type of this image.

The information is read from the file; see [getPixelSize](kexiv2iface-kexiv2.md#getPixelSize)() to know when it is available.

### QSize KExiv2::getPixelSize() const {#getPixelSize}

Returns the pixel size of the current image.

This information is read from the file, not from the metadata.

The returned [QSize](https://doc.qt.io/qt-6/qsize.html) is valid if the [KExiv2](kexiv2iface-kexiv2.md) object was *constructed* by reading a file or image data; the information is not available when the object was created from [KExiv2Data](kexiv2iface-kexiv2data.md).

Note that in the Exif or XMP metadata, there may be fields describing the image size. These fields are not accessed by this method.

When replacing the metadata with [setData](kexiv2iface-kexiv2.md#setData)(), the metadata may change; this information always keeps referring to the file it was initially read from.

### KExiv2Iface::KExiv2::TagsMap KExiv2::getStdExifTagsList() const {#getStdExifTagsList}

Returns a map of all standard Exif tags supported by Exiv2.

### QByteArray KExiv2::getXmp() const {#getXmp}

Returns a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) copy of the XMP container acquired from the current image.

Returns a null [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) if there is no XMP metadata in memory.

### QStringList KExiv2::getXmpKeywords() const {#getXmpKeywords}

Returns a strings list of XMP keywords from the image.

Returns a null string list if no keywords are set.

### QStringList KExiv2::getXmpSubCategories() const {#getXmpSubCategories}

Returns a string list of XMP subcategories from the image.

Returns a null string list if no subcategories are set.

### QStringList KExiv2::getXmpSubjects() const {#getXmpSubjects}

Returns a string list of XMP subjects from the image.

Returns a null string list if no subjects are set.

### QString KExiv2::getXmpTagDescription(const char \**xmpTagName*) {#getXmpTagDescription}

Returns the XMP Tag description for `xmpTagName` or a null string.

### QString KExiv2::getXmpTagString(const char \**xmpTagName*, bool *escapeCR* = true) const {#getXmpTagString}

Gets an XMP tag content `xmpTagName` as a string.

If `escapeCR` is set to `true`, the CR characters will be removed.

Returns a null string if the XMP tag cannot be found.

### QStringList KExiv2::getXmpTagStringBag(const char \**xmpTagName*, bool *escapeCR*) const {#getXmpTagStringBag}

Gets an XMP tag content `xmpTagName` as a bag of strings.

If `escapeCR` is set to `true`, the CR characters will be removed from strings.

Returns a null string list if the XMP tag cannot be found.

### QString KExiv2::getXmpTagStringLangAlt(const char \**xmpTagName*, const QString &*langAlt*, bool *escapeCR*) const {#getXmpTagStringLangAlt}

Gets an XMP tag content `xmpTagName` as a string set with an alternative language header `langAlt` (like "fr-FR" for French - RFC3066 notation).

If `escapeCR` is set to `true`, the CR characters will be removed.

Returns a null string if the XMP tag cannot be found.

### KExiv2::AltLangMap KExiv2::getXmpTagStringListLangAlt(const char \**xmpTagName*, bool *escapeCR* = true) const {#getXmpTagStringListLangAlt}

Gets all redundant Alternative Language XMP tags content `xmpTagName` as a map.

See [AltLangMap](kexiv2iface-kexiv2.md#AltLangMap-typedef) class description for details.

If `escapeCR` is set to `true`, the CR characters will be removed from strings.

Returns null string list if the XMP tag cannot be found.

### QStringList KExiv2::getXmpTagStringSeq(const char \**xmpTagName*, bool *escapeCR* = true) const {#getXmpTagStringSeq}

Gets an XMP tag content `xmpTagName` as a sequence of strings.

If `escapeCR` is set to `true`, the CR characters will be removed from strings.

Returns a null string list if the XMP tag cannot be found.

### QString KExiv2::getXmpTagTitle(const char \**xmpTagName*) {#getXmpTagTitle}

Returns the XMP Tag title for `xmpTagName` or a null string.

### QVariant KExiv2::getXmpTagVariant(const char \**xmpTagName*, bool *rationalAsListOfInts* = true, bool *stringEscapeCR* = true) const {#getXmpTagVariant}

Gets an XMP tag content `xmpTagName` as a [QVariant](https://doc.qt.io/qt-6/qvariant.html).

Returns a null [QVariant](https://doc.qt.io/qt-6/qvariant.html) if the XMP tag cannot be found.

For string and integer values the matching [QVariant](https://doc.qt.io/qt-6/qvariant.html) types will be used, for date and time values QVariant::DateTime.

Rationals will be returned as QVariant::List with two integer QVariants (numerator, denominator) if `rationalAsListOfInts` is `true`, as double if `rationalAsListOfInts` is `false`.

Arrays (ordered, unordered, alternative) are returned as a [QStringList](https://doc.qt.io/qt-6/qstringlist.html).

LangAlt values will have type Map (`QMap<QString, QVariant>`) with the language code as key and the contents as value, of type [QString](https://doc.qt.io/qt-6/qstring.html).

### KExiv2::MetaDataMap KExiv2::getXmpTagsDataList(const QStringList &*xmpKeysFilter* = QStringList(), bool *invertSelection* = false) const {#getXmpTagsDataList}

Returns a map of XMP tags name/value pairs found in the metadata sorted by XMP keys given by `xmpKeysFilter`.

`xmpKeysFilter` is a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) of XMP keys.

For example, if you use the string list given below:

"dc" // Dubling Core schema.

"xmp" // Standard XMP schema.

List can be empty to not filter output.

Given the above example, this method will return a map of all XMP tags which:

- will include "dc", or "xmp" in the XMP tag keys if `invertSelection` is `false`.
- will not include "dc", or "xmp" in the XMP tag keys if `invertSelection` is `true`.

### KExiv2::TagsMap KExiv2::getXmpTagsList() const {#getXmpTagsList}

Returns a map of all standard XMP tags supported by Exiv2.

### bool KExiv2::hasComments() const {#hasComments}

Returns `true` if metadata container in memory has Comments.

### bool KExiv2::hasExif() const {#hasExif}

Returns `true` if the metadata container in memory has Exif.

### bool KExiv2::hasIptc() const {#hasIptc}

Returns `true` if metadata container in memory has IPTC.

### \[static\] bool KExiv2::hasSidecar(const QString &*path*) {#hasSidecar}

Performs a [QFileInfo](https://doc.qt.io/qt-6/qfileinfo.html) based check if the file in the given file `path` has a sidecar.

### bool KExiv2::hasXmp() const {#hasXmp}

Returns `true` if the metadata container in memory has XMP.

### \[static\] bool KExiv2::initializeExiv2() {#initializeExiv2}

Returns `true` if Exiv2 library initialization is done properly.

This method must be called before using libkexiv2 with multithreading.

It initializes several non re-entrancy code from Adobe XMP SDK.

See B.K.O \#166424 for details.

Call [cleanupExiv2](kexiv2iface-kexiv2.md#cleanupExiv2)() to clean things up later.

### bool KExiv2::initializeGPSInfo(const bool *setProgramName*) {#initializeGPSInfo}

Makes sure all static required GPS EXIF and XMP tags exist.

### bool KExiv2::isEmpty() const {#isEmpty}

Returns `true` if the metadata container in memory has no Comments, Exif, IPTC, and XMP.

### \[virtual\] bool KExiv2::load(const QString &*filePath*) const {#load}

Load all metadata (Exif, IPTC, XMP, and JFIF Comments) from a picture (JPEG, RAW, TIFF, PNG, DNG, etc...).

Returns `true` if the metadata has been loaded successfully from file in `filePath`.

### bool KExiv2::loadFromData(const QByteArray &*imgData*) const {#loadFromData}

Load all metadata (Exif, IPTC, XMP, and JFIF Comments) from a byte array.

Returns `true` if the metadata has been loaded successfully from `imgData`.

### int KExiv2::metadataWritingMode() const {#metadataWritingMode}

Returns the metadata writing mode.

*See also* [MetadataWritingMode](kexiv2iface-kexiv2.md#MetadataWritingMode-enum), [setMetadataWritingMode](kexiv2iface-kexiv2.md#setMetadataWritingMode)()

### \[static\] bool KExiv2::registerXmpNameSpace(const QString &*uri*, const QString &*prefix*) {#registerXmpNameSpace}

Registers a namespace which Exiv2 doesn't know yet.

This is only needed when new XMP properties are added manually.

The `uri` is the namespace url and prefix the string used to construct new XMP key.

> **Note:** If the XMP metadata is read from an image, namespaces are decoded and registered by Exiv2 at the same time.

### bool KExiv2::removeExifTag(const char \**exifTagName*, bool *setProgramName* = true) const {#removeExifTag}

Removes the Exif tag `exifTagName` from the Exif metadata.

Returns `true` if the Exif tag is removed successfully or if no tag was present.

### bool KExiv2::removeExifThumbnail() const {#removeExifThumbnail}

Remove the Exif thumbnail from the image.

### bool KExiv2::removeFromXmpTagStringBag(const char \**xmpTagName*, const QStringList &*entriesToRemove*, bool *setProgramName*) const {#removeFromXmpTagStringBag}

Removes the XMP tag entries `entriesToRemove` for the XMP tag content `xmpTagName` from the entries in the metadata.

Returns `true` if the tag entries are no longer contained in the metadata.

All other entries are preserved.

### bool KExiv2::removeGPSInfo(const bool *setProgramName* = true) {#removeGPSInfo}

Removes all Exif tags relevant to the GPS location information.

Returns `true` if all tags have been removed successfully from the metadata.

### bool KExiv2::removeIptcTag(const char \**iptcTagName*, bool *setProgramName* = true) const {#removeIptcTag}

Removes all instances of the IPTC tag `iptcTagName` from the IPTC metadata.

Returns `true` if all tags have been removed successfully (or none were present).

### bool KExiv2::removeXmpKeywords(const QStringList &*keywordsToRemove*, bool *setProgramName* = true) {#removeXmpKeywords}

Removes the XMP keywords `keywordsToRemove` from the keywords in the metadata.

Returns `true` if the keywords are no longer contained in the metadata.

### bool KExiv2::removeXmpSubCategories(const QStringList &*categoriesToRemove*, bool *setProgramName* = true) {#removeXmpSubCategories}

Removes the XMP sub `categoriesToRemove` from the subcategories in the metadata.

Returns `true` if the subjects are no longer contained in the metadata.

### bool KExiv2::removeXmpSubjects(const QStringList &*subjectsToRemove*, bool *setProgramName* = true) {#removeXmpSubjects}

Removes the XMP `subjectsToRemove` from the subjects in the metadata.

Returns `true` if the subjects are no longer contained in the metadata.

### bool KExiv2::removeXmpTag(const char \**xmpTagName*, bool *setProgramName* = true) const {#removeXmpTag}

Removes the XMP tag `xmpTagName` from XMP metadata.

Returns `true` if the tag is removed successfully or if no tag was present.

### bool KExiv2::rotateExifQImage(QImage &*image*, KExiv2Iface::KExiv2::ImageOrientation *orientation*) const {#rotateExifQImage}

Fixes orientation of a QImage `image` according to the Exif `orientation` tag.

Returns `true` if image is rotated, `false` otherwise.

### bool KExiv2::save(const QString &*filePath*) const {#save}

Saves all metadata to a file in `filePath`.

This one can be different from the original picture to perform a transfer operation.

Returns `true` if the metadata has been saved to the file.

### bool KExiv2::setComments(const QByteArray &*data*) const {#setComments}

Sets the Comments `data` using a Qt byte array.

Returns `true` if Comments metadata has been changed in memory.

*See also* [hasComments](kexiv2iface-kexiv2.md#hasComments)()

### void KExiv2::setData(const KExiv2Iface::KExiv2Data &*data*) {#setData}

*See also* [data](kexiv2iface-kexiv2.md#data)()

### bool KExiv2::setExif(const QByteArray &*data*) const {#setExif}

Sets the Exif `data` using a Qt byte array.

Returns `true` if Exif metadata has been changed in memory.

*See also* [hasExif](kexiv2iface-kexiv2.md#hasExif)()

### bool KExiv2::setExifComment(const QString &*comment*, bool *setProgramName* = true) const {#setExifComment}

Sets an Exif user `comment` from the image.

Look at the Exif specification for more details about this tag.

Returns `true` if the Exif user comment has been changed in the metadata.

### bool KExiv2::setExifTagData(const char \**exifTagName*, const QByteArray &*data*, bool *setProgramName* = true) const {#setExifTagData}

Sets an Exif tag content `exifTagName` using a byte array `data`.

Returns `true` if the tag is set successfully.

### bool KExiv2::setExifTagLong(const char \**exifTagName*, long *val*, bool *setProgramName* = true) const {#setExifTagLong}

Sets an Exif tag content `exifTagName` using a long value `val`.

Returns `true` if the Exif tag is set successfully.

### bool KExiv2::setExifTagRational(const char \**exifTagName*, long *num*, long *den*, bool *setProgramName* = true) const {#setExifTagRational}

Sets an Exif tag content `exifTagName` using a rational value with the numerator `num` and denominator `den`.

Returns `true` if tag is set successfully.

### bool KExiv2::setExifTagString(const char \**exifTagName*, const QString &*value*, bool *setProgramName* = true) const {#setExifTagString}

Sets an Exif tag content `exifTagName` using a string `value`.

Returns `true` if the tag is set successfully.

### bool KExiv2::setExifTagVariant(const char \**exifTagName*, const QVariant &*data*, bool *rationalWantSmallDenominator* = true, bool *setProgramName* = true) const {#setExifTagVariant}

Sets an Exif tag content `exifTagName` using a [QVariant](https://doc.qt.io/qt-6/qvariant.html) `data`.

Returns `true` if the Exif tag is set successfully.

All types described for [getExifTagVariant](kexiv2iface-kexiv2.md#getExifTagVariant)() are supported.

Calling with a [QVariant](https://doc.qt.io/qt-6/qvariant.html) of type [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) is equivalent to calling [setExifTagData](kexiv2iface-kexiv2.md#setExifTagData)().

For the meaning of `rationalWantSmallDenominator`, see the documentation for the [convertToRational](kexiv2iface-kexiv2.md#convertToRational) methods.

Setting a value with multiple components is currently not supported.

### bool KExiv2::setExifThumbnail(const QImage &*thumb*, bool *setProgramName* = true) const {#setExifThumbnail}

Sets the Exif Thumbnail image.

The thumbnail image must have the right dimensions prior to this operation.

Look at the Exif specification for details.

Returns `true` if the thumbnail has been changed in the metadata.

### void KExiv2::setFilePath(const QString &*path*) {#setFilePath}

Sets the file `path` of the current image.

### bool KExiv2::setGPSInfo(const double *altitude*, const QString &*latitude*, const QString &*longitude*, const bool *setProgramName* = true) {#setGPSInfo}

Sets all GPS location information to the image.

Returns `true` if all information has been changed in the metadata.

### bool KExiv2::setGPSInfo(const double *altitude*, const double *latitude*, const double *longitude*, const bool *setProgramName* = true) {#setGPSInfo-1}

Sets all GPS location information to the image.

Returns `true` if all information has been changed in the metadata.

### bool KExiv2::setGPSInfo(const double \*const *altitude*, const double *latitude*, const double *longitude*, const bool *setProgramName* = true) {#setGPSInfo-2}

Sets all GPS location information to the image.

Returns `true` if all information has been changed in the metadata.

If you do not want altitude to be set, pass a null pointer.

### bool KExiv2::setImageColorWorkSpace(KExiv2Iface::KExiv2::ImageColorWorkSpace *workspace*, bool *setProgramName* = true) const {#setImageColorWorkSpace}

Sets the Exif color-space tag of the image.

Returns `true` if the `workspace` has been changed in the metadata.

*See also* [ImageColorWorkSpace](kexiv2iface-kexiv2.md#ImageColorWorkSpace-enum)

### bool KExiv2::setImageDateTime(const QDateTime &*dateTime*, bool *setDateTimeDigitized* = false, bool *setProgramName* = true) const {#setImageDateTime}

Sets the Exif and IPTC timestamp.

If `setDateTimeDigitized` is `true`, then the `Digitalized` timestamp is set, else only the `Created` timestamp is set.

### bool KExiv2::setImageDimensions(const QSize &*size*, bool *setProgramName* = true) const {#setImageDimensions}

Sets the `size` of image in pixels using Exif tags.

Returns `true` if the size has been changed in the metadata.

### bool KExiv2::setImageOrientation(KExiv2Iface::KExiv2::ImageOrientation *orientation*, bool *setProgramName* = true) const {#setImageOrientation}

Sets the Exif `orientation` tag of image.

Returns `true` if the orientation has been changed in the metadata.

*See also* [ImageOrientation](kexiv2iface-kexiv2.md#ImageOrientation-enum)

### \[virtual\] bool KExiv2::setImagePreview(const QImage &*preview*, bool *setProgramName* = true) const {#setImagePreview}

Sets the IPTC `preview` image. \* \* The thumbnail image must have the right size prior to this operation \* (64Kb max with JPEG file, else 256Kb). \* \* Look at the IPTC specification for details. \* \* Returns `true` if the preview has been changed in the metadata. \* \* Re-implement this method if you want to use an image file format other than JPEG to \* save the preview.

### bool KExiv2::setImageProgramId(const QString &*program*, const QString &*version*) const {#setImageProgramId}

Sets `program` name and program `version` in Exif and IPTC Metadata.

Returns `true` if information has been changed in the metadata.

### bool KExiv2::setIptc(const QByteArray &*data*) const {#setIptc}

Sets the IPTC data using a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) `data`.

Returns `true` if the IPTC metadata has been changed in memory.

*See also* [hasIptc](kexiv2iface-kexiv2.md#hasIptc)()

### bool KExiv2::setIptcKeywords(const QStringList &*oldKeywords*, const QStringList &*newKeywords*, bool *setProgramName* = true) const {#setIptcKeywords}

Sets IPTC keywords using a list of strings defined by `newKeywords` to replace `oldKeywords`.

Use getImageKeywords() to set `oldKeywords` to existing keywords from the image.

This method will compare all new keywords with all old keywords to prevent duplicate entries in the image.

Returns `true` if the keywords have been changed in the metadata.

### bool KExiv2::setIptcSubCategories(const QStringList &*oldSubCategories*, const QStringList &*newSubCategories*, bool *setProgramName* = true) const {#setIptcSubCategories}

Sets IPTC subcategories using a list of strings defined by `newSubCategories` to replace `oldSubCategories`.

Use getImageSubCategories() to set `oldSubCategories` with existing subcategories from the image.

This method will compare all new subcategories with all old subcategories to prevent duplicate entries in image.

Returns `true` if the subcategories have been changed in the metadata.

### bool KExiv2::setIptcSubjects(const QStringList &*oldSubjects*, const QStringList &*newSubjects*, bool *setProgramName* = true) const {#setIptcSubjects}

Sets IPTC subjects using a list of strings defined by `newSubjects` to replace `oldSubjects`.

Use getImageSubjects() to set `oldSubjects` with existing subjects from the image.

This method will compare all new subjects with all old subjects to prevent duplicate entries in image.

Returns `true` if the subjects have been changed in the metadata.

### bool KExiv2::setIptcTagData(const char \**iptcTagName*, const QByteArray &*data*, bool *setProgramName* = true) const {#setIptcTagData}

Sets an IPTC tag content `iptcTagName` using a byte array `data`.

Returns `true` if tag is set successfully.

### bool KExiv2::setIptcTagString(const char \**iptcTagName*, const QString &*value*, bool *setProgramName* = true) const {#setIptcTagString}

Sets an IPTC tag content `iptcTagName` using a string `value`.

Returns `true` if tag is set successfully.

### bool KExiv2::setIptcTagsStringList(const char \**iptcTagName*, int *maxSize*, const QStringList &*oldValues*, const QStringList &*newValues*, bool *setProgramName* = true) const {#setIptcTagsStringList}

Sets multiple IPTC tags contents with the given tag name `iptcTagName` using a string list `newValues` to replace `oldValues`.

`maxSize` is the max characters size of one entry.

Returns `true` if all tags have been set successfully.

### void KExiv2::setMetadataWritingMode(const int *mode*) {#setMetadataWritingMode}

Sets the metadata writing `mode`.

*See also* [MetadataWritingMode](kexiv2iface-kexiv2.md#MetadataWritingMode-enum), [metadataWritingMode](kexiv2iface-kexiv2.md#metadataWritingMode)()

### \[virtual protected\] bool KExiv2::setProgramId(bool *on* = true) const {#setProgramId}

Re-implement this method to automatically set the Program Name and Program Version information in Exif and IPTC metadata if `on` is set to `true`.

This method is called by all methods which change tags in the metadata.

By default this method does nothing and returns `true`.

### bool KExiv2::setTiffThumbnail(const QImage &*thumb*, bool *setProgramName* = true) const {#setTiffThumbnail}

Adds a JPEG thumbnail `thumb` to TIFF images.

Use this instead of [setExifThumbnail](kexiv2iface-kexiv2.md#setExifThumbnail)() for TIFF images.

### void KExiv2::setUpdateFileTimeStamp(bool *on*) {#setUpdateFileTimeStamp}

Enables or disables file timestamp updating when metadata are saved.

By default files timestamp are untouched.

*See also* [updateFileTimeStamp](kexiv2iface-kexiv2.md#updateFileTimeStamp)()

### void KExiv2::setUseXMPSidecar4Reading(const bool *on*) {#setUseXMPSidecar4Reading}

Enables or disables using an XMP sidecar for reading metadata.

*See also* [useXMPSidecar4Reading](kexiv2iface-kexiv2.md#useXMPSidecar4Reading)()

### void KExiv2::setWriteRawFiles(const bool *on*) {#setWriteRawFiles}

Enables or disables writing metadata operations to RAW tiff based files.

Requires Exiv2 0.18.

By default RAW files are untouched.

*See also* [writeRawFiles](kexiv2iface-kexiv2.md#writeRawFiles)()

### bool KExiv2::setXmp(const QByteArray &*data*) const {#setXmp}

Sets the XMP `data` using a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html).

Returns `true` if the XMP metadata has been changed in memory.

*See also* [hasXmp](kexiv2iface-kexiv2.md#hasXmp)()

### bool KExiv2::setXmpKeywords(const QStringList &*newKeywords*, bool *setProgramName* = true) const {#setXmpKeywords}

Sets XMP keywords using a list of strings defined by `newKeywords`.

The existing keywords from the image are preserved.

This method will compare all new keywords with all already existing keywords to prevent duplicate entries in the image.

Returns `true` if the keywords have been changed in the metadata.

### bool KExiv2::setXmpSubCategories(const QStringList &*newSubCategories*, bool *setProgramName* = true) const {#setXmpSubCategories}

Sets XMP subcategories using the string list `newSubCategories`.

The existing subcategories from the image are preserved.

This method will compare all new subcategories with all already existing subcategories to prevent duplicate entries in the image.

Returns `true` if the subcategories have been changed in the metadata.

### bool KExiv2::setXmpSubjects(const QStringList &*newSubjects*, bool *setProgramName* = true) const {#setXmpSubjects}

Sets XMP subjects using a string list of `newSubjects`.

The existing subjects from the image are preserved.

This method will compare all new subjects with all already existing subjects to prevent duplicate entries in the image.

Returns `true` if the subjects have been changed in the metadata.

### bool KExiv2::setXmpTagString(const char \**xmpTagName*, const QString &*value*, bool *setProgramName* = true) const {#setXmpTagString}

Sets an XMP tag content `xmpTagName` using a string `value`.

Returns `true` if tag is set successfully.

### bool KExiv2::setXmpTagString(const char \**xmpTagName*, const QString &*value*, KExiv2Iface::KExiv2::XmpTagType *type*, bool *setProgramName* = true) const {#setXmpTagString-1}

Sets an XMP tag `xmpTagName` with a specific `type` to the given `value`.

Returns `true` if tag is set successfully.

This method only accept [NormalTag](kexiv2iface-kexiv2.md#XmpTagType-enum), [ArrayBagTag](kexiv2iface-kexiv2.md#XmpTagType-enum) and [StructureTag](kexiv2iface-kexiv2.md#XmpTagType-enum). Other XmpTagTypes do nothing.

### bool KExiv2::setXmpTagStringBag(const char \**xmpTagName*, const QStringList &*bag*, bool *setProgramName* = true) const {#setXmpTagStringBag}

Sets an XMP tag content `xmpTagName` using the bag of strings `bag`.

Returns `true` if tag is set successfully.

### bool KExiv2::setXmpTagStringLangAlt(const char \**xmpTagName*, const QString &*value*, const QString &*langAlt*, bool *setProgramName* = true) const {#setXmpTagStringLangAlt}

Sets an XMP tag content `xmpTagName` using a string `value` with an alternative language header `langAlt`.

`langAlt` contains the language alternative information (like "fr-FR" for French - RFC3066 notation) or is null to set alternative language to default settings ("x-default").

Returns `true` if the tag is set successfully.

### bool KExiv2::setXmpTagStringListLangAlt(const char \**xmpTagName*, const KExiv2::AltLangMap &*values*, bool *setProgramName*) const {#setXmpTagStringListLangAlt}

Sets an Alternative Language XMP tag content `xmpTagName` using a map with the given `values`.

See [AltLangMap](kexiv2iface-kexiv2.md#AltLangMap-typedef) class description for details.

If `xmpTagName` already exists, it wil be removed prior to this operation.

Returns `true` if the tag is set successfully.

### bool KExiv2::setXmpTagStringSeq(const char \**xmpTagName*, const QStringList &*seq*, bool *setProgramName* = true) const {#setXmpTagStringSeq}

Sets an XMP tag content `xmpTagName` using the sequence of strings `seq`.

Returns `true` if the tag is set successfully.

### \[static\] QString KExiv2::sidecarFilePathForFile(const QString &*path*) {#sidecarFilePathForFile}

Returns the XMP Sidecar file `path` for an image in the given file `path`.

If the image file path does not include a file name or is empty, this function returns a null string.

### \[static\] QString KExiv2::sidecarPath(const QString &*path*) {#sidecarPath}

Like [sidecarFilePathForFile](kexiv2iface-kexiv2.md#sidecarFilePathForFile)(), but it works for local file `path`.

### \[static\] QUrl KExiv2::sidecarUrl(const QString &*path*) {#sidecarUrl}

Gives a file url for a local `path`.

### \[static\] QUrl KExiv2::sidecarUrl(const QUrl &*url*) {#sidecarUrl-1}

Like [sidecarFilePathForFile](kexiv2iface-kexiv2.md#sidecarFilePathForFile)(), but it works for a remote `url`.

### \[static\] bool KExiv2::supportMetadataWritting(const QString &*typeMime*) {#supportMetadataWritting}

Returns `true` if the library can write metadata to `typeMime` file format.

### \[static\] bool KExiv2::supportXmp() {#supportXmp}

Returns `true` if the library can handle XMP metadata.

### \[static\] bool KExiv2::unregisterXmpNameSpace(const QString &*uri*) {#unregisterXmpNameSpace}

Unregisters a previously registered custom namespace.

### bool KExiv2::updateFileTimeStamp() const {#updateFileTimeStamp}

Returns `true` if file timestamp is updated when metadata are saved.

*See also* [setUpdateFileTimeStamp](kexiv2iface-kexiv2.md#setUpdateFileTimeStamp)()

### bool KExiv2::useXMPSidecar4Reading() const {#useXMPSidecar4Reading}

Returns `true` if using an XMP sidecar for reading metadata is enabled.

*See also* [setUseXMPSidecar4Reading](kexiv2iface-kexiv2.md#setUseXMPSidecar4Reading)()

### \[static\] QString KExiv2::version() {#version}

Returns a string version of libkexiv2 release.

### bool KExiv2::writeRawFiles() const {#writeRawFiles}

Returns `true` if writing metadata operations on RAW tiff based files is enabled.

Requires Exiv2 0.18.

*See also* [setWriteRawFiles](kexiv2iface-kexiv2.md#setWriteRawFiles)()

### KExiv2Iface::KExiv2 &KExiv2::operator=(const KExiv2Iface::KExiv2 &*metadata*) {#operator-eq}

Create a copy of container.
