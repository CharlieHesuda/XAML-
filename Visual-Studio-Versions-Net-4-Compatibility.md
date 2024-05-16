# Visual Studio Versions

__The nuget package is backwardly compatible with older Visual Studio versions__, including 2012, 2013, 2015.

Compiling the __source__ code requires Visual Studio 2022.

If you are not running VS2022, but want to view the demo you have a couple of options:

 * Grab the latest demo which is a compiled .exe in a zip, found on the [Releases](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/releases) page.
 * VS2022 users can clone and checkout the tag of the source used to compile the desired version:

```
git clone https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit.git
cd MaterialDesignInXamlToolkit
git checkout tags/<desired version>
```

# .Net 4.0

There is a .Net 4.0 branch (net40) which is now only maintained by contributors, and is no longer officially supported:

* Branch: https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit/tree/net40
