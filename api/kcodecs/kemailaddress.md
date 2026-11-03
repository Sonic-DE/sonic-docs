---
title: "KEmailAddress Namespace"
description: "Text encoding."
---

# KEmailAddress Namespace

Text encoding. [More...](#details)

- Header: KEmailAddress
- CMake: find\_package(KF6 REQUIRED COMPONENTS Codecs) target\_link\_libraries(mytarget PRIVATE KF6::Codecs)

## Detailed Description {#details}

## Type Documentation {#type-documentation}

### enum KEmailAddress::EmailParseResult {#EmailParseResult-enum}

Email validation result. The only 'success' code in this enumeration is AddressOK; all the other values indicate some specific problem with the address which is being validated.

Result type for [splitAddress](kemailaddress.md#splitAddress)(), [isValidAddress](kemailaddress.md#isValidAddress)() and [isValidSimpleAddress](kemailaddress.md#isValidSimpleAddress)().

| Constant | Value | Description |
| --- | --- | --- |
| `KEmailAddress::AddressOk` | `0` | Email is valid |
| `KEmailAddress::AddressEmpty` | `1` | The address is empty |
| `KEmailAddress::UnexpectedEnd` | `2` | Something is unbalanced |
| `KEmailAddress::UnbalancedParens` | `3` | Unbalanced ( ) |
| `KEmailAddress::MissingDomainPart` | `4` | No domain in address |
| `KEmailAddress::UnclosedAngleAddr` | `5` | \< with no matching \> |
| `KEmailAddress::UnopenedAngleAddr` | `6` | \> with no preceding \< |
| `KEmailAddress::TooManyAts` | `7` | More than one @ in address |
| `KEmailAddress::UnexpectedComma` | `8` | Comma not allowed here |
| `KEmailAddress::TooFewAts` | `9` | Missing @ in address |
| `KEmailAddress::MissingLocalPart` | `10` | No address specified, only domain |
| `KEmailAddress::UnbalancedQuote` | `11` | Quotes (single or double) not matched |
| `KEmailAddress::NoAddressSpec` | `12` |   |
| `KEmailAddress::DisallowedChar` | `13` | An invalid character detected in address |
| `KEmailAddress::InvalidDisplayName` | `14` | An invalid displayname detected in address |
| `KEmailAddress::TooFewDots` | `15` | Missing . in address |

## Function Documentation {#function-documentation}

### bool KEmailAddress::compareEmail(const QString &*email1*, const QString &*email2*, bool *matchName*) {#compareEmail}

Compare two email addresses. If matchName is false, it just checks the email address, and returns true if this matches. If matchName is true, both the name and the email must be the same.

`email1` the first email address to use for comparison

`email2` the second email address to use for comparison

`matchName` if set to true email address and displayname must match

Returns true if the comparison matches true in all other cases

### QString KEmailAddress::decodeMailtoUrl(const QUrl &*mailtoUrl*) {#decodeMailtoUrl}

Extracts the mailbox out of the mailto: URL.

`mailtoUrl` the URL with the mailto protocol, which contains the mailbox to be extracted

Returns the mailbox, which means the display name and the address specification. An empty string is returned if `mailtoUrl` does not use the "mailto" scheme.

### QString KEmailAddress::emailParseResultToString(KEmailAddress::EmailParseResult *errorCode*) {#emailParseResultToString}

Translate the enum errorcodes from emailParseResult into i18n'd strings that can be used for msg boxes.

`errorCode` an error code returned from one of the email validation functions. Do not pass [AddressOk](kemailaddress.md#EmailParseResult-enum) as a value, since that will yield a misleading error message

Returns human-readable and already translated message describing the validation error.

### QUrl KEmailAddress::encodeMailtoUrl(const QString &*mailbox*) {#encodeMailtoUrl}

Creates a valid mailto: URL from the given mailbox.

`mailbox` The mailbox, which means the display name and the address specification, for example "Thomas McGuire" \<thomas@domain.com\>. The display name is optional.

Returns a valid mailto: URL for the given mailbox.

### QByteArray KEmailAddress::extractEmailAddress(const QByteArray &*address*) {#extractEmailAddress}

Returns the pure email address (addr-spec in RFC2822) of the given address (mailbox in RFC2822).

`address` an email address, e.g. "Joe User \<joe.user@example.org\>"

Returns the addr-spec of `address`, i.e. joe.user@example.org in the example

### QString KEmailAddress::extractEmailAddress(const QString &*address*) {#extractEmailAddress-1}

This is an overloaded member function, provided for convenience. It behaves essentially like the above function.

Returns the pure email address (addr-spec in RFC2822) of the given address (mailbox in RFC2822).

`address` an email address, e.g. "Joe User \<joe.user@example.org\>"

Returns the addr-spec of `address`, i.e. joe.user@example.org in the example

### QByteArray KEmailAddress::extractEmailAddress(const QByteArray &*address*, QString &*errorMessage*) {#extractEmailAddress-2}

Returns the pure email address (addr-spec in RFC2822) of the given address (mailbox in RFC2822).

`address` an email address, e.g. "Joe User \<joe.user@example.org\>"

`errorMessage` return error message when we can't parse email

Returns the addr-spec of `address`, i.e. joe.user@example.org in the example

### QString KEmailAddress::extractEmailAddress(const QString &*address*, QString &*errorMessage*) {#extractEmailAddress-3}

Returns the pure email address (addr-spec in RFC2822) of the first email address of a list of addresses.

`address` an email address, e.g. "Joe User \<joe.user@example.org\>"

`errorMessage` return error message when we can't parse email

Returns the addr-spec of `address`, i.e. joe.user@example.org in the example

### bool KEmailAddress::extractEmailAddressAndName(const QString &*aStr*, QString &*mail*, QString &*name*) {#extractEmailAddressAndName}

Return email address and name from string. Examples: "Stefan Taferner \<taferner@example.org\>" returns "taferner@example.org" and "Stefan Taferner". "joe@example.com" returns "joe@example.com" and "". Note that this only returns the first address.

Also note that the return value is true if both the name and the mail are not empty: this does NOT tell you if mail contains a valid email address or just some rubbish.

`aStr` an email address, e.g "Joe User \<joe.user@example.org\>"

`name` only out: returns the displayname, "Joe User" in the example

`mail` only out: returns the email address "joe.user@example.org" in the example

Returns true if both name and email address are not empty

### QByteArray KEmailAddress::firstEmailAddress(const QByteArray &*addresses*) {#firstEmailAddress}

Returns the pure email address (addr-spec in RFC2822) of the first email address of a list of addresses.

`addresses` an email address, e.g. "Joe User \<joe.user@example.org\>"

Returns the addr-spec of `addresses`, i.e. joe.user@example.org in the example

### QString KEmailAddress::firstEmailAddress(const QString &*addresses*) {#firstEmailAddress-1}

This is an overloaded member function, provided for convenience. It behaves essentially like the above function.

Returns the pure email address (addr-spec in RFC2822) of the first email address of a list of addresses.

`addresses` an email address, e.g. "Joe User \<joe.user@example.org\>"

Returns the addr-spec of `addresses`, i.e. joe.user@example.org in the example

### QByteArray KEmailAddress::firstEmailAddress(const QByteArray &*addresses*, QString &*errorMessage*) {#firstEmailAddress-2}

Returns the pure email address (addr-spec in RFC2822) of the first email address of a list of addresses.

`addresses` an email address, e.g. "Joe User \<joe.user@example.org\>"

`errorMessage` return error message when we can't parse email

Returns the addr-spec of `addresses`, i.e. joe.user@example.org in the example

### QString KEmailAddress::firstEmailAddress(const QString &*addresses*, QString &*errorMessage*) {#firstEmailAddress-3}

This is an overloaded member function, provided for convenience. It behaves essentially like the above function.

Returns the pure email address (addr-spec in RFC2822) of the first email address of a list of addresses.

`addresses` an email address, e.g. "Joe User \<joe.user@example.org\>"

`errorMessage` return error message when we can't parse email

Returns the addr-spec of `addresses`, i.e. joe.user@example.org in the example

### QString KEmailAddress::fromIdn(const QString &*addrSpec*) {#fromIdn}

Decodes the punycode domain part of the given addr-spec if it's an IDN.

`addrSpec` a pure 7-bit email address (addr-spec in RFC2822)

Returns the email address with Unicode domain

### KEmailAddress::EmailParseResult KEmailAddress::isValidAddress(const QString &*aStr*) {#isValidAddress}

Validates an email address in the form of "Joe User" \<joe@example.org\>. Returns [AddressOk](kemailaddress.md#EmailParseResult-enum) if no error was encountered. Otherwise an appropriate error code is returned.

`aStr` a single email address, example: Joe User (comment1) \<joe.user@example.org\>

Returns [AddressOk](kemailaddress.md#EmailParseResult-enum) if no error was encountered. Otherwise an appropriate error code is returned.

### KEmailAddress::EmailParseResult KEmailAddress::isValidAddressList(const QString &*aStr*, QString &*badAddr*) {#isValidAddressList}

Validates a list of email addresses, and also allow aliases and distribution lists to be expanded before validation.

`aStr` a string containing a list of email addresses.

`badAddr` a string to hold the address that was faulty.

Returns [AddressOk](kemailaddress.md#EmailParseResult-enum) if no error was encountered. Otherwise an appropriate error code is returned.

### bool KEmailAddress::isValidSimpleAddress(const QString &*aStr*) {#isValidSimpleAddress}

Validates an email address in the form of joe@example.org. Returns true if no error was encountered. This method should be used when the input field should not allow a "full" email address with comments and other special cases that normally are valid in an email address.

`aStr` a single email address, example: joe.user@example.org

Returns true if no error was encountered.

> **Note:** This method differs from calling [isValidAddress](kemailaddress.md#isValidAddress)() and checking that that returns [AddressOk](kemailaddress.md#EmailParseResult-enum) in two ways: it is faster, and it does not allow fancy addresses.

### QString KEmailAddress::normalizeAddressesAndDecodeIdn(const QString &*addresses*) {#normalizeAddressesAndDecodeIdn}

Normalizes all email addresses in the given list and decodes all IDNs.

`addresses` a list of email addresses with punycoded IDNs

Returns the email addresses in normalized form with Unicode IDNs

### QString KEmailAddress::normalizeAddressesAndEncodeIdn(const QString &*str*) {#normalizeAddressesAndEncodeIdn}

Normalizes all email addresses in the given list and encodes all IDNs in punycode.

`str` a list of email addresses

Returns the email addresses in normalized form

### QString KEmailAddress::normalizedAddress(const QString &*displayName*, const QString &*addrSpec*, const QString &*comment* = QString()) {#normalizedAddress}

Returns a normalized address built from the given parts. The normalized address is of one the following forms: - displayName (comment) &lt;addrSpec&gt; - displayName &lt;addrSpec&gt; - comment &lt;addrSpec&gt; - addrSpec

`displayName` the display name of the address

`addrSpec` the actual email address (addr-spec in RFC 2822)

`comment` a comment

Returns a normalized address built from the given parts

### QString KEmailAddress::quoteNameIfNecessary(const QString &*str*) {#quoteNameIfNecessary}

Add quote characters around the given string if it contains a character that makes that necessary, in an email name, such as ",".

`str` a string that may need quoting

Returns the string quoted if necessary

### QString KEmailAddress::simpleEmailAddressErrorMsg() {#simpleEmailAddressErrorMsg}

Returns a i18n string to be used in msgboxes. This allows for error messages to be the same across the board.

Returns An i18n ready string for use in msgboxes.

### KEmailAddress::EmailParseResult KEmailAddress::splitAddress(const QByteArray &*address*, QByteArray &*displayName*, QByteArray &*addrSpec*, QByteArray &*comment*) {#splitAddress}

Splits the given address into display name, email address and comment. Returns [AddressOk](kemailaddress.md#EmailParseResult-enum) if no error was encountered. Otherwise an appropriate error code is returned. In case of an error the values of displayName, addrSpec and comment are undefined.

`address` a single email address, example: Joe User (comment1) \<joe.user@example.org\> (comment2)

`displayName` only out: the display-name of the email address, i.e. "Joe User" in the example; in case of an error the return value is undefined

`addrSpec` only out: the addr-spec, i.e. "joe.user@example.org" in the example; in case of an error the return value is undefined

`comment` only out: the space-separated comments, i.e. "comment1 comment2" in the example; in case of an error the return value is undefined

Returns [AddressOk](kemailaddress.md#EmailParseResult-enum) if no error was encountered. Otherwise an appropriate error code is returned.

### KEmailAddress::EmailParseResult KEmailAddress::splitAddress(const QString &*address*, QString &*displayName*, QString &*addrSpec*, QString &*comment*) {#splitAddress-1}

This is an overloaded member function, provided for convenience. It behaves essentially like the above function.

Splits the given address into display name, email address and comment. Returns [AddressOk](kemailaddress.md#EmailParseResult-enum) if no error was encountered. Otherwise an appropriate error code is returned. In case of an error the values of displayName, addrSpec and comment are undefined.

`address` a single email address, example: Joe User (comment1) \<joe.user@example.org\> (comment2)

`displayName` only out: the display-name of the email address, i.e. "Joe User" in the example; in case of an error the return value is undefined

`addrSpec` only out: the addr-spec, i.e. "joe.user@example.org" in the example; in case of an error the return value is undefined

`comment` only out: the space-separated comments, i.e. "comment1 comment2" in the example; in case of an error the return value is undefined

Returns [AddressOk](kemailaddress.md#EmailParseResult-enum) if no error was encountered. Otherwise an appropriate error code is returned.

### QStringList KEmailAddress::splitAddressList(const QString &*aStr*) {#splitAddressList}

Split a comma separated list of email addresses.

`aStr` a single string representing a list of addresses

Returns a list of strings, where each string is one address from the original list

### QString KEmailAddress::toIdn(const QString &*addrSpec*) {#toIdn}

Encodes the domain part of the given addr-spec in punycode if it's an IDN.

`addrSpec` a pure email address with Unicode domain

Returns the email address with domain in punycode
