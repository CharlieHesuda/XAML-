- Start new WPF project
- Install _MaterialDesignThemes_ nuget: ``` Install-Package MaterialDesignThemes ```
- Edit App.xaml to following:

```
<Application . . .
    xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes">
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

- Edit MainWindow.xaml to the following:

```
<Window . . .
        xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
        TextElement.Foreground="{DynamicResource MaterialDesignBody}"
        TextElement.FontWeight="Regular"
        TextElement.FontSize="13"
        TextOptions.TextFormattingMode="Ideal" 
        TextOptions.TextRenderingMode="Auto"        
        Background="{DynamicResource MaterialDesignPaper}"
        FontFamily="{DynamicResource MaterialDesignFont}">
    <Grid>
        <StackPanel>
            <materialDesign:Card Padding="32" Margin="16">
                <TextBlock Style="{DynamicResource MaterialDesignHeadline6TextBlock}">My First Material Design App</TextBlock>
            </materialDesign:Card>
        </StackPanel>
    </Grid>
</Window>
```
- Hit F5, voila!

![](https://raw.githubusercontent.com/ButchersBoy/MaterialDesignInXamlToolkit/master/web/images/wikiscreen-quickstart.png)

