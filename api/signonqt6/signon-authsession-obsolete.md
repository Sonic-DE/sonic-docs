---
title: "Obsolete Members for SignOn::AuthSession"
description: "Deprecated members of SignOn::AuthSession."
parent: "signonqt6/signon-authsession"
---

# Obsolete Members for SignOn::AuthSession

**The following members of class [AuthSession](signon-authsession.md) are deprecated.** We strongly advise against using them in new code.

## Public Types

- [\[deprecated\] enum AuthSession::AuthSessionError](#AuthSessionError-enum)

## Public Functions

- [void signMessage(const SignOn::SessionData &params, const QString &mechanism = QString())](#signMessage)

## Obsolete Member Type Documentation {#obsolete-member-type-documentation}

### \[deprecated\] enum AuthSession::AuthSessionError {#AuthSessionError-enum}

This enum is deprecated. We strongly advise against using it in new code.

Codes for errors that may be reported by [AuthSession](signon-authsession.md) objects

This enum is deprecated. Replaced by [Error::ErrorType](signon-error.md#ErrorType-enum).

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::AuthSession::UnknownError` | `1` | Catch-all for errors not distinguished by another code. |
| `SignOn::AuthSession::InternalServerError` | `2` | Signon Daemon internal error. |
| `SignOn::AuthSession::InternalCommunicationError` | `3` | Communication with Signon Daemon error. |
| `SignOn::AuthSession::PermissionDeniedError` | `4` | The operation cannot be performed due to insufficient client permissions. |
| `SignOn::AuthSession::MechanismNotAvailableError` | `301` | The requested mechanism is not available. |
| `SignOn::AuthSession::MissingDataError` | `302` | The [SessionData](signon-sessiondata.md) object does not contain necessary information. |
| `SignOn::AuthSession::InvalidCredentialsError` | `303` | The supplied credentials are invalid for the mechanism implementation. |
| `SignOn::AuthSession::WrongStateError` | `304` | An operation method has been called in a wrong state. |
| `SignOn::AuthSession::OperationNotSupportedError` | `305` | The operation is not supported by the mechanism implementation. |
| `SignOn::AuthSession::NoConnectionError` | `306` | No Network connection. |
| `SignOn::AuthSession::NetworkError` | `307` | Network connection failed. |
| `SignOn::AuthSession::SslError` | `308` | Ssl connection failed. |
| `SignOn::AuthSession::RuntimeError` | `309` | Casting [SessionData](signon-sessiondata.md) into subclass failed |
| `SignOn::AuthSession::CanceledError` | `310` | Challenge was canceled. |
| `SignOn::AuthSession::TimedOutError` | `311` | Challenge was timed out. |
| `SignOn::AuthSession::UserInteractionError` | `312` | User interaction dialog failed |

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated\] void AuthSession::signMessage(const SignOn::SessionData &*params*, const QString &*mechanism* = QString()) {#signMessage}

This function is deprecated. We strongly advise against using it in new code.

Signs message by using secret stored into identity. This convenience interface is to do special challenge to signature service. `params` holds extra information for signing, and `mechanism` is the mechanism to use for signing.
