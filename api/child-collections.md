---
description: Configuring child collections in Konstrukt, the back office UI builder for Umbraco.
---

# Child Collections

A child collection is a container for a given data model that is tied to a parent collection data model. It shares all of the [Collections](collections.md) config builder API except child collections cannot contain further child collections.

{% hint style="info" %}
**Child Collections UI:** By default, child collections will be presented in the UI as context apps in the parent models editor view. If you have multiple child collections that make the context apps area over populated, you can use the [Child Collection Groups API](child-collection-groups.md) to group child collections under a single context app with the inner child collections then being presented in tabs.
{% endhint %}

## Defining a child collection

You define a child collection by calling one of the `AddChildCollection` methods on a given [`Collection`](collections.md) config builder instance.

#### **AddChildCollection&lt;TChildEntityType&gt;(Lambda idFieldExpression, Lambda fkFieldExpression, string nameSingular, string namePlural, string description, Lambda childCollectionConfig = null) : KonstruktChildCollectionConfigBuilder&lt;TEntityType&gt;**

Adds a child collection to the current collection with the given names and description and default icons. A property accessor expression is required for both the entity ID field and FK (Foreign Key) field of the entity. 

```csharp
// Example
collectionConfig.AddChildCollection<Child>(c => c.Id, c => c.ParentId, "Child", "Children", "A collection of children", childCollectionConfig => {
    ...
});
```

#### **AddChildCollection&lt;TChildEntityType&gt;(Lambda idFieldExpression, Lambda fkFieldExpression, string nameSingular, string namePlural, string description, string iconSingular, string iconPlural, Lambda childCollectionConfig = null) : KonstruktChildCollectionConfigBuilder&lt;TEntityType&gt;**

Adds a child collection to the current collection with the given names, description and icons. A property accessor expression is required for both the entity ID field and FK (Foreign Key) field of the entity. 

```csharp
// Example
collectionConfig.AddChildCollection<Child>(c => c.Id, c => c.ParentId, "Child", "Children", "A collection of children", "icon-umb-users", "icon-umb-users", childCollectionConfig => {
    ...
});
```

## Configuring a child collection

Child collections share the same API as the `Collection` config builder API, except child collections cannot contain further child collections. Please see the [Collections API documentation](collections.md) for more info.