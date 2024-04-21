Illustration of advanced configuration of App.xaml which allows individual palette hues to be specified.

```xml
<Application x:Class="MaterialDesignColors.WpfExample.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:dragablz="clr-namespace:Dragablz;assembly=Dragablz"
             StartupUri="MainWindow.xaml">
  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <!-- Set your base theme -->
        <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Light.xaml" />
        <!-- primary color -->
        <ResourceDictionary>
          <!-- include your primary palette -->
          <ResourceDictionary.MergedDictionaries>
            <ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/MaterialDesignColor.Indigo.Primary.xaml" />
          </ResourceDictionary.MergedDictionaries>
          
          <SolidColorBrush x:Key="MaterialDesign.Brush.Primary.Light" Color="{StaticResource Primary200}"/>
          <SolidColorBrush x:Key="MaterialDesign.Brush.Primary.Light.Foreground" Color="{StaticResource Primary200Foreground}"/>
          <SolidColorBrush x:Key="MaterialDesign.Brush.Primary" Color="{StaticResource Primary500}"/>
          <SolidColorBrush x:Key="MaterialDesign.Brush.Primary.Foreground" Color="{StaticResource Primary500Foreground}"/>
          <SolidColorBrush x:Key="MaterialDesign.Brush.Primary.Dark" Color="{StaticResource Primary700}"/>
          <SolidColorBrush x:Key="MaterialDesign.Brush.Primary.Dark.Foreground" Color="{StaticResource Primary700Foreground}"/>
        </ResourceDictionary>

        <!-- secondary colour -->
        <ResourceDictionary>
          <!-- include your secondary pallette -->
          <ResourceDictionary.MergedDictionaries>
            <ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/MaterialDesignColor.Yellow.Secondary.xaml" />
          </ResourceDictionary.MergedDictionaries>

          <SolidColorBrush x:Key="MaterialDesign.Brush.Secondary.Light" Color="{StaticResource Secondary200}" />
          <SolidColorBrush x:Key="MaterialDesign.Brush.Secondary.Light.Foreground" Color="{StaticResource Secondary200Foreground}" />
          <SolidColorBrush x:Key="MaterialDesign.Brush.Secondary" Color="{StaticResource Secondary400}" />
          <SolidColorBrush x:Key="MaterialDesign.Brush.Secondary.Foreground" Color="{StaticResource Secondary400Foreground}" />
          <SolidColorBrush x:Key="MaterialDesign.Brush.Secondary.Dark" Color="{StaticResource Secondary700}" />
          <SolidColorBrush x:Key="MaterialDesign.Brush.Secondary.Dark.Foreground" Color="{StaticResource Secondary700Foreground}" />
        </ResourceDictionary>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

