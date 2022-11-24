# Compiling From Source

The NuGet package are backwards compatible and can be used in any WPF application (targeting .NET Framework 4.5.2 or later) with any version of Visual Studio. If you wish to **compile the library from source it will REQUIRE Visual Studio 2022 (version 17.4 or later; C# 11 compiler is required) with .NET 7.0.100 SDK or later installed**. You will need to ensure that you have enabled the .NET desktop development workflow from the Visual Studio Installer. Finally, due to the various projects in the main solution you will need to ensure that you have the .NET Framework 4.5.2 and 4.7.2 SDKs installed. The easiest way to do this is to open the Visual Studio Installer and select Modify. From there select the "Individual components" tab at the top and select the ".NET Framework 4.5.2 targeting pack" and the ".NET Framework 4.7.2 targeting pack".


The main project is contained within the `MaterialDesignToolkit.Wpf.slnf` file located at the root of the repository. This is the file you want to open in Visual Studio.  

Launch Visual Studio and set the startup project to be `Demos\MaterialDesignDemo`, compile and run (or simply press F5).  



