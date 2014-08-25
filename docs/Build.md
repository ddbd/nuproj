# Checked-in Toolkit

On the build machine, you shouldn't install NuProj. Instead, you should restore
the [NuGet package that provides the build server support](http://www.nuget.org/packages/NuProj).

In order for MSBuild to find the `NuProj.targets` that NuProj files depend on
you need to override the `NuProjTargetsPath` property:

```xml
<PropertyGroup>
    <MyNuProjPath>$(MyCheckinRoot)packages\NuProj.0.9.2\tools\</MyNuProjPath>
    <NuProjTargetsPath>$(MyNuProjPath)NuProj.targets</NuProjTargetsPath>
    <!--
    <NuProjTasksPath>$(MyNuProjPath)NuProj.Tasks.dll</NuProjTasksPath>
    <NuGetToolPath>$(MyNuProjPath)</NuGetToolPath>
    <NuGetToolExe>NuGet.exe</NuGetToolExe>
    -->
</PropertyGroup>
```

Optionally, you can also chose a different layout and override the other
properties as well.