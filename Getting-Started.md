**Material Design in XAML Toolkit** consists of Material styles for existing components and completely new components that follow the Material Design logic. This article will guide you through the steps necessary to set up Material Design in XAML Toolkit in your project.

There is also an [introductory video](https://youtu.be/-n5yeEOsbCk).

The setup of the toolkit can vary from version to version. Please note which version of the toolkit you are using.

## Installing the Toolkit

Before anything else, you must install the Toolkit. This can be done either manually or through the [NuGet package](https://www.nuget.org/packages/MaterialDesignThemes/) (```Install-Package MaterialDesignThemes```).

## Version 5.0.0 and later
If you would like to get started with a full solution template @Keboo has a solution template you can find [here](https://github.com/Keboo/DotnetTemplates). Simply install the template and run `dotnet new keboo.wpf` to get a full solution up and running.

Like any other XAML library, the Toolkit needs to be imported and configured through your project's App.xaml to function properly. All of the following changes should be done as merged dictionaries (complete sample below). First, you will need to include all of the default styles for the controls. This is required regardless of which of the three styling options you choose.

```xaml
<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesign3.Defaults.xaml" /> 
```
Or if you prefer the classic look and feel (note the version changed to 2 from 3):
```xaml
<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesign2.Defaults.xaml" /> 
```

Next, you need to select a color theme. The simplest option is to use one of the built-in themes provided by the `BundledTheme` resource dictionary.

A final App.xaml should look something like this:
```xaml
<Application x:Class="Example.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <materialDesign:BundledTheme BaseTheme="Light" PrimaryColor="DeepPurple" SecondaryColor="Lime" />
                <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesign3.Defaults.xaml" /> 
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```

If you would prefer to use your own custom colors for the theme, you can do this with the `CustomColorTheme` resource dictionary.
A final App.xaml should look something like this:
```xml
<Application x:Class="Example.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <materialDesign:CustomColorTheme BaseTheme="Light" PrimaryColor="Aqua" SecondaryColor="DarkGreen" />
                <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesign3.Defaults.xaml" /> 
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```

### Configuring your Window(s)
To properly setup all of the colors at the Window, you will need to apply a style to your Window classes.

```xml
<Window [...]
        Style="{StaticResource MaterialDesignWindow}"
        [...] >
```

Now your window's text will also blend in nicely with Material Design.

## Version 3.0.0 through 4.9.0

### Configuring your App.xaml

Like any other XAML library, the Toolkit needs to be imported and configured through your project's App.xaml to function properly. All of the following changes should be done as merged dictionaries (complete sample below). First, you will need to include all of the default styles for the controls. This is required regardless of which of the three styling options you choose.

```xml
<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Defaults.xaml" /> 
```

Next, you need to select a color theme. The simplest option is to use one of the built-in themes provided by the `BundledTheme` resource dictionary.

A final App.xaml should look something like this:
```xml
<Application x:Class="Example.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <materialDesign:BundledTheme BaseTheme="Light" PrimaryColor="DeepPurple" SecondaryColor="Lime" />
                <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Defaults.xaml" /> 
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```

If you would prefer to use your own custom colors for the theme, you can do this with the `CustomColorTheme` resource dictionary.
A final App.xaml should look something like this:
```xml
<Application x:Class="Example.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <materialDesign:CustomColorTheme BaseTheme="Light" PrimaryColor="Aqua" SecondaryColor="DarkGreen" />
                <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Defaults.xaml" /> 
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```

### Configuring your Window(s)
We're almost there! Now, all we need to do is configure our window to have Material Designs's look. There are no secrets here, you just need to add a few parameters to your Window's opening tag. The basic ones are:

```xml
<Window [...]
        TextElement.Foreground="{DynamicResource MaterialDesign.Brush.Foreground}"
        Background="{DynamicResource MaterialDesign.Brush.Background}"
        [...] >
```

These will ensure the window uses Material Design colors, blending in nicely with the Toolkit's styles and components. However, for the full Material Design experience, you should set up the font like this:

```xml
<Window [...]
        xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
        TextElement.Foreground="{DynamicResource MaterialDesign.Brush.Foreground}"
        Background="{DynamicResource MaterialDesign.Brush.Background}"
        TextElement.FontWeight="Medium"
        TextElement.FontSize="14"
        FontFamily="{materialDesign:MaterialDesignFont}"
        [...] >
```

Now your window's text will also blend in nicely with Material Design.


## Version 2.6.0 and earlier

### Configuring your App.xaml

Like any other XAML library, the Toolkit needs to be imported and configured through your project's App.xaml to function properly. All of the following changes should be done as merged dictionaries (complete sample below). First, you will need to include all of the default styles for the controls. This is required regardless of which of the three styling options you choose.

First of all, you'll need to merge one of the themes (Dark or Light) into your resource dictionary. This can be accomplished by adding the following line inside your Resource Dictionary's Merged Dictionaries:

* For the Light theme:
```xml
<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Light.xaml" />
```

* For the Dark theme:
```xml
<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Dark.xaml" />
```

Then, you'll need to load the `MaterialDesignTheme.Defaults.xaml` file, which contains all of the component styles, with the following line:

```xml
<ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Defaults.xaml" /> 
```

Your App.xaml should be looking something like this for now:
```xml
<Application x:Class="MaterialTest.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:local="clr-namespace:MaterialTest"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Light.xaml" />
                <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Defaults.xaml" />
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```

### The Colors

In Material Design, two 'palettes' need to be defined: Primary and Secondary. To make your life easier, the Toolkit includes all of [Google's swatches](https://www.google.com/design/spec/style/color.html#color-color-palette) and their recommended palettes built-in and ready to be used! They are contained in the MaterialDesignColors project, which is imported automatically as a dependency when you install the main NuGet package. 

In this section, we'll use the recommended palettes to define our application's colors, since they're the easiest way to do it and also the most common. If you'd like to learn more, see the [[Swatches and Recommended Colors]] page.

The recommended palettes live in ```/Themes/Recommended/Secondary/MaterialDesignColor.COLOR_NAME.xaml``` and ```/Themes/Recommended/Primary/MaterialDesignColor.COLOR_NAME.xaml```, inside the *MaterialDesignColors* project, where *COLOR_NAME* is the name of the color swatch as defined in [Google's guide](https://www.google.com/design/spec/style/color.html#color-color-palette), without spaces (So *Deep Purple* becomes *DeepPurple*). Please note that not all swatches have Primary and Secondary colors. So see which ones are available, consult Google's guide or the project's [Secondary](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/tree/master/src/MaterialDesignColors.Wpf/Themes/Recommended/Secondary) and [Primary](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/tree/master/src/MaterialDesignColors.Wpf/Themes/Recommended/Primary) folders.

Now, let's get to the code. Importing them is very similar to how you imported other resources earlier, just with a change to the project:

```xml
<ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/Recommended/Primary/MaterialDesignColor.COLOR_NAME.xaml" />
<ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/Recommended/Secondary/MaterialDesignColor.COLOR_NAME.xaml" />
```

So, if you wanted to use Deep Purple as your primary color and Lime as your secondary, your App.xaml would look something like this right now:

```xml
<Application x:Class="MaterialTest.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>

                <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Light.xaml" />
                <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Defaults.xaml" />
                <ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/Recommended/Primary/MaterialDesignColor.DeepPurple.xaml" />
                <ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/Recommended/Secondary/MaterialDesignColor.Lime.xaml" />

            </ResourceDictionary.MergedDictionaries>            
        </ResourceDictionary>
    </Application.Resources>
</Application>
```

### Configuring your Window(s)

We're almost there! Now, all we need to do is configure our window to have Material Designs' look. There are no secrets here, you just need to add a few parameters to your Window's opening tag. The basic ones are:

```xml
<Window [...]
        TextElement.Foreground="{DynamicResource MaterialDesign.Brush.Foreground}"
        Background="{DynamicResource MaterialDesign.Brush.Background}"
        [...] >
```

These will ensure the window uses Material Design colors, blending in nicely with the Toolkit's styles and components. However, for the full Material Design experience, you should use:

```xml
<Window [...]
        TextElement.Foreground="{DynamicResource MaterialDesign.Brush.Foreground}"
        Background="{DynamicResource MaterialDesign.Brush.Background}"
        TextElement.FontWeight="Medium"
        TextElement.FontSize="14"
        FontFamily="pack://application:,,,/MaterialDesignThemes.Wpf;component/Resources/Roboto/#Roboto"
        [...] >
```

Now your window's text will also blend in nicely with Material Design.

## Summary
To use Material Design in the XAML Toolkit, you'll need to install the package manually or through NuGet, import either the Light or Dark theme, import the Default file that contains all of the component's themes, choose Primary and Secondary colors of your preference and configure your window to use Material Design's looks.

# Using the Toolkit with MahApps
If you also want to use MahApps.Metro in your project, check out the [[MahApps.Metro integration]] page.

# Aftermath
Now that you're all set to stun your users with modern and beautiful applications, you should take a look at the [Toolkit's Demo](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/tree/master/src/MainDemo.Wpf) to learn how to properly use components and styles, or at the [Mash Up Demo](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/tree/master/src/MahMaterialDragablzMashUp) to see how to integrate Material Design, MahApps, and Dragablz for a truly modern application.