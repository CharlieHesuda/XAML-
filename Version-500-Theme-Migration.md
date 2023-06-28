# 5.0.0 Theme changes
For the 5.0.0 release the theme brushes have been renamed.
Depending on the size of the application there are several different options for handling the migration. However, ultimently you will want to eventually move your app to using the new brush names.

## Updating the brush names

From the root of the repository, there is a script `/Scripts/MigrateBrushes.ps1` which can be used to do a blind find and replace of the old brush names. This can be helpful to get you started on upgrading the brushes from the old brush names to the new ones. Some of the old brushes were split into new brushes, so you may want to consider, depending on the context if one of the other new brush names might be a more appropriate one to use.

## Using obsolete brush shim

If you would prefer to avoid updating your current references within your application, you can add the obsolete brush shim to your App.xaml. A sample of what it might look like is shown below.
```xaml
  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <materialDesign:BundledTheme BaseTheme="Inherit"
                                     ColorAdjustment="{materialDesign:ColorAdjustment}"
                                     PrimaryColor="DeepPurple"
                                     SecondaryColor="Lime" />

        <!-- NB: For anyone migrating and not wanting to update your brushes you will want this resource dictionary for old brush names -->
        <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.ObsoleteBrushes.xaml" />

        <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Defaults.xaml" />
      </ResourceDictionary.MergedDictionaries>
  </Application.Resources>
```

## Custom Theme Resource Dictionaries
For any resource dictionary stored in the App.xaml MergedDictionaries if the dictionary contains `MaterialDesign.Resources.RecreateOnThemeChange` boolean value set to true, then when the theme is changed, the resource dictionary will be remove and recreated when the theme changes.
```xaml
<system:Boolean x:Key="MaterialDesign.Resources.RecreateOnThemeChange">True</system:Boolean>
```
