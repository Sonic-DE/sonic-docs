---
title: "KFileMetaData::Property Namespace"
description: "The Property namespace."
---

# KFileMetaData::Property Namespace

The Property namespace. [More...](#details)

- Header: Property
- CMake: find\_package(KF6 REQUIRED COMPONENTS FileMetaData) target\_link\_libraries(mytarget PRIVATE KF6::FileMetaData)

## Detailed Description {#details}

## Type Documentation {#type-documentation}

### enum Property::Property {#Property-enum}

The Property enum contains all files property types that [KFileMetaData](kfilemetadata-module.md) manipulates

| Constant | Value |   |
| --- | --- | --- |
| `KFileMetaData::Property::Empty` | `0` |   |
| `KFileMetaData::Property::BitRate` | `1` | The Bit Rate of the Audio in the file. Represented as an integer in kbit/sec |
| `KFileMetaData::Property::Channels` | `2` | The number of channels of the Audio in the file. Represented as an integer |
| `KFileMetaData::Property::Duration` | `3` | The duration of the media in the file. Represented as an integer in seconds |
| `KFileMetaData::Property::Genre` | `4` | The Genre of an Audio file. This is represented as a string of genres and not integers. The IDv1 standard provides a list of commonly excepted genres. |
| `KFileMetaData::Property::SampleRate` | `5` | The sample rate or frequency of the Audio in the file. This is represented as an integer in Hz. So a file with "44.1KHz" will have a frequency of 44100 |
| `KFileMetaData::Property::TrackNumber` | `6` | Represents the track number in a set. Typically maps to the "TRCK" tag in IDv3 |
| `KFileMetaData::Property::ReleaseYear` | `7` | Indicates the year a track was released. Represented as an integer. Typically mapped to the "TYE (Year)" tag in IDv1 |
| `KFileMetaData::Property::Comment` | `8` | Represents a comment stored in the file. This can map to e.g. the "COMM" field from IDv3 |
| `KFileMetaData::Property::Artist` | `9` | Represents the artist of a media file. This generally corresponds to the IDv1 ARTIST tag. Many extractors often split this string into a number of artists. |
| `KFileMetaData::Property::Album` | `10` | Represents the album of a media file. This generally corresponds to the IDv1 ALBUM tag. |
| `KFileMetaData::Property::AlbumArtist` | `11` | Represents the album artist of a media file. This generally corresponds to the IDv3 TPE2 ("Band/Orchestra/Accompaniment") tag. |
| `KFileMetaData::Property::Composer` | `12` | Represents the Composer of a media file. This generally corresponds to the IDv2 COMPOSER tag |
| `KFileMetaData::Property::Lyricist` | `13` | Represents the Lyricist of a media file. This generally corresponds to the IDv2 "Lyricist/text writer" tag |
| `KFileMetaData::Property::Author` | `14` | The Author field indicated the primary creator of a document. This often corresponds directly to dc:creator |
| `KFileMetaData::Property::Title` | `15` | Refers to the Title of the content of the file. This can represented by the IDv1 tag TT2 (Title/songname/content description) or the TITLE in a PDF file or the 'dc:title' tag in DublinCore |
| `KFileMetaData::Property::Subject` | `16` | Refers to the subject of the file. This directly corresponds to the 'dc:subject' tag from DublinCore. |
| `KFileMetaData::Property::Generator` | `17` | Refers to the Application used to create this file. In the ODF standard this maps to the 'meta:generator' tag. In PDFs its mapped to the "Producer" tag. |
| `KFileMetaData::Property::PageCount` | `18` | The number of pages in a document |
| `KFileMetaData::Property::WordCount` | `19` | The number of words in a document. This is often only provided for documents where the word count is available in the metadata |
| `KFileMetaData::Property::LineCount` | `20` | The number of lines in a document. This is often only provided for documents where the line count is available in the metadata |
| `KFileMetaData::Property::Language (since Qt 5.50)` | `21` | The language the document is written in. This directly maps to the 'dc:language' tag from DublinCore. We do NOT employ any language detection schemes on the text |
| `KFileMetaData::Property::Copyright` | `22` | The copyright of the file. Represented as a string |
| `KFileMetaData::Property::Publisher` | `23` | The publisher of the content. Represented as a string |
| `KFileMetaData::Property::CreationDate` | `24` | The date the content of the file was created. This is extracted from the file metadata and not from the file system. In ODF, it corresponds to "meta:creation-date", in PDF to the "CreationDate" tag, and otherwise the "dcterms:created" tag |
| `KFileMetaData::Property::Keywords` | `25` | The keywords used to represent the document. This is mostly a string list of all the keywords |
| `KFileMetaData::Property::Width` | `26` | Represents the width of the Media in pixels. This is generally only applicable for Images and Videos |
| `KFileMetaData::Property::Height` | `27` | Represents the height of the Media in pixels. This is generally only applicable for Images and Videos |
| `KFileMetaData::Property::AspectRatio` | `28` | The Aspect Ratio of the visual image or video. It is the width of a pixel divided by the height of the pixel |
| `KFileMetaData::Property::FrameRate` | `29` | Number of frames per second |
| `KFileMetaData::Property::Manufacturer (since Qt 5.60)` | `30` | The manufacturer of the equipment used for generating the file and metadata. Typically maps to the 'Exif.Image.Make' tag |
| `KFileMetaData::Property::Model (since Qt 5.60)` | `31` | The model name of the equipment used for generating the file and metadata. Typically maps to the 'Exif.Image.Model' tag |
| `KFileMetaData::Property::ImageDateTime` | `32` |   |
| `KFileMetaData::Property::ImageOrientation` | `33` |   |
| `KFileMetaData::Property::PhotoFlash` | `34` |   |
| `KFileMetaData::Property::PhotoPixelXDimension` | `35` |   |
| `KFileMetaData::Property::PhotoPixelYDimension` | `36` |   |
| `KFileMetaData::Property::PhotoDateTimeOriginal` | `37` |   |
| `KFileMetaData::Property::PhotoFocalLength` | `38` |   |
| `KFileMetaData::Property::PhotoFocalLengthIn35mmFilm` | `39` |   |
| `KFileMetaData::Property::PhotoExposureTime` | `40` |   |
| `KFileMetaData::Property::PhotoFNumber` | `41` |   |
| `KFileMetaData::Property::PhotoApertureValue` | `42` |   |
| `KFileMetaData::Property::PhotoExposureBiasValue` | `43` |   |
| `KFileMetaData::Property::PhotoWhiteBalance` | `44` |   |
| `KFileMetaData::Property::PhotoMeteringMode` | `45` |   |
| `KFileMetaData::Property::PhotoISOSpeedRatings` | `46` |   |
| `KFileMetaData::Property::PhotoSaturation` | `47` |   |
| `KFileMetaData::Property::PhotoSharpness` | `48` |   |
| `KFileMetaData::Property::PhotoGpsLatitude` | `49` |   |
| `KFileMetaData::Property::PhotoGpsLongitude` | `50` |   |
| `KFileMetaData::Property::PhotoGpsAltitude` | `51` |   |
| `KFileMetaData::Property::TranslationUnitsTotal` | `52` |   |
| `KFileMetaData::Property::TranslationUnitsWithTranslation` | `53` |   |
| `KFileMetaData::Property::TranslationUnitsWithDraftTranslation` | `54` |   |
| `KFileMetaData::Property::TranslationLastAuthor` | `55` |   |
| `KFileMetaData::Property::TranslationLastUpDate` | `56` |   |
| `KFileMetaData::Property::TranslationTemplateDate` | `57` |   |
| `KFileMetaData::Property::OriginUrl` | `58` | The URL this file has originally been downloaded from |
| `KFileMetaData::Property::OriginEmailSubject` | `59` | The subject of the email this file was originally attached to |
| `KFileMetaData::Property::OriginEmailSender` | `60` | The sender of the email this file was originally attached to |
| `KFileMetaData::Property::OriginEmailMessageId` | `61` | The message ID of the email this file was originally attached to |
| `KFileMetaData::Property::DiscNumber` | `62` | Represents the disc number in a multi-disc set. Typically maps to the "TPOS" tag for mp3 |
| `KFileMetaData::Property::Location` | `63` | Represents the location where an audio file was recorded |
| `KFileMetaData::Property::Performer` | `64` | Represents the (lead) performer of an audio file |
| `KFileMetaData::Property::Ensemble` | `65` | Represents the ensemble of an audio file |
| `KFileMetaData::Property::Arranger` | `66` | Represents the arranger of an audio file |
| `KFileMetaData::Property::Conductor` | `67` | Represents the conductor of an audio file |
| `KFileMetaData::Property::Opus` | `68` | Represents the opus of an audio file mostly used for classical music |
| `KFileMetaData::Property::Label` | `69` | Represents the label of the content |
| `KFileMetaData::Property::Compilation` | `70` | Contains the name of the compilation of an audio file |
| `KFileMetaData::Property::License` | `71` | Contains the license information of the file |
| `KFileMetaData::Property::Rating` | `72` | For ratings stored in Metadata tags |
| `KFileMetaData::Property::Lyrics` | `73` | Contains the lyrics of a song embedded in the file |
| `KFileMetaData::Property::ReplayGainAlbumPeak` | `74` | Contains ReplayGain information for audio files |
| `KFileMetaData::Property::ReplayGainAlbumGain` | `75` | Contains ReplayGain information for audio files. The album gain is given in "dB" |
| `KFileMetaData::Property::ReplayGainTrackPeak` | `76` | Contains ReplayGain information for audio files |
| `KFileMetaData::Property::ReplayGainTrackGain` | `77` | Contains ReplayGain information for audio files. The track gain is given in "dB" |
| `KFileMetaData::Property::Description` | `78` | Represents the description stored in the file. This maps to the 'dc:description' tag from DublinCore |
| `KFileMetaData::Property::VideoCodec (since Qt 6.13)` | `79` | A string description of the codec used |
| `KFileMetaData::Property::AudioCodec (since Qt 6.13)` | `80` | A string description of the codec used |
| `KFileMetaData::Property::PixelFormat (since Qt 6.13)` | `81` | The Pixel format used by the media (image or video) |
| `KFileMetaData::Property::ColorSpace (since Qt 6.13)` | `82` | The Color space used by the media (image or video) |
| `KFileMetaData::Property::AssistiveAlternateDescription (since Qt 6.16)` | `83` | A brief textual description of the purpose and meaning of an image. The text can be used by assistive technology. |
