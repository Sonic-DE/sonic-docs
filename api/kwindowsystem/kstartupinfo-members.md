---
title: "List of All Members for KStartupInfo"
description: "Every member of KStartupInfo, including inherited members."
parent: "kwindowsystem/kstartupinfo"
---

# List of All Members for KStartupInfo

This is the complete list of members for [KStartupInfo](kstartupinfo.md), including inherited members.

- [KStartupInfo(int, QObject \*)](kstartupinfo.md#KStartupInfo)
- [appStarted()](kstartupinfo.md#appStarted)
- [appStarted(const QByteArray &)](kstartupinfo.md#appStarted-1)
- [checkStartup(WId) : KStartupInfo::startup\_t](kstartupinfo.md#checkStartup)
- [checkStartup(WId, KStartupInfoData &) : KStartupInfo::startup\_t](kstartupinfo.md#checkStartup-1)
- [checkStartup(WId, KStartupInfoId &) : KStartupInfo::startup\_t](kstartupinfo.md#checkStartup-2)
- [checkStartup(WId, KStartupInfoId &, KStartupInfoData &) : KStartupInfo::startup\_t](kstartupinfo.md#checkStartup-3)
- [createNewStartupId() : QByteArray](kstartupinfo.md#createNewStartupId)
- [createNewStartupIdForTimestamp(quint32) : QByteArray](kstartupinfo.md#createNewStartupIdForTimestamp)
- [gotNewStartup(const KStartupInfoId &, const KStartupInfoData &)](kstartupinfo.md#gotNewStartup)
- [gotRemoveStartup(const KStartupInfoId &, const KStartupInfoData &)](kstartupinfo.md#gotRemoveStartup)
- [gotStartupChange(const KStartupInfoId &, const KStartupInfoData &)](kstartupinfo.md#gotStartupChange)
- [resetStartupEnv()](kstartupinfo.md#resetStartupEnv)
- [sendChange(const KStartupInfoId &, const KStartupInfoData &) : bool](kstartupinfo.md#sendChange)
- [sendChangeXcb(xcb\_connection\_t \*, int, const KStartupInfoId &, const KStartupInfoData &) : bool](kstartupinfo.md#sendChangeXcb)
- [sendFinish(const KStartupInfoId &) : bool](kstartupinfo.md#sendFinish)
- [sendFinish(const KStartupInfoId &, const KStartupInfoData &) : bool](kstartupinfo.md#sendFinish-1)
- [sendFinishXcb(xcb\_connection\_t \*, int, const KStartupInfoId &) : bool](kstartupinfo.md#sendFinishXcb)
- [sendFinishXcb(xcb\_connection\_t \*, int, const KStartupInfoId &, const KStartupInfoData &) : bool](kstartupinfo.md#sendFinishXcb-1)
- [sendStartup(const KStartupInfoId &, const KStartupInfoData &) : bool](kstartupinfo.md#sendStartup)
- [sendStartupXcb(xcb\_connection\_t \*, int, const KStartupInfoId &, const KStartupInfoData &) : bool](kstartupinfo.md#sendStartupXcb)
- [setNewStartupId(QWindow \*, const QByteArray &)](kstartupinfo.md#setNewStartupId)
- [setStartupId(const QByteArray &)](kstartupinfo.md#setStartupId)
- [setTimeout(unsigned int)](kstartupinfo.md#setTimeout)
- [windowStartupId(WId) : QByteArray](kstartupinfo.md#windowStartupId)

KStartupInfo also inherits the members of [QObject](https://doc.qt.io/qt-6/qobject-members.html).
