Material Design XAML Toolkit comes with Font-awesome icons builted-in and they are very easy to use.

Just create a `PackIcon` and set its `Kind` property to whatever icon you want to use. (All icons type are stored in the `PackIconKind` enum.)

> For an overview of all available icons go to the [material design icons website](https://materialdesignicons.com/) or download the [compiled sample project](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/releases/latest)

**You can use XAML**

```xaml
<materialDesign:PackIcon Kind="SmileyHappy"/>
```
Here you'll need to add a namespace reference to your window like this

```xaml
xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
```

**or you can use Code-Behind**

```cs
var icon = new PackIcon { Kind = PackIconKind.SmileyHappy };
```
Here you'll need to add a namespace reference like this

```cs
using MaterialDesignThemes.Wpf;
```

***

You can change the icon's colour by setting the `Foreground` property to the desired colour.

**XAML**
```xaml
<materialDesign:PackIcon Kind="SmileyHappy" Foreground="Red"/>
```

**Code-Behind**
```cs
var icon = new PackIcon { Kind = PackIconKind.SmileyHappy, Foreground = System.Windows.Media.Brushes.Red};
```

***

You can also use them inside other controls

**Using XAML**

```xaml
<Button Name="BtnIcon" Content="{materialDesign:PackIcon SmileyHappy}"
        ToolTip="Icon"/>
```

**Using Code-Behind**

```cs
BtnIcon.Content = new PackIcon() {Kind=PackIconKind.SmileyHappy}
```