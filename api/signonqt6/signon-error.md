---
title: "SignOn::Error Class"
description: "Base object definition for Signon error handling."
---

# SignOn::Error Class

Base object definition for Signon error handling. [More...](#details)

- **Header:** `#include <SignOn/Error>`
- **CMake:** `find_package(SignOnQt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SignOnQt6::SignOnQt6)`

[List of all members, including inherited members](signon-error-members.md)

## Public Types

- [enum Error::ErrorType](#ErrorType-enum)

## Public Functions

- [Error()](#Error)
- [Error(int type, const QString &message = QString())](#Error-2)
- [Error(const SignOn::Error &src)](#Error-1)
- [~Error()](#dtor.Error)
- [QString message() const](#message)
- [void setMessage(const QString &message)](#setMessage)
- [void setType(int type)](#setType)
- [int type() const](#type)
- [SignOn::Error &Error::operator=(const SignOn::Error &src)](#operator-eq)

## Detailed Description {#details}

Extend this class' error range in order to provide custom error handling.

> **Note:** All this class' definitions must be inline.

## Member Type Documentation {#member-type-documentation}

### enum Error::ErrorType {#ErrorType-enum}

Error codes for all the Signon by default supported errors. Plugin developers should use the predefined error types in the AuthSessionErr and UserErr interval, and in the case of extended error handling values greater than UserErr.

> **Note:** Error types lesser than Error::UserErr are reserved.

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::Error::Unknown` | `1` | Catch-all for errors not distinguished by another code. |
| `SignOn::Error::InternalServer` | `2` | Signon Daemon internal error. |
| `SignOn::Error::InternalCommunication` | `3` | Communication with Signon Daemon error. |
| `SignOn::Error::PermissionDenied` | `4` | The operation cannot be performed due to insufficient client permissions. |
| `SignOn::Error::EncryptionFailure` | `5` | Failure during data encryption/decryption. |
| `SignOn::Error::AuthServiceErr` | `100` | Placeholder to rearrange enumeration - [AuthService](signon-authservice.md) specific |
| `SignOn::Error::MethodNotKnown` | `101` | The method with this name is not found. |
| `SignOn::Error::ServiceNotAvailable` | `102` | The service is temporarily unavailable. |
| `SignOn::Error::InvalidQuery` | `103` | Parameters for the query are invalid. |
| `SignOn::Error::IdentityErr` | `200` | Placeholder to rearrange enumeration - Identity specific |
| `SignOn::Error::MethodNotAvailable` | `201` | The requested method is not available. |
| `SignOn::Error::IdentityNotFound` | `202` | The identity matching this Identity object was not found on the service. |
| `SignOn::Error::StoreFailed` | `203` | Storing credentials failed. |
| `SignOn::Error::RemoveFailed` | `204` | Removing credentials failed. |
| `SignOn::Error::SignOutFailed` | `205` | SignOut failed. |
| `SignOn::Error::IdentityOperationCanceled` | `206` | Identity operation was canceled by user. |
| `SignOn::Error::CredentialsNotAvailable` | `207` | Query failed. |
| `SignOn::Error::ReferenceNotFound` | `208` | Trying to remove nonexistent reference. |
| `SignOn::Error::AuthSessionErr` | `300` | Placeholder to rearrange enumeration - [AuthSession](signon-authsession.md)/AuthPluginInterface specific |
| `SignOn::Error::MechanismNotAvailable` | `301` | The requested mechanism is not available. |
| `SignOn::Error::MissingData` | `302` | The [SessionData](signon-sessiondata.md) object does not contain necessary information. |
| `SignOn::Error::InvalidCredentials` | `303` | The supplied credentials are invalid for the mechanism implementation. |
| `SignOn::Error::NotAuthorized` | `304` | Authorization failed. |
| `SignOn::Error::WrongState` | `305` | An operation method has been called in a wrong state. |
| `SignOn::Error::OperationNotSupported` | `306` | The operation is not supported by the mechanism implementation. |
| `SignOn::Error::NoConnection` | `307` | No Network connection. |
| `SignOn::Error::Network` | `308` | Network connection failed. |
| `SignOn::Error::Ssl` | `309` | Ssl connection failed. |
| `SignOn::Error::Runtime` | `310` | Casting [SessionData](signon-sessiondata.md) into subclass failed |
| `SignOn::Error::SessionCanceled` | `311` | Challenge was cancelled. |
| `SignOn::Error::TimedOut` | `312` | Challenge was timed out. |
| `SignOn::Error::UserInteraction` | `313` | User interaction dialog failed |
| `SignOn::Error::OperationFailed` | `314` | Temporary failure in authentication. |
| `SignOn::Error::EncryptionFailed` | `315` | Deprecated: failure during data encryption/decryption. |
| `SignOn::Error::TOSNotAccepted` | `316` | User declined Terms of Service. |
| `SignOn::Error::ForgotPassword` | `317` | User requested reset password sequence. |
| `SignOn::Error::MethodOrMechanismNotAllowed` | `318` | Method or mechanism not allowed for this identity. |
| `SignOn::Error::IncorrectDate` | `319` | Date time incorrect on device. |
| `SignOn::Error::UserErr` | `400` | Placeholder to rearrange enumeration - User space specific |

## Member Function Documentation {#member-function-documentation}

### Error::Error() {#Error}

Constructor

### Error::Error(int *type*, const QString &*message* = QString()) {#Error-2}

For convenience constructor, with the `type` of the error and the error `message`.

### Error::Error(const SignOn::Error &*src*) {#Error-1}

Copy constructor, copying `src`.

### \[virtual noexcept\] Error::~Error() {#dtor.Error}

Destructor

### QString Error::message() const {#message}

Returns the error message.

*See also* [setMessage](signon-error.md#setMessage)()

### void Error::setMessage(const QString &*message*) {#setMessage}

Sets the error `message`.

*See also* [message](signon-error.md#message)()

### void Error::setType(int *type*) {#setType}

Sets the `type` of the error. The type is an integer and values beyond [Error::ErrorType](signon-error.md#ErrorType-enum) can be used for customized error reporting.

*See also* [type](signon-error.md#type)(), [Error::ErrorType](signon-error.md#ErrorType-enum)

### int Error::type() const {#type}

Returns the type of the error.

*See also* [setType](signon-error.md#setType)()

### SignOn::Error &Error::operator=(const SignOn::Error &*src*) {#operator-eq}

Assignment operator, assigning `src` to this instance.
