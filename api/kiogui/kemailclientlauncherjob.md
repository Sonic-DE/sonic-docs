---
title: "KEMailClientLauncherJob Class"
description: "KEMailClientLauncherJob starts a mail client in order to compose a new mail."
---

# KEMailClientLauncherJob Class

[KEMailClientLauncherJob](kemailclientlauncherjob.md) starts a mail client in order to compose a new mail. [More...](#details)

- **Header:** `#include <KEMailClientLauncherJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [KJob](../kcoreaddons/kjob.md)

[List of all members, including inherited members](kemailclientlauncherjob-members.md)

## Public Functions

- [KEMailClientLauncherJob(QObject \*parent = nullptr)](#KEMailClientLauncherJob)
- [~KEMailClientLauncherJob()](#dtor.KEMailClientLauncherJob)
- [void setAttachments(const QList\<QUrl\> &urls)](#setAttachments)
- [void setBcc(const QStringList &bcc)](#setBcc)
- [void setBody(const QString &body)](#setBody)
- [void setCc(const QStringList &cc)](#setCc)
- [void setStartupId(const QByteArray &startupId)](#setStartupId)
- [void setSubject(const QString &subject)](#setSubject)
- [void setTo(const QStringList &to)](#setTo)
- [void start()](#start)

## Detailed Description {#details}

It creates a startup notification and finishes it on success or on error (for the taskbar). It also emits an error message if necessary (e.g. "program not found").

The job finishes when the application is successfully started. For error handling, either connect to the [result](../kcoreaddons/kjob.md#result)() signal, or for a simple messagebox on error, you can do

```cpp
job->setUiDelegate(new KDialogJobUiDelegate(KJobUiDelegate::AutoHandlingEnabled, this));
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KEMailClientLauncherJob::KEMailClientLauncherJob(QObject \**parent* = nullptr) {#KEMailClientLauncherJob}

Creates a [KEMailClientLauncherJob](kemailclientlauncherjob.md).

`parent` the parent [QObject](https://doc.qt.io/qt-6/qobject.html)

### \[override virtual noexcept\] KEMailClientLauncherJob::~KEMailClientLauncherJob() {#dtor.KEMailClientLauncherJob}

Destructor

Note that jobs auto-delete themselves after emitting result

### void KEMailClientLauncherJob::setAttachments(const QList\<QUrl\> &*urls*) {#setAttachments}

Sets attachments for the email

`urls` URLs of the attachments for the email

Remember to use [QUrl::fromLocalFile](https://doc.qt.io/qt-6/qurl.html#fromLocalFile)() to construct those URLs from local file paths.

### void KEMailClientLauncherJob::setBcc(const QStringList &*bcc*) {#setBcc}

Sets the email address(es) that will be used in the Bcc field for the email

`bcc` recipients; each entry can use the format "someone@example.com" or "John Doe \<someone@example.com\>"

### void KEMailClientLauncherJob::setBody(const QString &*body*) {#setBody}

Sets the body for the email

`body` the email body

### void KEMailClientLauncherJob::setCc(const QStringList &*cc*) {#setCc}

Sets the email address(es) that will be used in the CC field for the email

`cc` recipients; each entry can use the format "someone@example.com" or "John Doe \<someone@example.com\>"

### void KEMailClientLauncherJob::setStartupId(const QByteArray &*startupId*) {#setStartupId}

Sets the platform-specific startup id of the mail client launch.

`startupId` startup id, if any (otherwise "").

For X11, this would be the id for the Startup Notification protocol.

### void KEMailClientLauncherJob::setSubject(const QString &*subject*) {#setSubject}

Sets the subject for the email

`subject` the email subject

### void KEMailClientLauncherJob::setTo(const QStringList &*to*) {#setTo}

Sets the email address(es) that will be used in the To field for the email

`to` recipients; each entry can use the format "someone@example.com" or "John Doe \<someone@example.com\>"

### \[override virtual\] void KEMailClientLauncherJob::start() {#start}

Reimplements: [KJob::start()](../kcoreaddons/kjob.md#start).

Starts the job.

You must call this, after having called all the necessary setters.
