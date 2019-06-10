# Frequently Asked Questions
For control specific questions look at the corresponding pages under the Controls section in the sidebar.
  
### Exception: Cannot find resource named 'MaterialDesign...'
This error typically comes when you have a static resource referencing one of the material design styles, and have not included the appropriate resource dictionary that contains the style. Try the following:
 - Ensure that you have loaded all of the default material design styles in your App.xaml. You can find directions for this in the [Getting Started guide](Getting-Started).
 - Ensure you have referenced the control specific resource dictionary that contains the style. The path for this is resource dictionary should be `<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.<Control Name Here>.xaml" />`. For example, if you were trying to reference the `MaterialDesignFloatingActionMiniButton` style for a button, the resource dictionary source would be: `<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Button.xaml" />`. Typically these inclusions are done at root of your Window, User Control, or Template. You can find the full list of the resource dictionaries [here](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/tree/master/MaterialDesignThemes.Wpf/Themes)

### Project fails to build with error: The command ""...\MaterialDesignInXamlToolkit\.paket\paket.exe" restore --references-file "...\MaterialDesignInXamlToolkit\MainDemo.Wpf\paket.references"" exited with code 1.
This error typically occurs when changing branches or occasionally on the initial build. Simply restart Visual Studio and rebuild the project.

### When apply a style, the Material Design theme is lost.
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
