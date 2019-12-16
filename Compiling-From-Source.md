# Compiling From Source

The NuGet package are backwards compatibile and can be used in any WPF application (targetting .NET 4.5 or later) with any version of Visual Studio. If you wish to **compile the library from source it will REQUIRE Visual Studio 2019 (v16.3 or later) with .NET Core 3.0 installed**. This is because the source code leverages the latest features, such as expression bodied members, which cannot be compiled in earlier versions of Visual Studio. 
  
The main project is contained within the `MaterialDesignToolkit.Wpf.sln` file located at the root of the repository. This is the file you want to open in Visual Studio.  
  
Set the startup project to be `Demos\MaterialDesignDemo`, compile and run (or simply press F5).  
  
The first time you compile the project you will likely get the error `ShowMeTheXAML was added to the MaterialDesignDemo project. Please rebuild the project.`. This is expected and should only occur the very first time you compile the library. Simply re-build the solution (from the top menu Build>>Rebuild Solution). You must **rebuild**, not just a normal incremental build. If you continue to get this error, you may need to restart Visual Studio. For more details see [this comment](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/issues/1187#issuecomment-462640254).
  
This library uses [paket](https://fsprojects.github.io/Paket/) to install its dependencies. Typically these should be downloaded automatically for you when you first compile the solution.

