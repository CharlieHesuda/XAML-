## Fonts (v3.0.0 and later)

In versions prior to 3.0.0 the only wany to reference the bundled Roboto font was as a packd resource using: 
```xml
FontFamily="pack://application:,,,/MaterialDesignThemes.Wpf;component/Resources/Roboto/#Roboto"
```
With version 3.0.0 this has been greatly simplified using the new `MaterialDesignFont` markup extension. Now you can simply reference the font using:
```xml
xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
[...]
FontFamily="{materialDesign:MaterialDesignFont}" 
```

## Include font files (v3.0.0 and later)
If you would prefer to have the Roboto font files included in your project rather than just as an embedded resources inside of the material design library you can add a new property to your project.

First edit your csproj file and add place the following ***inside*** of the `<Project>` element.
```xml
<PropertyGroup>
  <IncludeMaterialDesignFont>True</IncludeMaterialDesignFont>
  <MaterialDesignFontDirectory>Resources\Roboto\</MaterialDesignFontDirectory>
</PropertyGroup>
```

Then rebuild your project. In your output directory, you will see the font font show up under a Resources\Roboto directory. Depending on which version of the csproj you are using, you may also see the files show up in the folder inside of your solution explorer.