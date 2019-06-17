### Localization and Spell Checking
The context menus on the text boxes support [spelling suggestions](https://docs.microsoft.com/en-us/dotnet/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control). These can be enabled with the [SpellCheck.IsEnabled](https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.spellcheck.isenabled) attached property. 
This will cause additional menu items to be included with spelling suggestions as well as options for `Ignore All`, and `(no spelling suggestions)`. Because these are coming directly from this library and not the built-in these strings are not localized. If you need to adjust them you can do the following in your App.xaml

```XAML
<Application x:Class="Button.RotatedProgress.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:md="http://materialdesigninxaml.net/winfx/xaml/themes"
             ... >
    <Application.Resources>
        <ResourceDictionary>
            ...

            <Style x:Key="{x:Static md:Spelling.IgnoreAllMenuItemStyleKey}"  TargetType="{x:Type MenuItem}" BasedOn="{StaticResource MaterialDesignMenuItem}">
                <!--Change this to whatever is appropriate to for your application-->
                <Setter Property="Header" Value="Localized Ignore All" />
            </Style>

            <Style x:Key="{x:Static md:Spelling.NoSuggestionsMenuItemStyleKey}" TargetType="{x:Type MenuItem}" BasedOn="{StaticResource MaterialDesignMenuItem}">
                <!--Change this to whatever is appropriate to for your application-->
                <Setter Property="Header" Value="Localized (no spelling suggestions)" />
                <Setter Property="IsEnabled" Value="False" />
            </Style>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```