---
uid: release-notes.version-3-3
---
# Release notes: Intent Architect version 3.3

_Will be released between 2022/04/18 and 2202/04/25_

## Version 3.3.0

### New features added in 3.3.0

- [Additional Application Template options](#additional-application-template-options).
- [Repository management enhancements](#repository-management-enhancements)
- [Code management statistics](#code-management-statistics)
- Intent Architect upgraded to internally run using .NET 6. This allows the Software Factory to now support modules which are compiled to targetting any framework supported by .NET 6.
- Elements now allow specifying a custom validation function. This allows Designer authors to specify additional validation rules for their element types which make elements in the tree view highlight in red when any validation fails.
- It is now possible to have metadata file names also include the element name. This makes it easier in pull requests to quickly see which metadata has been changed.
- When a module is re-installed, unassigned `Template Output` elements will now be removed and re-added to Designers. This means that if a template did not initially have a Role in the Template Builder and one was applied later, on re-install of the module, the `Template Output` will be "moved" to the correct place.

### Issues fixed in 3.3.0

- Fixed: It was not possible to select multiple mapped members with the same name in the mapping dialogue.
- Fixed: `ApplicationEvent` was not triggering handlers subscribed to them by event type and would only work by `EventIdentifier`. Both methods of subscribing now work.
- Fixed: Intent Architect would automatically upgrade modules to the "highest available version" of when a specific version could not be restored which could result in incompatible modules being installed. Intent will now just show an error that the module could not be restored.

### Additional Application template options

- It is now possible to specify between allowing selection "Multiple" or "Single Only" components within a component group.

![Control selection of components within a component group](images/3.3.0/application-templates-control-component-selection.png)

- It is now possible to specify dependencies between components. When selecting the checkbox of a component which has dependencies, all the dependencies checkboxes are also automatically selected. When deselecting a checkbox, any other components which are dependent on it are also automatically deselected.

- It is now possible to make a component "Is Required". When a component "Is Required", then it cannot be deselected.

![Specify component dependencies and is required](images/3.3.0/application-templates-component-dependencies-and-is-required.png)

- It is now possible to specify settings for an application template which can be used to set different values during [metadata installation](xref:modules.metadata-installation).

![Specify application template settings](images/3.3.0/application-templates-settings-define.png)

![Application template with settings](images/3.3.0/application-templates-settings-preview.png)

### Repository management enhancements

The `Asset Repository` dialogue available when pressing the "cog" icon from the Modules screens has been updated.

![Repository management enhancements](images/3.3.0/repository-management-enhancements.png)

1. The number of modules in the repository (file system based repositories only).
2. Launches your operating system's file browser which you can use to select the path.
3. Can be used to specify if the repository is:
   - Global: Saved to the user's computer and available to all Solutions and Applications.
   - Current Solution: Saved in the same folder as the Intent Architect Solution and is available to the Solution and any Applications within it.
   - Current Application: Saved in the same folder as the current Intent Architect Application and is only available to the Application.

   When changed, it will automatically update the `Address` to/from being fully qualified or update its relative location accordingly.
4. The link can be clicked on to open the location in your operating system's file browser.

### Code management statistics

The Software Factory Execution Changes dialogue now shows statistics on the number of lines and files being managed and affected by the current execution:

![Code management statistics](images/3.3.0/code-management-statistics.png)