# Jenkins Configuration
Current pre-configured Jenkins master docker image makes use of the scripts found in `jcasc` directory.

For plugins installations or set a specific version for a plugin, we can update the file `plugins/plugins.txt`.

## Jenkins plugins

Plugins for Jenkins can be installed by adding the plugin name (an optionally its version) in `plugins/plugins.txt`. Once a plugin has been added there, a new docker image can be build and once deployed to Jenkins it will install the new plugin.

When we want to uninstall a plugin, we need to follow a few steps:

1. Delete the plugin from `plugins/plugins.txt`
2. Build a new docker image and deploy it.
3. Manually uninstall the plugin from "Manage Plugins" in Jenkins in case volume for previous Jenkins container was preserved

## Jenkins CASC (Configuration as code plugin)

There are using casc configuration files to configure Jenkins instace. Authorization to Jenkins and preconfigured jobs inside are configured with the casc plugin. Any configuration added using the casc plugin needs to have a YAML file placed in `jcasc/`, that way Jenkins will automatically pick the file and configure jenkins based on the files in that directory.