# Understanding Routed commands

This question has come up a lot so I wanted to put down a more detailed answer. First, all of this information can be found in the [WPF docs](https://docs.microsoft.com/en-us/dotnet/desktop/wpf/advanced/commanding-overview?view=netframeworkdesktop-4.8). However, that is quite a long article, and none of it is specific to this library (and most people asking about this encounter the issue when working with the `DialogHost` control in this library). What follows is my attempt to explain the same concepts as they relate to this library.

Many WPF controls that allow user interaction (such as `Button`), have [`ICommand`](https://docs.microsoft.com/dotnet/api/system.windows.input.icommand) properties on them. An `ICommand` is a pretty simple interface that encompasses two pieces of functionally. An "execute action" or bit of code to run when the command is invoked, and a "can execute" or bit of code that returns a boolean indicating if the action can be executed. When you set the Command property two things happen:

1. The control will likely show as enabled/disabled depending on the command's "can execute".
1. The control will run the "execute action" part of the command when the user interacts with the control (such as clicking the button).

Obviously if the button is disable from the first step, it will be impossible for the user to be able to click it for the second step. This is important to keep in mind as we turn our attention to one specific `ICommand` implementation, [`RoutedCommand`](https://docs.microsoft.com/dotnet/api/system.windows.input.routedcommand).

With `RoutedCommand`, the key thing to understand, is there is a separation between the control that invokes the command and the code that handles that command. It is quite common to find yourself in a situation where a nested control needs to perform an action, but the code to handle that action exists at a different location. Imagine clicking a button that wants to close its parent window. The button would invoke a command, but the window would provide the handler for the command to do the work of actually closing the window. However, **if a routed command cannot find a handler, its "can execute" will always return false.**

To understand setting up an using RoutedCommands, let's look at an [example](https://github.com/Keboo/MaterialDesignInXaml.Examples/tree/master/DialogHost/DialogHost.RoutedCommand) using the `DialogHost` control.
```xaml
...
<materialDesign:DialogHost>
    <materialDesign:DialogHost.DialogContent>
        <StackPanel Margin="15">
            <StackPanel.CommandBindings>
                <CommandBinding Command="{x:Static materialDesign:DialogHost.CloseDialogCommand}"
                                CanExecute="CommandBinding_OnCanExecute" />
            </StackPanel.CommandBindings>

            <TextBlock Text="Is this ok?" />
            <CheckBox Content="Check me" x:Name="CheckBox"/>

            <Button Content="Close" Command="{x:Static materialDesign:DialogHost.CloseDialogCommand}" />
        </StackPanel>
    </materialDesign:DialogHost.DialogContent>

    <StackPanel HorizontalAlignment="Center" VerticalAlignment="Center">
        <Button Content="Show Dialog" Command="{x:Static materialDesign:DialogHost.OpenDialogCommand}" />
        ...
    </StackPanel>
</materialDesign:DialogHost>
```
The code above shows usage of two routed commands, `DialogHost.OpenDialogCommand` and `DialogHost.CloseDialogCommand`.
Let's start with the `CloseDialogCommand`. Note that it is used in two places, first as the `Command` for the "Close" button, and second as the `Command` for a `CommandBinding` on the `StackPanel`. The "Close" button is the *command source*; it is the object that invokes the command. When determining if the command "can execute" it works up through the element tree until it finds a [CommandBinding](https://docs.microsoft.com//dotnet/api/system.windows.input.commandbinding) with a matching command that contains a handler for [`CanExecute`](https://docs.microsoft.com/dotnet/api/system.windows.input.commandbinding.canexecute). In this case it will find one  on the `StackPanel`. The contents of the handle look like this:
```C#
private void CommandBinding_OnCanExecute(object sender, CanExecuteRoutedEventArgs e)
{
    e.Handled = true;
    e.CanExecute = CheckBox.IsChecked == true;
}
```
This handler simply marks the command as able to execute if the `CheckBox` is checked.

When the command finally "can execute", it once again works up through the element tree until it finds a [CommandBinding](https://docs.microsoft.com//dotnet/api/system.windows.input.commandbinding) with a matching command that contains a handler for [`Execute`](https://docs.microsoft.com/dotnet/api/system.windows.input.routedcommand.execute). However, in this case we have not explicitly created one. Most of the time, a `CommandBinding` will be something that you create in your code. There are, however, a few cases where there are built-in handlers for some routed command (such as the common [Copy](https://docs.microsoft.com/dotnet/api/system.windows.input.applicationcommands.copy) and [Paste](https://docs.microsoft.com/dotnet/api/system.windows.input.applicationcommands.paste) commands for a TextBox). Within this library, the [`DialogHost`](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/blob/master/MaterialDesignThemes.Wpf/DialogHost.cs) control's constructor creates a couple of `CommandBindings`.
```C#
public DialogHost()
{
    ...
    CommandBindings.Add(new CommandBinding(CloseDialogCommand, CloseDialogHandler, CloseDialogCanExecute));
    CommandBindings.Add(new CommandBinding(OpenDialogCommand, OpenDialogHandler));
}
```
This means that the CommandBinding that will get matched will be the one on the `DialogHost` itself. As you might expect the handlers for these commands open and close the dialog.

This also should help explain how the `OpenDialogCommand` command on the "Show Dialog" button works. When looking for a matching `CommandBinding` it always finds the one on the `DialogHost` since it is the first one encountered in the element tree.

A common mistake is to simply set a Button's command to one of the `DialogHost` Open/Close commands (as is what many example show) and have the button become disabled. This occurs when it is unable to locate a handler for those commands. Since the only built-in functionality for handling these commands is found within the `DialogHost` control the common advice is to simply put the button inside the element tree of a `DialogHost` control. 

Finally, it is worth a brief mention of the [`CommandTarget`](https://docs.microsoft.com/en-us/dotnet/desktop/wpf/advanced/commanding-overview?view=netframeworkdesktop-4.8#command-target) property. In the previous example there was not an explicit `CommandTarget` specified so the default will the the control that has keyboard focus. Because of this handy default, in many situations you will not need to specify the CommandTarget.

In the [example project](https://github.com/Keboo/MaterialDesignInXaml.Examples/tree/master/DialogHost/DialogHost.RoutedCommand) you can see an example of setting the `CommandTarget`, using a Button that is outside of the `DialogHost` so that it can properly find the handlers for the `RoutedCommand`.
```xaml
<Button Content="Show Dialog (using CommandTarget)" 
        Command="{x:Static materialDesign:DialogHost.OpenDialogCommand}"
        CommandTarget="{Binding ElementName=MyDialogHost}"
        Margin="0,0,0,10" Grid.Row="1"/>
```