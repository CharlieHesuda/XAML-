The [ComboBox](https://learn.microsoft.com/en-us/dotnet/api/system.windows.controls.combobox) control presents users with a list of options. The list is shown and hidden as the control expands and collapses. In its default state, the list is collapsed, displaying only one choice.

## Changing the color of the underline
The color of the underline can be changed by applying the `TextFieldAssist.UnderlineBrush` brush.
```xaml
<ComboBox Style="{DynamicResource MaterialDesignComboBox}" materialDesign:TextFieldAssist.UnderlineBrush="Chocolate" >
    <ComboBoxItem IsSelected="True">Item 1</ComboBoxItem>
</ComboBox>
```
![2022-10-09 22_11_22-Window](https://user-images.githubusercontent.com/33844665/194777510-e958ffdc-281a-4f12-a47d-c3fe83449f18.png)


# Styles

The Material Design In XAML Toolkit provides two styles:
* MaterialDesignComboBox 
* MaterialDesignFloatingHintComboBox

## MaterialDesignComboBox
The default ComboBox in the Material Design.
```xaml
<ComboBox Style="{DynamicResource MaterialDesignComboBox}">
    <ComboBoxItem IsSelected="True">Item 1</ComboBoxItem>
</ComboBox>
```
![2022-10-09 22_03_39-Window](https://user-images.githubusercontent.com/33844665/194777307-c0583f78-cddc-490e-b719-56aad18090bd.png)

## MaterialDesignFloatingHintComboBox
Adds a customizable hint above the item preview.
```xaml
<ComboBox Style="{DynamicResource MaterialDesignFloatingHintComboBox}" materialDesign:HintAssist.Hint="Hint text">
    <ComboBoxItem IsSelected="True">Item 1</ComboBoxItem>
</ComboBox>
```
![2022-10-09 22_06_00-Window](https://user-images.githubusercontent.com/33844665/194777314-9d294b7d-90aa-4801-bffb-5ad349c37803.png)

### Changing the color of the Hint
The color of the hint can be changed by applying the `HintAssist.Foreground` brush.
```xaml
<ComboBox Style="{DynamicResource MaterialDesignFloatingHintComboBox}" materialDesign:HintAssist.Foreground="DeepPink" materialDesign:HintAssist.Hint="Hint text">
    <ComboBoxItem IsSelected="True">Item 1</ComboBoxItem>
</ComboBox>
```
![2022-10-09 22_16_21-Window](https://user-images.githubusercontent.com/33844665/194777676-104fde0c-1737-4cef-9224-9227183de61a.png)
