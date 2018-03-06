# Introduction 
This is a fork of the [NuProj GitHub Repository](https://github.com/nuproj/nuproj) with the required changes to install the Nuget Project Template Visual Studio Extension to Visual Studio 2017.

## Issue Description
The Visual Studio Extension is required to add the Nuget Project Template. This extension is not compatible with Visual Studio 2017 and .Net 4.6.1:
```System.IO.FileNotFoundException: Could not load file or assembly 'NuGet.Frameworks, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies.```
But it is with Visual Studio 2015.


# Getting Started
This is a copy of the described changes from [Issue 297 of GitHub](https://github.com/nuproj/nuproj/issues/297).

- open src/NuProj.sln with Visual Studio 2017
- remove projects NuProj.ProjectSystem.12, NuProj.ProjectSystem.14 and NuProj.Setup
- build the project
- right-click on NuProj.ProjectSystem.15 and add a new folder called NuProj
- right-click on the NuProj folder and add (use Add as Link!! the little arrow on the Add button in the dialog) existing items from the bin/Debug folder of the NuProj.Tasks project:
  - NuGet.Frameworks.dll
  - NuGet.Packaging.dll
  - NuGet.Packaging.Core.dll
  - NuGet.Packaging.Core.Types.dll
  - NuGet.Versioning.dll
- select the five files and change:
  - Install Root to MSBuild
  - Include in VSIX to True
- open Solution items -> version.json and change version from what it is (ex: 0.20-beta) to something larger (0.26) - optional, but it will stop saying you need to update and if you have your local nuget server it will tell you to update the one you have
- rebuild (not just build) solution
- The resulting .vsix file (src\NuProj.ProjectSystem.15\bin\Debug\NuProj.ProjectSystem.15.vsix) is the extension that allows using .nuproj in VS2017