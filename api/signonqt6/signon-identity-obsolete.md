---
title: "Obsolete Members for SignOn::Identity"
description: "Deprecated members of SignOn::Identity."
parent: "signonqt6/signon-identity"
---

# Obsolete Members for SignOn::Identity

**The following members of class [Identity](signon-identity.md) are deprecated.** We strongly advise against using them in new code.

## Public Types

- [\[deprecated\] enum Identity::IdentityError](#IdentityError-enum)

## Obsolete Member Type Documentation {#obsolete-member-type-documentation}

### \[deprecated\] enum Identity::IdentityError {#IdentityError-enum}

This enum is deprecated. We strongly advise against using it in new code.

Codes for errors that may be reported by Identity objects

This enum is deprecated. Replaced by [Error::ErrorType](signon-error.md#ErrorType-enum).

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::Identity::UnknownError` | `1` | Catch-all for errors not distinguished by another code. |
| `SignOn::Identity::InternalServerError` | `2` | Signon Daemon internal error. |
| `SignOn::Identity::InternalCommunicationError` | `3` | Communication with Signon Daemon error. |
| `SignOn::Identity::PermissionDeniedError` | `4` | The operation cannot be performed due to insufficient client permissions. |
| `SignOn::Identity::MethodNotAvailableError` | `201` | The requested mechanism is not available. |
| `SignOn::Identity::NotFoundError` | `202` | The identity matching this Identity object was not found on the service. |
| `SignOn::Identity::StoreFailedError` | `203` | Storing credentials failed. |
| `SignOn::Identity::RemoveFailedError` | `204` | Removing credentials failed. |
| `SignOn::Identity::SignOutFailedError` | `205` | SignOut failed. |
| `SignOn::Identity::CanceledError` | `206` | Operation was canceled by user. |
| `SignOn::Identity::CredentialsNotAvailableError` | `207` | Query fails |
