# WP Self-Host Updater Checker

A lightweight PHP solution for self-hosting WordPress plugin and theme updates. This repository provides a seamless system to check for updates and integrate with your self-hosted server, supporting both plugins and themes while adhering to WordPress standards.

## Features

- **Self-hosted Updates**: Manage updates for WordPress plugins and themes outside the official repository.
- **JSON Metadata Integration**: Fetch plugin/theme metadata from your self-hosted server.
- **WordPress Standards**: Fully integrates with the native WordPress update flow.
- **Future-Proof**: Designed to support both plugins and themes.

## How It Works

1. The server (e.g., GitHub repository) hosts the `.zip` file and a JSON metadata file with details about the plugin or theme.
2. This PHP script is added to your plugin or theme to handle update checks.
3. WordPress automatically queries the JSON file, compares versions, and updates if a new version is available.

## Installation

1. Clone this repository or download the PHP file.
2. Include the PHP file in your WordPress plugin or theme.
3. Configure the script to point to your self-hosted update server.

## Coming Soon
- Detailed setup instructions.
- Support for MU-Plugins.
- License validation for premium plugins/themes.
