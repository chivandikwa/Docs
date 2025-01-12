---
uid: application-development.software-factory.about-software-factory-execution
remarks: |
    # TODO

    Perhaps how to configure diff tool, or anything else we need to cover. -->
---
# About Software Factory Execution

The Software Factory Execution is the process that executes the installed [Modules](xref:application-development.applications-and-solutions.about-modules) with the metadata from the [Designers](xref:application-development.modelling.about-designers) within an [Application](xref:application-development.applications-and-solutions.about-applications). The result is changes to the codebase which are **staged** before being accepted or rejected.

![Software Factory Execution](images/software-factory-execution.gif)

Intent Architect will not make changes to your codebase without your consent. The changes will be listed and can be clicked on which launches a Diff tool for you to view the changes between the files - like a _pull request_ from your robot developer friend.

![Diff Example](images/diff-example.png)
_An example diff of changes made to a C# interface that's managed by Intent Architect._

The Software Factory Execution is initiated from within an Application by clicking on the _Play_ button in the top nav-bar. The execution is typically kicked off after completing some design changes, or installing / updating Modules.

![Play Button](images/play-button.png)
