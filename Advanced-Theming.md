*The information here applies to version 2.6.0 and later.*

## Setting the initial theme

The first step is to set the inital theme. There are two recommended ways to accomplish this:
1. Use one of the built in [Markup Extensions](https://docs.microsoft.com/en-us/dotnet/framework/wpf/advanced/markup-extensions-and-wpf-xaml) that generates a theme resource dictionary. Use one of the built-in markup extenions (`BundledTheme` or `CustomColorTheme`). These return a new `ResourceDictionary` instance with all of the brushes setup for you.
2. Create a new `ITheme` object and use `ResourceDictionaryExtensions.SetTheme(Application.Current.Resources)`. You can create a new `Theme` object using:
```C#
using MaterialDesignColors;
using MaterialDesignThemes.Wpf;
using System.Windows.Media;
...
PrimaryColor primary = PrimaryColor.DeepPurple;
Color primaryColor = SwatchHelper.Lookup[(MaterialDesignColor)primary];

SecondaryColor secondary = SecondaryColor.Teal;
Color secondaryColor = SwatchHelper.Lookup[(MaterialDesignColor)secondary];

IBaseTheme baseTheme = Theme.Light;
//If you want a dark theme you can use IBaseTheme baseTheme = Theme.Dark;

ITheme theme = Theme.Create(baseTheme, primaryColor, secondaryColor);
```
If you want you can use any arbitrary colors.
```C#
using MaterialDesignThemes.Wpf;
using System.Windows.Media;
...
Color primaryColor = Colors.Purple;
Color secondaryColor = Colors.Lime;

IBaseTheme baseTheme = Theme.Light;
//If you want a dark theme you can use IBaseTheme baseTheme = Theme.Dark;

ITheme theme = Theme.Create(baseTheme, primaryColor, secondaryColor);
```

## Changing the theme
Prior to version 2.6.0 the `PaletteHelper` class provided methods for modifying the theme. These methods are now obsolete in favor of the new `GetTheme` and `SetTheme` methods on `PaletteHelper`. To change the theme simply get the existing `ITheme`, modify this theme object, and then simply set it with `PaletteHelper.SetTheme`. Similar to this:
```C#
using MaterialDesignColors;
using MaterialDesignThemes.Wpf;
...
var paletteHelper = new PaletteHelper();
//Retrieve the app's existing theme
ITheme theme = paletteHelper.GetTheme();

//Change the base theme to Dark
theme.SetBaseTheme(Theme.Dark);
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