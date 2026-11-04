---
title: KIdleTime
description: Detect and handle the system being idle.
source_url: https://develop.kde.org/docs/features/kidletime/
source_authors: [Andreas Cord-Landwehr, Carl Schwan, Chris Holland, Mikhail Zolotukhin, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-idle-tracker (src/kidletime.h, src/plugins/xsync, examples/KIdleTest.cpp); the example was built against SonicDE's KIdleTime (not run; it needs an X session)
---

# KIdleTime

[KIdleTime](/docs/api/kidletime/kidletime), in `sonic-frameworks-idle-tracker` (`find_package(KF6IdleTime)`, `KF6::IdleTime`), reports how long the system has been idle. Besides the current idle time, it notifies you of idle events, such as timeouts you set or the user becoming active again. It offers:

- the current idle time
- timeout notifications, emitted when the system has been idle for a given time
- activity notifications, when the user becomes active again after being idle

On SonicDE it measures idle time with the X server's XSync extension.

## Using it

The example is a small test program, "KIdleTest". It waits for the user's first action, then registers some idle timeouts and reacts whenever the system has been idle that long. The singleton `KIdleTime::instance()` provides all the signals and information about the idle state. First, connect to the signals for the user becoming active again and for the timeouts you will set:

```cpp
KIdleTest::KIdleTest()
{
    // connect to idle events
    connect(KIdleTime::instance(), &KIdleTime::resumingFromIdle, this, &KIdleTest::resumeEvent);
    connect(KIdleTime::instance(), qOverload<int, int>(&KIdleTime::timeoutReached), this, &KIdleTest::timeoutReached);

    // register to get informed for the very next user event
    KIdleTime::instance()->catchNextResumeEvent();

    printf("Your idle time is %d\n", KIdleTime::instance()->idleTime());
    printf("Welcome!! Move your mouse or do something to start...\n");
}
```

`catchNextResumeEvent()` asks KIdleTime to report the user's next action. It applies only to that one next time; for later events, call `catchNextResumeEvent()` again.

When the user becomes active, the handler registers some idle timeouts:

```cpp
void KIdleTest::resumeEvent()
{
    KIdleTime::instance()->removeAllIdleTimeouts();

    printf("Great! Now stay idle for 5 seconds to get a nice message. From 10 seconds on, you can move your mouse to get back here.\n");
    printf("If you will stay idle for too long, I will simulate your activity after 25 seconds, and make everything start back\n");

    KIdleTime::instance()->addIdleTimeout(5000);
    KIdleTime::instance()->addIdleTimeout(10000);
    KIdleTime::instance()->addIdleTimeout(25000);
}
```

`addIdleTimeout()` takes milliseconds (an `int` or a `std::chrono::milliseconds`) and returns an ID for the timeout. When the system has been idle for one of these times, the `timeoutReached()` slot connected earlier is called with the timeout's ID and length, and prints a message:

```cpp
void KIdleTest::timeoutReached(int id, int timeout)
{
    Q_UNUSED(id)

    if (timeout == 5000) {
        printf("5 seconds passed, stay still some more...\n");
    } else if (timeout == 10000) {
        KIdleTime::instance()->catchNextResumeEvent();
        printf("Cool. You can move your mouse to start over\n");
    } else if (timeout == 25000) {
        printf("Uff, you're annoying me. Let's start again. I'm simulating your activity now\n");
        KIdleTime::instance()->simulateUserActivity();
    } else {
        qDebug() << "OUCH";
    }
}
```

Depending on the timeout reached, the program goes back to one of the earlier steps. A timeout stays registered, and fires again each time the system has been idle that long, until you remove it with `removeIdleTimeout()` or `removeAllIdleTimeouts()`. `simulateUserActivity()` resets the idle time to 0, as if the user had done something.

The full example is in `sonic-frameworks-idle-tracker/examples`; its code is licensed under the GPL-2.0-or-later. It needs `Qt6::Gui` besides `KF6::IdleTime`, because it creates a `QGuiApplication`.
