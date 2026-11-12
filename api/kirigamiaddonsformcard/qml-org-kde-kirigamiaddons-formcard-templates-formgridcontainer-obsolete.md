---
title: "Obsolete Members for FormGridContainer"
description: "Deprecated members of FormGridContainer QML Type."
parent: "kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-templates-formgridcontainer"
---

# Obsolete Members for FormGridContainer

**The following members of QML type [FormGridContainer](qml-org-kde-kirigamiaddons-formcard-templates-formgridcontainer.md) are deprecated.** We strongly advise against using them in new code.

## Properties

- [\[deprecated\] infoCards : list\<QtObject\>](#infoCards-prop)

## Obsolete Property Documentation {#obsolete-property-documentation}

### \[deprecated\] infoCards : list\<QtObject\> {#infoCards-prop}

This property is deprecated. We strongly advise against using it in new code.

This property holds the InfoCards which should be displayed.

Each InfoCard contains a title and an optional subtitle

```qml
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormGridContainer {
    infoCards: [
        FormCard.FormGridContainer.InfoCard {
            title: "42"
            subtitle: i18nc("@info:Number of Posts", "Posts")
        },
        FormCard.FormGridContainer.InfoCard {
            title: "42"
        },
        FormCard.FormGridContainer.InfoCard {
            title: "Details"
            action: Kirigami.Action {
                onClicked: pageStack.push("Details.qml")
            }
        }
    ]
}
```

Use direct form delegates instead.
