*The information here applies to version 5.0.0 and later.*

## Setting the initial theme

The first step is to set the initial theme. There are two recommended ways to accomplish this:
1. Use one of the built in [Markup Extensions](https://docs.microsoft.com/en-us/dotnet/framework/wpf/advanced/markup-extensions-and-wpf-xaml) that generates a theme resource dictionary. Use one of the built-in markup extensions (`BundledTheme` or `CustomColorTheme`). These return a new `ResourceDictionary` instance with all of the brushes setup for you.
2. Create a new `Theme` object and use `ResourceDictionaryExtensions.SetTheme(Application.Current.Resources)`. You can create a new `Theme` object using:
```C#
using MaterialDesignColors;
using MaterialDesignThemes.Wpf;
using System.Windows.Media;
...
Theme theme = new();
PrimaryColor primary = PrimaryColor.DeepPurple;
Color primaryColor = SwatchHelper.Lookup[(MaterialDesignColor)primary];
theme.SetPrimaryColor(primaryColor);

SecondaryColor secondary = SecondaryColor.Teal;
Color secondaryColor = SwatchHelper.Lookup[(MaterialDesignColor)secondary];
theme.SetSecondaryColor(secondaryColor);

theme.SetLightTheme();
//If you want a dark theme you can use theme.SetDarkTheme(); or theme.SetBaseTheme()
```
If you want you can use any arbitrary colors.
```C#
Theme theme = new();
Color primaryColor = Colors.Purple;
theme.SetPrimaryColor(primaryColor);

Color secondaryColor = Colors.Lime;
theme.SetSecondaryColor(secondaryColor);

theme.SetLightTheme();
//If you want a dark theme you can use theme.SetDarkTheme(); or theme.SetBaseTheme()
```

## Changing the theme
To change the theme simply get or create a `Theme` instance, modify this theme instance, and then apply it with `PaletteHelper.SetTheme`. Similar to this:
```C#
using MaterialDesignColors;
using MaterialDesignThemes.Wpf;
...
var paletteHelper = new PaletteHelper();
//Retrieve the app's existing theme
Theme theme = paletteHelper.GetTheme();

//Change the base theme to Dark
theme.SetBaseTheme(BaseTheme.Dark);
//or theme.SetBaseTheme(Theme.Light);

//Change all of the primary colors to Red
theme.SetPrimaryColor(Colors.Red);

//Change all of the secondary colors to Blue
theme.SetSecondaryColor(Colors.Blue);

//You can also change a single color on the theme, and optionally set the corresponding foreground color
theme.PrimaryMid = new ColorPair(Colors.Brown, Colors.White);

//Change the app's current theme
paletteHelper.SetTheme(theme);
```