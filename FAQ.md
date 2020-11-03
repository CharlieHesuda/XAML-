# Frequently Asked Questions
For control specific questions look at the corresponding pages under the Controls section in the sidebar.
  
### Exception: Cannot find resource named 'MaterialDesign...'
This error typically comes when you have a static resource referencing one of the material design styles, and have not included the appropriate resource dictionary that contains the style. Try the following:
 - Ensure that you have loaded all of the default material design styles in your App.xaml. You can find directions for this in the [Getting Started guide](Getting-Started).
 - Ensure you have referenced the control specific resource dictionary that contains the style. The path for this is resource dictionary should be `<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.<Control Name Here>.xaml" />`. For example, if you were trying to reference the `MaterialDesignFloatingActionMiniButton` style for a button, the resource dictionary source would be: `<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Button.xaml" />`. Typically these inclusions are done at root of your Window, User Control, or Template. You can find the full list of the resource dictionaries [here](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/tree/master/MaterialDesignThemes.Wpf/Themes)

### Project fails to build with error: The command ""...\MaterialDesignInXamlToolkit\.paket\paket.exe" restore --references-file "...\MaterialDesignInXamlToolkit\MainDemo.Wpf\paket.references"" exited with code 1.
This error typically occurs when changing branches or occasionally on the initial build. Simply restart Visual Studio and rebuild the project.

This can also occur if your project has been cloned at too deep of a path. Try moving the repository closer to the root (typically C:\\) and try again.

### When custom style is applied, the Material Design theme is lost.
This occurs when you replace a style rather than extending from it. In the same way that [C# classes can inherit from another class](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/inheritance) a WPF Style can also [extend another Style](https://docs.microsoft.com/en-us/dotnet/framework/wpf/controls/styling-and-templating#extending-styles). In many cases, if you are not explicitly setting the style, you can simply use the default style for the control as the base. For example, this creates a new style for `Button` that extends the default style being applied to `Buttons`.
```xaml
<Style TargetType="Button" BasedOn="{StaticResource {x:Type Button}}">
<!-- Your setters and triggers here -->
</Style>
```
You can also specify an explicit style to derive from. For example, this style extends the existing `MaterialDesignFlatButton` style. This also requires that you have [included the appropriate resource dictionary](#exception-cannot-find-resource-named-materialdesign) that contains the style you want to reference. 

```xaml
<!--Ensure you have referenced pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Button.xaml-->

<Style TargetType="Button" BasedOn="{StaticResource MaterialDesignFlatButton}">
<!-- Your setters and triggers here -->
</Style>
```

### "***ValidationRule" does not exist in the namespace "clr-namespace:MaterialDesignDemo.Domain"
This error occurs when you have copied some of the example [Binding validation rules](https://docs.microsoft.com/en-us/dotnet/framework/wpf/data/how-to-implement-binding-validation) that [exist in the demo app](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/tree/master/MainDemo.Wpf/Domain). These validators are merely one simple way of doing data validation in WPF. These validators are part of the demo app and not part of the Material Design in XAML library. If you would like to use them in your app, you are welcome to copy the code into your project and adjust the namespace to match.

### XamlDisplay control issues
You should not need this control inside of your application. This control was designed to make it easy for people to be able to see the corresponding XAML at run-time inside of the demo application. So when you copy the code out of the demo application, you can omit this control. 

### How can I set the *Assist.SomeProperty in code?
In WPF there exists the concept of an [Attached Property](https://docs.microsoft.com/en-us/dotnet/framework/wpf/advanced/attached-properties-overview). These properties can be specified on _any_ object. Common ones you have likely uses are `DockPanel.Dock`, `Grid.Row`, or `Grid.Column`. To see these in C# code you simply invoke them as static methods. For example if you want to set `materialDesign:ShadowAssist.ShadowDepth="Depth1"` in C# you should do:
```C#
FrameworkElement myControl = ...;
ShadowAssist.SetShadowDepth(myControl, ShadowDepth.Depth1);
```

### When Using MahApps, attempting to reference PopupEx has the error "The type 'PopupEx' exists in both 'MaterialDesignThemes.Wpf' and 'ControlzEx`".
This occurs because we include the same PopupEx code file in the MaterialDesginTemes.Wpf project that is also included in ControlzEx (which is referenced by MahApps). In most cases, types can be identified by simply specifying their full type name (namespace and type name), however in this case those match, and the types must be delimited by their assembly. In C# this is done using the [extern alias](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/extern-alias). This allows you to give an alias to one of the assemblies so that you can specify which class you intend to use. Though support for applying `extern alias` is coming soon to NuGet [see issue 4989](https://github.com/NuGet/Home/issues/4989), at present the simplest solution is to include an MSBuild target that will apply the alias to one of the assemblies. This target can be included anywhere inside of the `<Project>` element of your `.csproj` file.
```xml
<Target Name="ChangeAliasesOfNugetRefs" BeforeTargets="FindReferenceAssembliesForReferences;ResolveReferences">
  <ItemGroup>
    <ReferencePath Condition="'%(FileName)' == 'ControlzEx'">
      <Aliases>controlzEx</Aliases>
    </ReferencePath>
  </ItemGroup>
</Target>
```
Then in your C# files:
```c#
//extern alias must come before any using statements
extern alias controlzEx;
...
//A reference to the PopupEx class inside of ControlzEx
controlzEx::ControlzEx.PopupEx popup = ...
            
//Because no alias is specified on MaterialDesignThemes this reference now refers to the type in that assembly
ControlzEx.PopupEx popup2 = ...
```
Or in XAML
```xaml
xmlns:mdix="clr-namespace:ControlzEx;assembly=MaterialDesignThemes.Wpf"
xmlns:controlzEx="clr-namespace:ControlzEx;assembly=ControlzEx"
...
<mdix:PopupEx />
<controlzEx:PopupEx />
```

### When attaching routed command (such as `DialogHost.OpenDialogCommand`) my button shows as disabled.
This is normal WPF commanding behavior. When you attached a command to a button, the command can indicate if it is able to execute. If it is not able to be executed, the button is then disabled. Within WPF there are two common types of commands that get used. 
1. The first type is a simple `ICommand` implementation that is provided via a view model (or similar). These command often simply invoke a method when they are executed. Though WPF does not provide a native implementation for this, many popular MVVM libraries do have some implementation of the `ICommand` interface that is designed to make method invocation simple.
2. Routed commands, are setup to explicitly cause a separation between the element invoking the command, and the element handling the execution of the command. When a routed command is invoked, WPF looks up through the visual tree (starting with element that invoked the command) for an element that can handle the command. If no handler is found, then the command will cause the button to be disabled. In the case with the `DialogHost.OpenDialogCommand` this often occurs because no `DialogHost` instance is found in the visual tree. You can also specify and alternate command target to use to find the handler for the RoutedCommand by using the [CommandTarget property](https://docs.microsoft.com/dotnet/api/system.windows.input.inputbinding.commandtarget?view=netcore-3.1).

You can find more information in the [docs](https://docs.microsoft.com/en-us/dotnet/desktop/wpf/advanced/commanding-overview?view=netframeworkdesktop-4.8)