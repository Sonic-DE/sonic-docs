---
title: "KDarkLightScheduleProvider Class"
description: "The KDarkLightScheduleProvider provides a convenient way to retrieve the schedule of the dark-light cycle."
---

# KDarkLightScheduleProvider Class

The [KDarkLightScheduleProvider](kdarklightscheduleprovider.md) provides a convenient way to retrieve the schedule of the dark-light cycle. [More...](#details)

- **Header:** `#include <KDarkLightScheduleProvider>`
- **CMake:** `find_package(KNightTime REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE KNightTime::KNightTime)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kdarklightscheduleprovider-members.md)

## Public Functions

- [KDarkLightScheduleProvider(const QString &state = QString(), QObject \*parent = nullptr)](#KDarkLightScheduleProvider)
- [KDarkLightSchedule schedule() const](#schedule)
- [QString state() const](#state)

## Signals

- [void scheduleChanged()](#scheduleChanged)

## Detailed Description {#details}

Example usage:

```cpp
auto stateConfig = KSharedConfig::openStateConfig();
auto provider = new KDarkLightScheduleProvider(stateConfig->group(QStringLiteral("DarkLightCycle")).readEntry(QStringLiteral("State")));
connect(provider, &KDarkLightScheduleProvider::scheduleChanged, [provider, stateConfig]() {
    stateConfig->group(QStringLiteral("DarkLightCycle")).writeEntry(QStringLiteral("State"), provider->state());
    stateConfig->sync();

    qDebug() << "next transition:" << provider->schedule().nextTransition(QDateTime::currentDateTime());
});

qDebug() << "next transition:" << provider->schedule().nextTransition(QDateTime::currentDateTime());
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDarkLightScheduleProvider::KDarkLightScheduleProvider(const QString &*state* = QString(), QObject \**parent* = nullptr) {#KDarkLightScheduleProvider}

Constructs the schedule provider. If a `state` string is specified, the previous schedule will be restored.

If no state string is given, the provider will use the default schedule until the current one is retrieved asynchronously. With the default schedule, morning lasts from 6:00AM to 6:30AM, and evening lasts from 6:00PM to 6:30PM.

### KDarkLightSchedule KDarkLightScheduleProvider::schedule() const {#schedule}

Returns the schedule of the dark-light cycle.

### \[signal\] void KDarkLightScheduleProvider::scheduleChanged() {#scheduleChanged}

This signal is emitted when the schedule is refreshed.

### QString KDarkLightScheduleProvider::state() const {#state}

Returns the corresponding state string. The state string can be stored in a state config to restore the schedule after a reboot. It can be used to reduce the number of unnecessary animations at system startup.
