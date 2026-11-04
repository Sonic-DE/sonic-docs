---
title: "SignOn Namespace"
description: "The SignOn namespace includes the following elements from module SignOnPlugins. The full namespace is documented in module SignOnQt6 here.."
---

# SignOn Namespace

The SignOn namespace includes the following elements from module SignOnPlugins. The full namespace is documented in module SignOnQt6 here..

## Classes {#classes}

### class [UiSessionData](signon-uisessiondata.md)

Data container to hold values for the user interaction of an authentication session.

## Type Documentation {#type-documentation}

### enum QueryError {#QueryError-enum}

Error codes for ui interaction.

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::UiSessionData::QUERY_ERROR_NONE` | `0` | No errors. |
| `SignOn::UiSessionData::QUERY_ERROR_GENERAL` | `1` | Generic error during interaction. |
| `SignOn::UiSessionData::QUERY_ERROR_NO_SIGNONUI` | `2` | Cannot send request to signon-ui. |
| `SignOn::UiSessionData::QUERY_ERROR_BAD_PARAMETERS` | `3` | Signon-Ui cannot create dialog based on the given [UiSessionData](signon-uisessiondata.md). |
| `SignOn::UiSessionData::QUERY_ERROR_CANCELED` | `4` | User canceled action. Plugin should not retry automatically after this. |
| `SignOn::UiSessionData::QUERY_ERROR_NOT_AVAILABLE` | `5` | Requested ui is not available. For example browser cannot be started. |
| `SignOn::UiSessionData::QUERY_ERROR_BAD_URL` | `6` | Given url was not valid. |
| `SignOn::UiSessionData::QUERY_ERROR_BAD_CAPTCHA` | `7` | Given captcha image was not valid. |
| `SignOn::UiSessionData::QUERY_ERROR_BAD_CAPTCHA_URL` | `8` | Given url for captcha loading was not valid. |
| `SignOn::UiSessionData::QUERY_ERROR_REFRESH_FAILED` | `9` | Refresh failed. |
| `SignOn::UiSessionData::QUERY_ERROR_FORBIDDEN` | `10` | Showing ui forbidden by ui policy. |
| `SignOn::UiSessionData::QUERY_ERROR_FORGOT_PASSWORD` | `11` | User pressed forgot password. |
| `SignOn::UiSessionData::QUERY_ERROR_NETWORK` | `12` | Network error. |
| `SignOn::UiSessionData::QUERY_ERROR_SSL` | `13` | SSL error. |

### enum QueryMessageId {#QueryMessageId-enum}

Predefined messages to be shown to user while querying input.

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::UiSessionData::QUERY_MESSAGE_EMPTY` | `0` | No predefined message. |
| `SignOn::UiSessionData::QUERY_MESSAGE_LOGIN` | `1` | Login without prior errors. |
| `SignOn::UiSessionData::QUERY_MESSAGE_NOT_AUTHORIZED` | `2` | Authentication failed. |
