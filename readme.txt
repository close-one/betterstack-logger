=== BetterStack Logger ===
Contributors: millertchris
Donate link: https://github.com/sponsors/millertchris
Plugin Name: BetterStack Logger
Plugin URI:  https://prolificdigital.com
Tags: betterstack, logger, logging, debug, monitor
Stable tag: 2.0.0
Requires at least: 6.0
Requires PHP: 8.0
Tested up to: 6.6
Author: Prolific Digital
Author URI: https://prolificdigital.com
License: GPLv2 or later
License URI: https://www.gnu.org/licenses/gpl-2.0.html
Text Domain: betterstack-logger
Seamlessly integrate with BetterStack to log messages directly from your WordPress site.

== MODIFIED VERSION NOTICE ==

This is a modified version of the original BetterStack Logger plugin. Security improvements, bug fixes and new features have been applied.

Forked from: https://github.com/prolific-digital/betterstack-logger

= New Features in This Fork =

* **PHP Error Capture:** Automatically capture PHP errors, warnings, and notices with configurable verbosity levels.
* **Site Prefix:** Auto-detect or customize a prefix for all log messages to distinguish between environments (production/staging/dev).
* **Custom Ingesting Host:** Configure a custom BetterStack ingesting URL for regional or self-hosted endpoints.

== Description ==

BetterStack Logger is a powerful WordPress plugin that allows you to seamlessly integrate BetterStack with your WordPress site. Enhance your logging capabilities by sending error messages, post changes, user actions, and more directly to BetterStack. With easy configuration and flexible logging functions, this plugin is an essential tool for developers and site administrators looking to keep track of their site's activities.

## Features

- **Error Logging:** Capture and log WordPress errors directly to BetterStack.
- **PHP Error Capture:** Automatically capture PHP errors, warnings, and notices with configurable verbosity levels.
- **User Action Logging:** Log important user actions such as logins, registrations, and profile updates.
- **Post Changes:** Monitor post creation, updates, and deletions.
- **Plugin and Theme Activity:** Log plugin activations/deactivations and theme switches.
- **Customizable Logging:** Use helper functions to log custom messages from anywhere in your codebase.
- **Site Prefix:** Auto-detect or customize a prefix for log messages to distinguish environments.
- **Settings Page:** Easily configure the API key, enable or disable specific logging features via the WordPress admin panel.
- **Support for `wp-config.php`:** Define settings in `wp-config.php` for additional security and portability.

## Installation

### From Your WordPress Dashboard

1. Navigate to `Plugins` -> `Add New`.
2. Search for `BetterStack Logger`.
3. Click `Install Now`.
4. Activate the plugin.
5. Go to `Tools` -> `BetterStack Logger Settings` to configure the plugin.

### Manual Installation

1. Download the plugin from the [Plugin Releases](https://github.com/prolific-digital/betterstack-logger/releases).
2. Upload the `betterstack-logger` directory to the `/wp-content/plugins/` directory.
3. Activate the plugin through the `Plugins` menu in WordPress.
4. Go to `Tools` -> `BetterStack Logger Settings` to configure the plugin.

## Configuration

### API Key

To log messages to BetterStack, you need to set up your API key:

1. Go to `Tools` -> `BetterStack Logger Settings`.
2. Enter your BetterStack API key in the `API Key` field.
3. Optionally, define the API key in your `wp-config.php` file using `BETTERSTACK_API_KEY`.

### Logging Options

- **Enable Error Logging:** Toggle to capture WordPress errors.
- **Enable Event Logging:** Toggle to log user actions, post changes, and more.

### PHP Error Verbosity

Control which PHP errors are sent to BetterStack:

- **Disabled:** No PHP errors captured.
- **Errors only:** Fatal errors, parse errors, and compile errors.
- **Errors & Warnings:** (Recommended) Errors plus warnings.
- **Errors, Warnings & Notices:** Includes notice-level messages.
- **All PHP errors:** Everything including deprecated and strict standards.

### Site Prefix

Distinguish logs from different environments (production, staging, development):

- **Auto-detect:** (Default) Automatically derives prefix from the site URL.
- **Disabled:** No prefix added to log messages.
- **Custom:** Specify your own prefix string.

### Ingesting Host URL

By default, logs are sent to `https://in.logs.betterstack.com`. You can configure a custom endpoint for regional or self-hosted BetterStack instances.

## Usage

### Logging Custom Messages

Use the following functions to log messages from anywhere in your code:

```php
// Log a custom message
better_error_log('This is a custom error message.');

// Shorter version
b_log('This is a quick log message.');
```

### Example:

```php
function my_custom_function() {
    // Perform some task
    // ...

    // Log a message
    better_error_log('Task completed successfully.');
}

add_action('init', 'my_custom_function');
```

### Available Functions

- `better_error_log($message)`: Logs a custom message to BetterStack.
- `b_log($message)`: Shorthand function to log a custom message to BetterStack.

## Frequently Asked Questions

Can I define the API key in `wp-config.php`?

Yes! For added security, you can define your API key in `wp-config.php` using:

```php
define('BETTERSTACK_API_KEY', 'your-api-key-here');
```

What other settings can I define in `wp-config.php`?

You can define the following constants:

```php
// Required: Your BetterStack API key
define('BETTERSTACK_API_KEY', 'your-api-key-here');

// Optional: Custom ingesting host URL
define('BETTERSTACK_HOST_URL', 'https://in.logs.betterstack.com');

// Optional: Custom site prefix (overrides auto-detect)
define('BETTERSTACK_SITE_PREFIX', 'mysite-production');
```

What types of events can I log with BetterStack Logger?

You can log errors, user actions (e.g., logins, registrations), post changes (e.g., creation, updates, deletions), plugin activations/deactivations, theme switches, and custom messages.

Does the plugin capture PHP errors automatically?

Yes! The plugin includes a PHP error handler that can capture errors, warnings, and notices and send them to BetterStack. You can configure the verbosity level in the settings page. Error logs include the file path and line number for easy debugging.

## Support

If you need help or have any questions, feel free to reach out to us:

- Visit our [Support Page](https://prolificdigital.notion.site/BetterStack-Logger-c0cc4526efd049c09b77965bf3ecc28e)
- Email us at support@prolificdigital.com
