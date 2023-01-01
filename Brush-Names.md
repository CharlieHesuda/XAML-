Sometimes you may want to use the toolkit's brushes directly in your XAML. Typically you'll use them as dynamic resources, so they update with the current material palette.

# Palette Brush Names

## Primary Color

* PrimaryHueLightBrush
* PrimaryHueLightForegroundBrush
* PrimaryHueMidBrush
* PrimaryHueMidForegroundBrush
* PrimaryHueDarkBrush
* PrimaryHueDarkForegroundBrush

NB `[Light/Mid/Dark]Brush` define the different hues of the color, and the `[Light/Mid/Dark]ForegroundBrush` define a foreground color which will show up clearly on that hue.


## Secondary Color

* SecondaryHueLightBrush
* SecondaryHueLightForegroundBrush
* SecondaryHueMidBrush
* SecondaryHueMidForegroundBrush
* SecondaryHueDarkBrush
* SecondaryHueDarkForegroundBrush

NB `[Light/Mid/Dark]Brush` define the different hues of the color, and the `[Light/Mid/Dark]ForegroundBrush` define a foreground color which will show up clearly on that hue.

Prior to version 2.6.0 there was only these accent brushes. Though these still exist in version 3.0.0, they should be considered obsolete and will be removed in a future version.
* SecondaryAccentBrush
* SecondaryAccentForegroundBrush

## Example Usage

```<TextBlock Foreground="{DynamicResource PrimaryHueMidBrush}" />```

# Light/Dark Specific Brush Names

* MaterialDesignBackground
* MaterialDesignPaper
* MaterialDesignCardBackground
* MaterialDesignToolBarBackground
* MaterialDesignBody
* MaterialDesignBodyLight
* MaterialDesignColumnHeader
* MaterialDesignCheckBoxOff
* MaterialDesignCheckBoxDisabled
* MaterialDesignTextBoxBorder
* MaterialDesignDivider
* MaterialDesignSelection
* MaterialDesignFlatButtonClick
* MaterialDesignFlatButtonRipple
* MaterialDesignToolTipBackground
* MaterialDesignChipBackground
* MaterialDesignSnackbarBackground
* MaterialDesignSnackbarMouseOver
* MaterialDesignSnackbarRipple
* MaterialDesignTextFieldBoxBackground
* MaterialDesignTextFieldBoxHoverBackground
* MaterialDesignTextFieldBoxDisabledBackground
* MaterialDesignTextAreaBorder
* MaterialDesignTextAreaInactiveBorder

