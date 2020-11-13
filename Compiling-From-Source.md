# Compiling From Source

The NuGet package are backwards compatible and can be used in any WPF application (targeting .NET Framework 4.5.2 or later) with any version of Visual Studio. If you wish to **compile the library from source it will REQUIRE Visual Studio 2019 (v16.8 or later; C# 9 compiler is required) with .NET 5.0.100 SDK or later installed**. This is because the source code leverages the latest features, such as expression bodied members, which cannot be compiled in earlier versions of Visual Studio. You will need to ensure that you have enabled the .NET desktop development workflow from the Visual Studio Installer.

The main project is contained within the `MaterialDesignToolkit.Wpf.slnf` file located at the root of the repository. This is the file you want to open in Visual Studio.  

Launch Visual Studio and set the startup project to be `Demos\MaterialDesignDemo`, compile and run (or simply press F5).  



