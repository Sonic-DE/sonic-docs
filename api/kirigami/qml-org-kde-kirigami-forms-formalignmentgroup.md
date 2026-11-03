---
title: "FormAlignmentGroup QML Type"
description: "A group of forms that should be perfectly aligned with each other."
---

# FormAlignmentGroup QML Type

A group of forms that should be perfectly aligned with each other. [More...](#details)

- Import Statement: import org.kde.kirigami.forms

## Detailed Description {#details}

Sometimes for implementation reasons there must be multiple Form instances in the same encompassing layout. when the forms are not in collapsed mode, their tiles and contents need to be perfectly aligned with each other, therefore while doing its layout, a form must know about all the other forms in the group, so they can synchronize their size hints with each other.

Use a [FormAlignmentGroup](qml-org-kde-kirigami-forms-formalignmentgroup.md) instance and its attached property to add every form in the same group

Example usage:

```qml
FormAlignGroup {
    id: formGroup
}

Form {
    FormAlignGroup.group: formGroup
    ...
}

Form {
    FormAlignGroup.group: formGroup
    ...
}
```

*See also* [Form](qml-org-kde-kirigami-forms-form.md)

## Property Documentation {#property-documentation}

### forms : list\<Item\> {#forms-prop}

All the forms in this group.

## Attached Property Documentation {#attached-property-documentation}

### FormAlignmentGroup.group : FormAlignmentGroup {#group-attached-prop}

The group this form belongs to. The attached property makes sense to be used only inside a Form
