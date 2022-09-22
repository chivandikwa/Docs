---
uid: application-development.code-weaving-and-generation.about-template-output-targeting
---
# About Template Output Targeting

## Overview

`Output Targeting` refers to how Intent Architect determines where a Template's output should be placed on the file system during the software execution through configuration within designers and the template itself.

Some designers (such as the `Folders` and `Visual Studio` designers) support "Output Configuration" which lets Intent Architect know during module installation that `Template Output`s should be placed in it. The Software Factory Execution uses these `Template Outputs` to determine the output paths for template instances.

![Output Config Template Output](images/output-config-template-output-side-by-side.png)
_Example features both a Folder (left) and Visual Studio (right) designer layout with Template Output items highlighted_

## Template Outputs

`Template Output`s in the designers are used by the Software Factory to know where on the file system that template output should be written, in particular under which sub-folder. As modules are installed, for each template within them, a `Template Output` is automatically created with its name being the value of the `TemplateId` property of the template as specified during module building.

## Unassigned Template Output

Some designers (such as the Visual Studio designer) will show unassigned Template Outputs in red:

![Unassigned Template in Output Configuration Designer](images/output-config-vs-unassigned-template.png)

Running the the Software Factory while these template are unassigned will result in errors during the execution about there being unassigned templates.

Templates can specify where their "Template Output" should be placed by default during module installation so that things work automatically, this is covered in the next section.

## Roles and Default Locations

Templates in the module builder can have their `Role` and `Default Location` configured. These are used by Intent Architect during module installation to determine where the template's `Template Output` should be placed.

![Module Builder Template Role Specification](images/module-builder-template-role-specification.png)

As part of the module installation Intent Architect will search "Output Configuration" designers for a `Role` element with a name matching the `Role` value captured in the Module Builder.

If a `Role` with a matching name is found, then Intent Architect will then add any additional sub-folders specified in the `Default Location` as needed and finally place the new `Template Output` for the template within the correct sub-folder as specified by the template's `Default Location`. If `Default Location` was blank, then the `Template Output` is placed in the same folder as the `Role`.

If no `Role` with a matching name was found then the `Template Output` is placed in the "root" folder of the designer.

The following example depicts a Template created in the Module Builder and installed in a target Application.

![Module Builder Template Settings Relative Location Example](images/module-builder-template-settings-example-relative-location.png)

The `Role` is set to `Distribution` and `Default Location` is set to `Controllers`.

![Output Configuration Relative Location Example](images/output-config-example-relative-location.png)

In the example above the `Distribution` `Role` can be identified by the blue badge icon and at the same tree depth is the `Controllers` Folder.

Once that Module is installed, it will create the `Template Output` named `Intent.AspNetCore.Controllers.Controller` where the `Role` named `Distribution` is located but in a folder location relative to the `Role` which is `Controllers`.

> [!NOTE]
> Re-installing a Module may cause unassigned Template Outputs to be relocated, however assigned Template Outputs will remain untouched. This will allow you as a user to customize the output layout as you need it to be.