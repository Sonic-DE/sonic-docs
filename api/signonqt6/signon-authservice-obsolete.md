---
title: "Obsolete Members for SignOn::AuthService"
description: "Deprecated members of SignOn::AuthService."
parent: "signonqt6/signon-authservice"
---

# Obsolete Members for SignOn::AuthService

**The following members of class [AuthService](signon-authservice.md) are deprecated.** We strongly advise against using them in new code.

## Public Types

- [\[deprecated\] enum AuthService::ServiceError](#ServiceError-enum)

## Obsolete Member Type Documentation {#obsolete-member-type-documentation}

### \[deprecated\] enum AuthService::ServiceError {#ServiceError-enum}

This enum is deprecated. We strongly advise against using it in new code.

Codes for errors that may be reported by [AuthService](signon-authservice.md) objects.

This enum is deprecated. Replaced by [Error::ErrorType](signon-error.md#ErrorType-enum).

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::AuthService::UnknownError` | `1` | Catch-all for errors not distinguished by another code. |
| `SignOn::AuthService::InternalServerError` | `2` | Signon Daemon internal error. |
| `SignOn::AuthService::InternalCommunicationError` | `3` | Communication with Signon Daemon error. |
| `SignOn::AuthService::PermissionDeniedError` | `4` | The operation cannot be performed due to insufficient client permissions. |
| `SignOn::AuthService::MethodNotKnownError` | `101` | The method with this name is not found. |
| `SignOn::AuthService::NotAvailableError` | `102` | The service is temporarily unavailable. |
| `SignOn::AuthService::InvalidQueryError` | `103` | Parameters for the query are invalid. |
