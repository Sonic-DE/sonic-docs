---
title: "KCodecs::Codec Class"
description: "An abstract base class of codecs for common mail transfer encodings."
---

# KCodecs::Codec Class

An abstract base class of codecs for common mail transfer encodings. [More...](#details)

- **Header:** `#include <KCodecs>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Codecs)`  
  `target_link_libraries(mytarget PRIVATE KF6::Codecs)`

[List of all members, including inherited members](kcodecs-codec-members.md)

## Public Types

- [enum Codec::NewlineType](#NewlineType-enum)

## Public Functions

- [QByteArray decode(QByteArrayView src, KCodecs::Codec::NewlineType newline = NewlineLF) const](#decode)
- [bool decode(const char \*&scursor, const char \*const send, char \*&dcursor, const char \*const dend, KCodecs::Codec::NewlineType newline = NewlineLF) const](#decode-1)
- [QByteArray encode(QByteArrayView src, KCodecs::Codec::NewlineType newline = NewlineLF) const](#encode)
- [bool encode(const char \*&scursor, const char \*const send, char \*&dcursor, const char \*const dend, KCodecs::Codec::NewlineType newline = NewlineLF) const](#encode-1)
- [KCodecs::Decoder \*makeDecoder(KCodecs::Codec::NewlineType newline = NewlineLF) const](#makeDecoder)
- [KCodecs::Encoder \*makeEncoder(KCodecs::Codec::NewlineType newline = NewlineLF) const](#makeEncoder)
- [qsizetype maxDecodedSizeFor(qsizetype insize, KCodecs::Codec::NewlineType newline = NewlineLF) const](#maxDecodedSizeFor)
- [qsizetype maxEncodedSizeFor(qsizetype insize, KCodecs::Codec::NewlineType newline = NewlineLF) const](#maxEncodedSizeFor)
- [const char \*name() const](#name)

## Static Public Members

- [KCodecs::Codec \*codecForName(QByteArrayView name)](#codecForName)

## Detailed Description {#details}

### Glossary: {#glossary}

#### MIME: {#mime}

Multipurpose Internet Mail Extensions or MIME is an Internet Standard that extends the format of e-mail to support text in character sets other than US-ASCII, non-text attachments, multi-part message bodies, and header information in non-ASCII character sets. Virtually all human-written Internet e-mail and a fairly large proportion of automated e-mail is transmitted via SMTP in MIME format. Internet e-mail is so closely associated with the SMTP and MIME standards that it is sometimes called SMTP/MIME e-mail. The content types defined by MIME standards are also of growing importance outside of e-mail, such as in communication protocols like HTTP for the World Wide Web. MIME is also a fundamental component of communication protocols such as HTTP, which requires that data be transmitted in the context of e-mail-like messages, even though the data may not actually be e-mail.

#### Codec: {#codec}

a program capable of performing encoding and decoding on a digital data stream. Codecs encode data for storage or encryption and decode it for viewing or editing.

#### CRLF: {#crlf}

A "Carriage Return (0x0D)" followed by a "Line Feed (0x0A)", two ASCII control characters used to represent a newline on some operating systems, notably DOS and Microsoft Windows.

#### LF: {#lf}

a "Line Feed (0x0A)" ASCII control character used to represent a newline on some operating systems, notably Unix, Unix-like, and Linux.

Provides an abstract base class of codecs like base64 and quoted-printable. Implemented as a singleton.

## Member Type Documentation {#member-type-documentation}

### enum Codec::NewlineType {#NewlineType-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KCodecs::Codec::NewlineLF` | `0` | Line Feed |
| `KCodecs::Codec::NewlineCRLF` | `1` | Carriage Return Line Feed |

## Member Function Documentation {#member-function-documentation}

### \[static\] KCodecs::Codec \*Codec::codecForName(QByteArrayView *name*) {#codecForName}

Returns a codec associated with the specified `name`.

`name` is a valid codec name.

### QByteArray Codec::decode(QByteArrayView *src*, KCodecs::Codec::NewlineType *newline* = NewlineLF) const {#decode}

Even more convenient, but also a bit slower and more memory intensive, since it allocates storage for the worst case and then shrinks the result [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) to the actual size again.

For use with small `src`.

`src` is the data to decode.

`newline` whether make new lines using CRLF, or LF (default is LF).

### \[virtual\] bool Codec::decode(const char \*&*scursor*, const char \*const *send*, char \*&*dcursor*, const char \*const *dend*, KCodecs::Codec::NewlineType *newline* = NewlineLF) const {#decode-1}

Convenience wrapper that can be used for small chunks of data when you can provide a large enough buffer. The default implementation creates a Decoder and uses it.

Decodes a chunk of bytes starting at `scursor` and extending to `send` into the buffer described by `dcursor` and `dend`.

This function doesn't support chaining of blocks. The returned block cannot be added to, but you don't need to finalize it, too.

Example usage (`in` contains the input data):

```cpp
KCodecs::Codec *codec = KCodecs::Codec::codecForName("base64");
if (!codec) {
    qFatal() << "no base64 codec found!?";
}
QByteArray out(in.size()); // good guess for any encoding...
QByteArray::Iterator iit = in.begin();
QByteArray::Iterator oit = out.begin();
if (!codec->decode(iit, in.end(), oit, out.end())) {
    qDebug() << "output buffer too small";
    return;
}
qDebug() << "Size of decoded data:" << oit - out.begin();
```

`scursor` is a pointer to the start of the input buffer.

`send` is a pointer to the end of the input buffer.

`dcursor` is a pointer to the start of the output buffer.

`dend` is a pointer to the end of the output buffer.

`newline` whether make new lines using CRLF, or LF (default is LF).

Returns false if the decoded data didn't fit into the output buffer; true otherwise.

### QByteArray Codec::encode(QByteArrayView *src*, KCodecs::Codec::NewlineType *newline* = NewlineLF) const {#encode}

Even more convenient, but also a bit slower and more memory intensive, since it allocates storage for the worst case and then shrinks the result [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) to the actual size again.

For use with small `src`.

`src` is the data to encode.

`newline` whether make new lines using CRLF, or LF (default is LF).

### \[virtual\] bool Codec::encode(const char \*&*scursor*, const char \*const *send*, char \*&*dcursor*, const char \*const *dend*, KCodecs::Codec::NewlineType *newline* = NewlineLF) const {#encode-1}

Convenience wrapper that can be used for small chunks of data when you can provide a large enough buffer. The default implementation creates an Encoder and uses it.

Encodes a chunk of bytes starting at `scursor` and extending to `send` into the buffer described by `dcursor` and `dend`.

This function doesn't support chaining of blocks. The returned block cannot be added to, but you don't need to finalize it, too.

Example usage (`in` contains the input data):

```cpp
KCodecs::Codec *codec = KCodecs::Codec::codecForName("base64");
if (!codec) {
    qFatal() << "no base64 codec found!?";
}
QByteArray out(in.size() * 1.4); // crude maximal size of b64 encoding
QByteArray::Iterator iit = in.begin();
QByteArray::Iterator oit = out.begin();
if (!codec->encode(iit, in.end(), oit, out.end())) {
    qDebug() << "output buffer too small";
    return;
}
qDebug() << "Size of encoded data:" << oit - out.begin();
```

`scursor` is a pointer to the start of the input buffer.

`send` is a pointer to the end of the input buffer.

`dcursor` is a pointer to the start of the output buffer.

`dend` is a pointer to the end of the output buffer.

`newline` whether make new lines using CRLF, or LF (default is LF).

Returns false if the encoded data didn't fit into the output buffer; true otherwise.

### \[pure virtual\] KCodecs::Decoder \*Codec::makeDecoder(KCodecs::Codec::NewlineType *newline* = NewlineLF) const {#makeDecoder}

Creates the decoder for the codec.

`newline` whether make new lines using CRLF, or LF (default is LF).

Returns a pointer to an instance of the codec's decoder.

### \[pure virtual\] KCodecs::Encoder \*Codec::makeEncoder(KCodecs::Codec::NewlineType *newline* = NewlineLF) const {#makeEncoder}

Creates the encoder for the codec.

`newline` whether make new lines using CRLF, or LF (default is LF).

Returns a pointer to an instance of the codec's encoder.

### \[pure virtual\] qsizetype Codec::maxDecodedSizeFor(qsizetype *insize*, KCodecs::Codec::NewlineType *newline* = NewlineLF) const {#maxDecodedSizeFor}

Computes the maximum size, in characters, needed for the deccoding.

`insize` is the number of input characters to be decoded.

`newline` whether make new lines using CRLF, or LF (default is LF).

Returns the maximum number of characters in the decoding.

### \[pure virtual\] qsizetype Codec::maxEncodedSizeFor(qsizetype *insize*, KCodecs::Codec::NewlineType *newline* = NewlineLF) const {#maxEncodedSizeFor}

Computes the maximum size, in characters, needed for the encoding.

`insize` is the number of input characters to be encoded.

`newline` whether make new lines using CRLF, or LF (default is LF).

Returns the maximum number of characters in the encoding.

### \[pure virtual constexpr\] const char \*Codec::name() const {#name}

Returns the name of the encoding. Guaranteed to be lowercase.
