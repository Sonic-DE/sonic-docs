---
title: "KCodecs Namespace"
description: "A collection of commonly used encoding and decoding algorithms."
---

# KCodecs Namespace

A collection of commonly used encoding and decoding algorithms. [More...](#details)

- Header: KCodecs
- CMake: find\_package(KF6 REQUIRED COMPONENTS Codecs) target\_link\_libraries(mytarget PRIVATE KF6::Codecs)

## Detailed Description {#details}

A wrapper class for the most commonly used encoding and decoding algorithms.

Currently there is support for encoding and decoding input using base64, uu and the quoted-printable specifications.

```cpp
QByteArray input = "Aladdin:open sesame";
QByteArray result = KCodecs::base64Encode(input);
cout << "Result: " << result.data() << endl;
```

Output should be

```cpp
Result: QWxhZGRpbjpvcGVuIHNlc2FtZQ==
```

The above example makes use of the convenience functions (ones that accept/return null-terminated strings) to encode/decode a string. If what you need is to encode or decode binary data, then it is highly recommended that you use the functions that take an input and output [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) as arguments. These functions are specifically tailored for encoding and decoding binary data.

## Classes {#classes}

### class [Codec](kcodecs-codec.md)

An abstract base class of codecs for common mail transfer encodings.

### class [Decoder](kcodecs-decoder.md)

Stateful CTE decoder class.

### class [Encoder](kcodecs-encoder.md)

Stateful encoder class.

## Type Documentation {#type-documentation}

### enum KCodecs::CharsetOption {#CharsetOption-enum}

Charset options for RFC2047 decoder

| Constant | Value | Description |
| --- | --- | --- |
| `KCodecs::NoOption` | `0` | No special option |
| `KCodecs::ForceDefaultCharset` | `1` | Force use of the default charset |

### \[since 6.20\] enum KCodecs::RFC2047EncodingOption {#RFC2047EncodingOption-enum}

Options for RFC2047 encoder

| Constant | Value | Description |
| --- | --- | --- |
| `KCodecs::RFC2047EncodingOption::NoOption` | `0` | No special option |
| `KCodecs::RFC2047EncodingOption::EncodeReservedCharcters` | `1` | Also encode all characeters that are reserved in the context of certain MIME headers, as specified in RFC 2047 §5. |

This enum was introduced in Qt 6.20.

## Function Documentation {#function-documentation}

### QByteArray KCodecs::base45Decode(QByteArrayView *in*) {#base45Decode}

Decodes the given data that was encoded using the base45 codec.

`in` data to be decoded.

Returns decoded string.

*See also* [https://datatracker.ietf.org/doc/draft-faltstrom-base45/](https://datatracker.ietf.org/doc/draft-faltstrom-base45/)

### QByteArray KCodecs::base64Decode(QByteArrayView *in*) {#base64Decode}

Decodes the given data that was encoded using the base64 algorithm.

`in` data to be decoded.

Returns decoded string.

### void KCodecs::base64Decode(QByteArrayView *in*, QByteArray &*out*) {#base64Decode-1}

Decodes the given data that was encoded with the base64 algorithm.

Use this function if you want the result of the decoding to be placed in another array which cuts down the number of copy operation that have to be performed in the process. This is also the preferred method for decoding an encoded binary data.

> **Note:** the output array is first reset and then resized appropriately before use, hence, all data stored in the output array will be lost.

`in` data to be decoded.

`out` decoded data.

### QByteArray KCodecs::base64Encode(QByteArrayView *in*) {#base64Encode}

Encodes the given data using the base64 algorithm.

The boolean argument determines if the encoded data is going to be restricted to 76 characters or less per line as specified by RFC 2045.

`in` data to be encoded.

Returns base64 encoded string.

### void KCodecs::base64Encode(QByteArrayView *in*, QByteArray &*out*, bool *insertLFs* = false) {#base64Encode-1}

Encodes the given data using the base64 algorithm.

Use this function if you want the result of the encoding to be placed in another array which cuts down the number of copy operation that have to be performed in the process. This is also the preferred method for encoding binary data.

The boolean argument determines if the encoded data is going to be restricted to 76 characters or less per line as specified by RFC 2045. If `insertLFs` is true, then there will be 76 characters or less per line.

> **Note:** the output array is first reset and then resized appropriately before use, hence, all data stored in the output array will be lost.

`in` data to be encoded.

`out` encoded data.

`insertLFs` limit the number of characters per line.

### QString KCodecs::decodeRFC2047String(QStringView *text*) {#decodeRFC2047String}

Decodes string `text` according to RFC2047, i.e., the construct =?charset?\[qb\]?encoded?=

`text` source string

Returns the decoded string

### QString KCodecs::decodeRFC2047String(QByteArrayView *src*, QByteArray \**usedCS*, const QByteArray &*defaultCS* = QByteArray(), KCodecs::CharsetOption *option* = NoOption) {#decodeRFC2047String-1}

Decodes string `src` according to RFC2047, i.e. the construct =?charset?\[qb\]?encoded?=

`src` source string.

`usedCS` the name of any detected charset or, in case of multiple different ones, "UTF-8" as that of a super charset is returned here

`defaultCS` the charset to use in case the detected one isn't known to us.

`option` options for the decoder

Returns the decoded string.

### \[since 6.20\] QByteArray KCodecs::encodeRFC2047String(QStringView *src*, QByteArrayView *charset*, KCodecs::RFC2047EncodingOption *option*) {#encodeRFC2047String}

Encodes string `src` according to RFC2047 using charset `charset`.

This function also makes commas, quotes and other characters part of the encoded name, for example the string "Jöhn Döe" \<john@example.com"\> would be encoded as \<encoded word for "Jöhn Döe"\> \<john@example.com\>, i.e. the opening and closing quote mark would be part of the encoded word. Therefore don't use this function for input strings that contain semantically meaningful characters, like the quoting marks in this example. `src` source string.

`charset` charset to use. If it can't encode the string, UTF-8 will be used instead.

`option` encoding options.

Returns the encoded string.

This function was introduced in Qt 6.20.

### QByteArray KCodecs::quotedPrintableDecode(QByteArrayView *in*) {#quotedPrintableDecode}

Decodes a quoted-printable encoded data.

Accepts data with CRLF or standard unix line breaks.

`in` data to be decoded.

Returns decoded string.

### void KCodecs::quotedPrintableDecode(QByteArrayView *in*, QByteArray &*out*) {#quotedPrintableDecode-1}

Decodes a quoted-printable encoded data.

Accepts data with CRLF or standard unix line breaks. Use this function if you want the result of the decoding to be placed in another array which cuts down the number of copy operation that have to be performed in the process. This is also the preferred method for decoding an encoded binary data.

> **Note:** the output array is first reset and then resized appropriately before use, hence, all data stored in the output array will be lost.

`in` data to be decoded.

`out` decoded data.

### QByteArray KCodecs::quotedPrintableEncode(QByteArrayView *in*, bool *useCRLF* = true) {#quotedPrintableEncode}

Encodes the given data using the quoted-printable algorithm.

`in` the data to be encoded.

`useCRLF` if true the input data is expected to have CRLF line breaks and the output will have CRLF line breaks, too.

Returns quoted-printable encoded string.

### void KCodecs::quotedPrintableEncode(QByteArrayView *in*, QByteArray &*out*, bool *useCRLF*) {#quotedPrintableEncode-1}

Encodes the given data using the quoted-printable algorithm.

Use this function if you want the result of the encoding to be placed in another array which cuts down the number of copy operation that have to be performed in the process. This is also the preferred method for encoding binary data.

> **Note:** the output array is first reset and then resized appropriately before use, hence, all data stored in the output array will be lost.

`in` data to be encoded.

`out` encoded data.

`useCRLF` if true the input data is expected to have CRLF line breaks and the output will have CRLF line breaks, too.

### QByteArray KCodecs::uudecode(QByteArrayView *in*) {#uudecode}

Decodes the given data using the uudecode algorithm.

Any 'begin' and 'end' lines like those generated by the utilities in unix and unix-like OS will be automatically ignored.

`in` the data to be decoded.

Returns the decoded string.

### void KCodecs::uudecode(QByteArrayView *in*, QByteArray &*out*) {#uudecode-1}

Decodes the given data using the uudecode algorithm.

Use this function if you want the result of the decoding to be placed in another array which cuts down the number of copy operation that have to be performed in the process. This is the preferred method for decoding binary data.

Any 'begin' and 'end' lines like those generated by the utilities in unix and unix-like OS will be automatically ignored.

> **Note:** the output array is first reset and then resized appropriately before use, hence, all data stored in the output array will be lost.

`in` data to be decoded.

`out` uudecoded data.
