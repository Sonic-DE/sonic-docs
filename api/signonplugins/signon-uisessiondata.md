---
title: "SignOn::UiSessionData Class"
description: "Data container to hold values for the user interaction of an authentication session."
---

# SignOn::UiSessionData Class

Data container to hold values for the user interaction of an authentication session. [More...](#details)

- **Header:** `#include <SignOn/UiSessionData>`
- **Inherits:** [SignOn::SessionData](../signonqt6/signon-sessiondata.md)

[List of all members, including inherited members](signon-uisessiondata-members.md)

## Public Functions

- [UiSessionData(const QVariantMap &data = QVariantMap())](#UiSessionData)
- [void setCaptchaImage(const QByteArray &value)](#setCaptchaImage)
- [QByteArray CaptchaImage() const](#CaptchaImage)
- [void setCaptchaResponse(const QString &value)](#setCaptchaResponse)
- [QString CaptchaResponse() const](#CaptchaResponse)
- [void setCaptchaUrl(const QString &value)](#setCaptchaUrl)
- [QString CaptchaUrl() const](#CaptchaUrl)
- [void setCaption(const QString &value)](#setCaption)
- [QString Caption() const](#Caption)
- [void setConfirm(const bool &value)](#setConfirm)
- [bool Confirm() const](#Confirm)
- [void setFinalUrl(const QString &value)](#setFinalUrl)
- [QString FinalUrl() const](#FinalUrl)
- [void setForgotPassword(const QString &value)](#setForgotPassword)
- [QString ForgotPassword() const](#ForgotPassword)
- [void setForgotPasswordUrl(const QString &value)](#setForgotPasswordUrl)
- [QString ForgotPasswordUrl() const](#ForgotPasswordUrl)
- [void setIcon(const QString &value)](#setIcon)
- [QString Icon() const](#Icon)
- [void setOpenUrl(const QString &value)](#setOpenUrl)
- [QString OpenUrl() const](#OpenUrl)
- [void setQueryErrorCode(const int &value)](#setQueryErrorCode)
- [int QueryErrorCode() const](#QueryErrorCode)
- [void setQueryMessage(const QString &value)](#setQueryMessage)
- [QString QueryMessage() const](#QueryMessage)
- [void setQueryMessageId(const int &value)](#setQueryMessageId)
- [int QueryMessageId() const](#QueryMessageId)
- [void setQueryPassword(const bool &value)](#setQueryPassword)
- [bool QueryPassword() const](#QueryPassword)
- [void setQueryUserName(const bool &value)](#setQueryUserName)
- [bool QueryUserName() const](#QueryUserName)
- [void setRememberPassword(const bool &value)](#setRememberPassword)
- [bool RememberPassword() const](#RememberPassword)
- [void setShowRealm(const bool &value)](#setShowRealm)
- [bool ShowRealm() const](#ShowRealm)
- [void setTitle(const QString &value)](#setTitle)
- [QString Title() const](#Title)
- [void setUrlResponse(const QString &value)](#setUrlResponse)
- [QString UrlResponse() const](#UrlResponse)

## Detailed Description {#details}

Inherit this class if you want to extend the property range.

> **Warning:** All this class' definitions must be inline.

## Member Function Documentation {#member-function-documentation}

### UiSessionData::UiSessionData(const QVariantMap &*data* = QVariantMap()) {#UiSessionData}

Constructor. Creates a [UiSessionData](signon-uisessiondata.md) containing `data`.

> **Note:** Internal use only recommended. As a SSO client application developer use setters/getters for specific SessionData properties.

### void UiSessionData::setCaptchaImage(const QByteArray &*value*) {#setCaptchaImage}

### QByteArray UiSessionData::CaptchaImage() const {#CaptchaImage}

The property [CaptchaImage](signon-uisessiondata.md#CaptchaImage) contains the captcha image to be verified by user. [CaptchaImage](signon-uisessiondata.md#CaptchaImage) is passed to signon-ui when plugin requires the captcha verification from user. If this is empty, captcha query is not shown, unless [CaptchaUrl](signon-uisessiondata.md#CaptchaUrl) point to valid image.

### void UiSessionData::setCaptchaResponse(const QString &*value*) {#setCaptchaResponse}

### QString UiSessionData::CaptchaResponse() const {#CaptchaResponse}

The property [CaptchaResponse](signon-uisessiondata.md#CaptchaResponse) is passed to plugin after signon-ui has processed the captcha query. It contains user input for captcha query.

*See also* [CaptchaUrl](signon-uisessiondata.md#CaptchaUrl)(), [CaptchaImage](signon-uisessiondata.md#CaptchaImage)()

### void UiSessionData::setCaptchaUrl(const QString &*value*) {#setCaptchaUrl}

### QString UiSessionData::CaptchaUrl() const {#CaptchaUrl}

The property [CaptchaUrl](signon-uisessiondata.md#CaptchaUrl) contains url to the captcha image to be verified by user. [CaptchaUrl](signon-uisessiondata.md#CaptchaUrl) is used in signon-ui when plugin requires the captcha verification from user. If this is empty, captcha query is not shown, unless [CaptchaImage](signon-uisessiondata.md#CaptchaImage) contain valid image.

### void UiSessionData::setCaption(const QString &*value*) {#setCaption}

### QString UiSessionData::Caption() const {#Caption}

The property Caption is used to set credentials caption. Empty caption is discarded.

> **Warning:** This string is shown to user as it is, plugin is responsible for localization.

### void UiSessionData::setConfirm(const bool &*value*) {#setConfirm}

### bool UiSessionData::Confirm() const {#Confirm}

The property Confirm will set dialog to confirm password mode.

### void UiSessionData::setFinalUrl(const QString &*value*) {#setFinalUrl}

### QString UiSessionData::FinalUrl() const {#FinalUrl}

The property [FinalUrl](signon-uisessiondata.md#FinalUrl): if this URL is set, the signon-ui browser widget will close automatically when this URL is reached.

### void UiSessionData::setForgotPassword(const QString &*value*) {#setForgotPassword}

### QString UiSessionData::ForgotPassword() const {#ForgotPassword}

The property [ForgotPassword](signon-uisessiondata.md#ForgotPassword): this string is shown as a link to user.

*See also* [ForgotPasswordUrl](signon-uisessiondata.md#ForgotPasswordUrl)()

### void UiSessionData::setForgotPasswordUrl(const QString &*value*) {#setForgotPasswordUrl}

### QString UiSessionData::ForgotPasswordUrl() const {#ForgotPasswordUrl}

The property [ForgotPasswordUrl](signon-uisessiondata.md#ForgotPasswordUrl) is shown to user if [ForgotPassword](signon-uisessiondata.md#ForgotPassword) link is pressed.

*See also* [ForgotPassword](signon-uisessiondata.md#ForgotPassword)()

### void UiSessionData::setIcon(const QString &*value*) {#setIcon}

### QString UiSessionData::Icon() const {#Icon}

The property Icon is shown to user in signin dialog.

### void UiSessionData::setOpenUrl(const QString &*value*) {#setOpenUrl}

### QString UiSessionData::OpenUrl() const {#OpenUrl}

The property [OpenUrl](signon-uisessiondata.md#OpenUrl): this url is passed to signon-ui to be opened and shown to user. Empty url does not open the url view.

### void UiSessionData::setQueryErrorCode(const int &*value*) {#setQueryErrorCode}

### int UiSessionData::QueryErrorCode() const {#QueryErrorCode}

The property [QueryErrorCode](signon-uisessiondata.md#QueryErrorCode) is used to report errors in ui interaction that is shown to user.

*See also* [SignOn::QueryError](signon-uisessiondata.md#QueryError-enum)

### void UiSessionData::setQueryMessage(const QString &*value*) {#setQueryMessage}

### QString UiSessionData::QueryMessage() const {#QueryMessage}

The property [QueryMessage](signon-uisessiondata.md#QueryMessage) is used to show given message to user. Empty message is discarded.

> **Warning:** This string is shown to user as it is, plugin is responsible for localization.

### void UiSessionData::setQueryMessageId(const int &*value*) {#setQueryMessageId}

### int UiSessionData::QueryMessageId() const {#QueryMessageId}

The property [QueryMessageId](signon-uisessiondata.md#QueryMessageId) is used to select predefined localized message that is shown to user.

*See also* [SignOn::QueryMessageId](signon-uisessiondata.md#QueryMessageId-enum)

### void UiSessionData::setQueryPassword(const bool &*value*) {#setQueryPassword}

### bool UiSessionData::QueryPassword() const {#QueryPassword}

The property [QueryPassword](signon-uisessiondata.md#QueryPassword) is used to enable password input in signon-ui.

### void UiSessionData::setQueryUserName(const bool &*value*) {#setQueryUserName}

### bool UiSessionData::QueryUserName() const {#QueryUserName}

The property [QueryUserName](signon-uisessiondata.md#QueryUserName) is used to enable username input in signon-ui.

### void UiSessionData::setRememberPassword(const bool &*value*) {#setRememberPassword}

### bool UiSessionData::RememberPassword() const {#RememberPassword}

The property [RememberPassword](signon-uisessiondata.md#RememberPassword) is used to enable password storing signond.

### void UiSessionData::setShowRealm(const bool &*value*) {#setShowRealm}

### bool UiSessionData::ShowRealm() const {#ShowRealm}

The property [ShowRealm](signon-uisessiondata.md#ShowRealm) is used to show realm in signon-ui.

### void UiSessionData::setTitle(const QString &*value*) {#setTitle}

### QString UiSessionData::Title() const {#Title}

The property Title is used to set dialog title for password confirmation.

> **Warning:** This string is shown to user as it is.

### void UiSessionData::setUrlResponse(const QString &*value*) {#setUrlResponse}

### QString UiSessionData::UrlResponse() const {#UrlResponse}

The property [UrlResponse](signon-uisessiondata.md#UrlResponse): the response from signon-ui for [OpenUrl](signon-uisessiondata.md#OpenUrl) request. After completion [UrlResponse](signon-uisessiondata.md#UrlResponse) contains redirect target url, if there was redirection.

## Related Non-Members {#related-non-members}

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
