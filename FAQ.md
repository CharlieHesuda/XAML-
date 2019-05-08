# Frequently Asked Questions
For control specific questions look at the corresponding pages under the Controls section in the sidebar.
  
### Exception: Cannot find resource named 'MaterialDesign...'
This error typically comes when you have a static resource referencing one of the material design styles, and have not included the appropriate resource dictionary that contains the style. Try the following:
 - Ensure that you have loaded all of the default material design styles in your App.xaml. You can find directions for this in the [Getting Started guide](Getting-Started).
 - Ensure you have referenced the control specific resource dictionary that contains the style. The path for this is resource dictionary should be `<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.<Control Name Here>.xaml" />`. For example, if you were trying to reference the `MaterialDesignFloatingActionMiniButton` style for a button, the resource dictionary source would be: `<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Button.xaml" />`. Typically these inclusions are done at root of your Window, User Control, or Template. You can find the full list of the resource dictionaries [here](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/tree/master/MaterialDesignThemes.Wpf/Themes)

### Project fails to build with error: The command ""...\MaterialDesignInXamlToolkit\.paket\paket.exe" restore --references-file "...\MaterialDesignInXamlToolkit\MainDemo.Wpf\paket.references"" exited with code 1.
This error typically occurs when changing branches or occasionally on the initial build. Simply restart Visual Studio and rebuild the project.			
