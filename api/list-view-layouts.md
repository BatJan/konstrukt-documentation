---
description: Configuring list view layouts in Konstrukt, the back office UI builder for Umbraco.
---

# List View Layouts

List view layouts allow you to provide custom angular views to be used by the list view UI. By default there are two build in layouts, `KonstruktTableListViewLayout` which displays results in a tabular layout and `KonstruktGridListViewLayout` which displays results in a tiled grid layout.

## Defining a list view layout

To define a list view layout you create a class that inherits from the base class `KonstruktListViewLayout` and implements the abstract configuration properties.

````csharp
// Example
public class MyCustomListViewLayout : KonstruktListViewLayout
{
    public KonstruktGridListViewLayout()
    {
        Name = "My Custom List";
        Alias = "my-custom-list";
        Icon = "icon-list";
        View = "/app_plugins/myplugin/views/mycustomlist.htm";
    }
}
````

The required configuration options are:

* **Name:** The name of the layout.
* **Alias:** A unique alias for the layout.
* **Icon:** An icon to display in the list view layouts dropdown.
* **View:** The path of the angular view to load by the list view.

As well as defining the list view layout class you will also need to implement the relevant angular view and controller. This is a little out of scope for the Konstrukt documentation, however in summary you will want to:

* Create a plugin folder in the root `App_Plugin` folder.
* Create a `package.manifest` file in your plugin folder.
* Create a html view to be loaded.
* Create an angular controller to control the view.
* Hook up the controller with the view using the `ng-controller` attribute.
* Add the controller js file path to the `package.manifest`.
* Build your custom logic.

## Changing the list view layout of a list view

A list view layout is assigned to a list view as part of the list view configuration. See [List View API Documentation](collection-list-views.md#changing-the-list-view-layout) for more info.
