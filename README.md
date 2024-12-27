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
require_once 'path-to/class-updater-checker.php';

$updater = new Updater_Checker();
$updater->init();
```

## Coming Soon
- Support for Private Github repositories.
- Support for mu-plugins.
