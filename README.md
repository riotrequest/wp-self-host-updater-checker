# WP Self-Host Updater Checker

A lightweight PHP solution designed to work with the [WP Self-Host Updater Generator](https://github.com/eduardovillao/wp-self-host-updater-generator) GitHub Action. This repository provides the client-side PHP script required to integrate seamlessly with your self-hosted update server (on Github), supporting updates for WordPress plugins and themes while adhering to WordPress standards.

## How It Works

1. Use the [WP Self-Host Updater Generator](https://github.com/eduardovillao/wp-self-host-updater-generator) to host the `.zip` file and generate the required JSON metadata.
2. Add this PHP script to your WordPress plugin or theme to handle update checks.
3. WordPress automatically queries the GitHub-hosted JSON file, compares versions, and updates if a new version is available.

## How to use

1. Clone this repository or download the PHP file.
2. Include the PHP file in your WordPress plugin or theme.
3. Init the class like the example below.

```php
require_once __DIR__ . '/path/to/class-updater-checker.php';

use Use\Your\Namespace\Updater_Checker;

$github_username = 'your-github-username';
$github_repository = 'your-repository-name';
$plugin_basename = plugin_basename( __FILE__ ); // Example: my-plugin/my-plugin.php // Make sure this is in the root plugin file.
$plugin_current_version = '1.0.0';

$updater = new Updater_Checker(
    $github_username,
    $github_repository,
    $plugin_basename,
    $plugin_current_version
);
$updater->set_hooks();
```

### Important Note About `plugin_basename`

The `plugin_basename(__FILE__)` function works correctly **only when used in the root file of your plugin**. If you call this function in a subfolder or include file, it may return an incorrect value, causing issues with plugin updates.

So if you are including and instantiations the updater class in other folder that it not the root file use a manual declaration or any consant that may you was deinfed in the root file.

```php
$plugin_basename = 'my-plugin/my-plugin.php'; // Specify manually if necessary.
```

## Coming Soon
- Support for Private Github repositories.
- Support for mu-plugins.
