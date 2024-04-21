Sometimes you may want to use the toolkit's brushes directly in your XAML. Typically you'll use them as dynamic resources, so they update with the current material palette.

# Palette Brush Names

## Primary Color

* MaterialDesign.Brush.Primary.Light
* MaterialDesign.Brush.Primary.Light.Foreground
* MaterialDesign.Brush.Primary
* MaterialDesign.Brush.Primary.Foreground
* MaterialDesign.Brush.Primary.Dark
* MaterialDesign.Brush.Primary.Dark.Foreground

NB `[Light/Mid/Dark]Brush` define the different hues of the color, and the `[Light/Mid/Dark].Foreground` define a foreground color which will show up clearly on that hue.


## Secondary Color

* MaterialDesign.Brush.Secondary.Light
* MaterialDesign.Brush.Secondary.Light.Foreground
* MaterialDesign.Brush.Secondary
* MaterialDesign.Brush.Secondary.Foreground
* MaterialDesign.Brush.Secondary.Dark
* MaterialDesign.Brush.Secondary.Dark.Foreground

NB `[Light/Mid/Dark]Brush` define the different hues of the color, and the `[Light/Mid/Dark].Foreground` define a foreground color which will show up clearly on that hue.

Prior to version 2.6.0 there was only these accent brushes. Though these still exist in version 3.0.0, they should be considered obsolete and were removed in 5.0.0.
* SecondaryAccentBrush
* SecondaryAccentForegroundBrush

## Example Usage

```<TextBlock Foreground="{DynamicResource MaterialDesign.Brush.Primary}" />```
