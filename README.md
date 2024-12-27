# WP Self-Host Updater Checker

A lightweight PHP solution designed to work with the [WP Self-Host Updater Generator](https://github.com/eduardovillao/wp-self-host-updater-generator) GitHub Action. This repository provides the client-side PHP script required to integrate seamlessly with your self-hosted update server (on Github), supporting updates for WordPress plugins and themes while adhering to WordPress standards.

## How It Works

1. Use the [WP Self-Host Updater Generator](https://github.com/eduardovillao/wp-self-host-updater-generator) to host the `.zip` file and generate the required JSON metadata.
2. Add this PHP script to your WordPress plugin or theme to handle update checks.
3. WordPress automatically queries the GitHub-hosted JSON file, compares versions, and updates if a new version is available.

## How to use

1. Get the file `class-updater-checker.php` from this repository.
2. Include the PHP file in your WordPress plugin.
3. Init the class like the example below.

```php
require_once __DIR__ . '/path/to/class-updater-checker.php'; // Use your path to file

use Use\Your\Namespace\Updater_Checker; // Use your namespace

$github_username = 'your-github-username'; // Use your gitbub username
$github_repository = 'your-repository-name'; // Use your repository name
$plugin_basename = plugin_basename( __FILE__ ); // Check note below
$plugin_current_version = '1.0.0'; // Use the current version of the plugin

$updater = new Updater_Checker(
    $github_username,
    $github_repository,
    $plugin_basename,
    $plugin_current_version
);
$updater->set_hooks();
```

### Important Note About `plugin_basename`

The `plugin_basename(__FILE__)` function **works correctly only when used in the root file of your plugin**. If you call this function from a subfolder or an included file, it may return an incorrect value, potentially causing issues with plugin updates.

If you are including and instantiating the updater class from a file located in a subfolder, you should manually define the basename or use a constant declared in the root file of your plugin.

```php
$plugin_basename = 'my-plugin/my-plugin.php'; // Specify manually if necessary.
```

Example Using a Constant Defined in the Root File:
```php
// In your root plugin file (my-plugin.php):
define( 'MY_PLUGIN_BASENAME', plugin_basename( __FILE__ ) );

// So in other files you can use
$plugin_basename = MY_PLUGIN_BASENAME;
```

## Coming Soon
- Support for Private Github repositories.
- Support for mu-plugins.
