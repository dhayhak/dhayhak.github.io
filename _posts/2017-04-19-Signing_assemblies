---
layout: post
title: You Have been Signing .NET Assemblies wrong!
---

## Don't hard code you Signing Key file Path

For a long time, if I want to sign an assembly I'll put this line into the `AssemblyInfo.cs` file
`[assembly: AssemblyKeyFile(@"<PATH_TO_FILE>\file.snk")]`

This is fine until we want to automate the build on a build Server which could have a deferent path.
The build will fail!


### The right Way
1. Remove that line from AssemblyInfo.
1. Change the project file to add these propertyGroup:
  1. Add `<keyFilePath><PATH_TO_FILE>\file.snk</keyFilePath>`.
  1. Add this code to the project file
   
   ```
         <PropertyGroup>
            <SignAssembly>true</SignAssembly>
         </PropertyGroup>
         <PropertyGroup>
            <AssemblyOriginatorKeyFile>$(keyFilePath)</AssemblyOriginatorKeyFile>
         </PropertyGroup>
     ```
1. Now you can build your project by providing `/p:keyFilePath="%KEY_FILE_PATH%"` to MsBuild
