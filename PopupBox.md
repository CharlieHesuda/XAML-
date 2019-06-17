The popup box is a helper control that functionally consists of a `ToggleButton` that you click on to show some content in a `Popup`. 

### Change the default icon
By default the `PopupBox` uses the built-in `PackIcon.DotsVertical` as the `ToggleButton`'s content, however you can change the content to be anything you want.
As a simple example you can change the content to be a different `PackIcon` like this:
```XAML
<materialDesign:PopupBox>
    <materialDesign:PopupBox.ToggleContent>
        <materialDesign:PackIcon Kind="DotsHorizontal" />
    </materialDesign:PopupBox.ToggleContent>
</materialDesign:PopupBox>
```