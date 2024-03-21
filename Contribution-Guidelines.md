## Ways to contribute
If you have enjoyed using this library and would like to help support it, there are several ways you can help contribute.
* Help answer questions on [issues](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/issues), [discussions](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/discussions) or on [Discord](https://discord.keboo.dev). We all start learning at different places. If you see a question you can answer, feel to respond. Remember to be kind and respectful. We all start learning at different levels.
* [Help improve bug reports](#Improving-bug-reports)
* [Submit code changes](#Pull-Requests)

## Pull Requests
Please take time to read the [contributing guidelines](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/blob/master/.github/CONTRIBUTING.md) before submitting PRs.

### Good First Issue
Issues that [are tagged with "good first issue"](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22) are expected to have good reproduction steps and clear guidelines around what work is needed to complete them. If you are interested in helping out with this library these are great issues to start with. Simply leave a comment on the issue indicating that you are working on it. If you end up not being able to complete the work, please leave another comment so others know that the issue is available to be worked on. 
Questions on these issues will be given priority, so if you are having any problems completing the work, please ask.

### Up-for-grabs Issue
Issues that [are tagged with up-for-grabs](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/labels/up-for-grabs) are available for anyone to work on. Simply leave a comment on the issue indicating that you are working on it to avoid doing duplicate work. If you decide not to complete it, please leave another comment so other people know it is available to be worked on.

## Wiki
If you come across an issue in the Wiki, please feel free to open an issue or discussion. 

## Improving bug reports
When a new issue is filed it often takes time simply to verify the bug before a fix can be done. This process gets more difficult if the bug report is incomplete. Things you can to to help in this area.
A perfect bug report contains:
- Version 
- Good steps to reproduce the issue. Preferably a small sample project that demonstrates the issue.
- A description of the observed failure.
- A description of the expected results.

Things people can do to help with triaging issues
- Verify the issue contains the above information. If you are able to, either add the information in a comment or ask the original poster to do so.
- Attempt to reproduce to the bug. If you are able to reproduce the issue please leave a comment indicating that you were also able to reproduce the bug along with the version of the library that you used. 
- If the original issue did not contain a reproduction solution consider adding one.
- If possible add additional notes or debugging information. For example, if you found the section of code that is causing the issue leave a comment. This can be very helpful for anyone looking to fix the issue.

## Source Code
The main solution file for this project is `MaterialDesignToolkit.Full.sln`. It contains reference to all of the projects. Loading this project and running all of the tests will require having a few additional dependencies installed (see Tests below). If you would prefer to load a smaller subset of the projects you can use the `MaterialDesignToolkit.Wpf.slnf` solution filter. This will load up the projects that are needed for WPF. 

### Coding style
[XamlStyler](https://github.com/Xavalon/XamlStyler) is a Visual Studio extension that styles XAML for better readability. It's recommended to install this extension if you're considering sending in PRs.

### Tests
This library contains several layers of tests. When making pull requests, consider if adding additional tests may be helpful. Not all code can be reasonably tested in this library (for example most of the XAML code cannot be reasonably tested). If you are unfamiliar with writing tests; simply leave a comment in the pull request asking for help.

Unit tests are all located in *.Tests projects. These are simple validation tests that run against the C# code in this library. These are run on every pull request.

If you load the full solution (`MaterialDesignToolkit.Full.sln`) you will also notice that there are UI tests for the library as well. If you want to run these, you will need to install the latest stable version of [WinAppDrive](https://github.com/microsoft/WinAppDriver). If you install it to the default location, the tests will detect it and automatically start it for you (this is the recommended configuration). If you install it to a custom location, you will need to ensure that WinAppDriver is running, prior to running any of the UI tests. Because these tests take significantly longer to run, these test are only run _after_ a pull request is merged.
 