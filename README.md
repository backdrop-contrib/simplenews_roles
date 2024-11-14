# Simplenews Roles Module for Backdrop CMS

The Simplenews Roles module for Backdrop CMS synchronizes user subscriptions to newsletters based on their role membership. This module allows automatic subscription/unsubscription of users to specific newsletters by associating user roles with newsletters, ensuring that only users with the specified roles are subscribed. Additionally, users manually added to a subscription list will be automatically removed if they do not belong to the designated roles (unless auto-remove is disabled).

## Features

- **Automatic Role-based Subscriptions**: Automatically subscribe users to newsletters based on their roles.
- **Auto-Remove**: Optionally remove users who no longer belong to the subscribed roles.
- **Synchronization via Cron**: Supports regular synchronization of subscriptions through cron jobs.
- **Configuration**: Define role-based subscriptions in the module's settings and set limits for subscribe/unsubscribe operations per cron run.

## Installation

1. Place the `simplenews_roles` directory in your Backdrop CMS `modules` directory.
2. Enable the module in the **Modules** section of the Backdrop CMS admin.
3. Navigate to **Configuration** > **Simplenews Roles Settings** to configure role-based newsletter subscriptions.

## Configuration

1. Go to the **Simplenews Roles Settings** page under **Configuration** to set up your role-to-newsletter mappings.
2. Select the roles that should be automatically subscribed to each newsletter.
3. Enable or disable the **Auto Remove** option for each newsletter.

## Usage

### Adding Role Synchronization to Newsletters

When adding or editing a newsletter, a **Role Synchronization** fieldset will appear:
- **Roles**: Select which user roles should be automatically subscribed to this newsletter.
- **Auto Remove**: Enabling this option will remove users from the newsletter if they lose the specified role(s).

### Syncing User Subscriptions

Subscriptions are synchronized on each save of the newsletter settings. Additionally, Backdrop’s cron will automatically synchronize subscriptions based on the configuration.

## API Functions

- **simplenews_roles_update_subscriptions**: Manually synchronize users and newsletters based on their roles.
- **simplenews_roles_user_insert** and **simplenews_roles_user_update**: Automatically handle subscriptions when a user is created or updated.

## Hooks Implemented

- **hook_config_info**: Defines configuration settings for Simplenews Roles.
- **hook_form_FORM_ID_alter**: Adds role synchronization settings to the newsletter form.
- **hook_user_insert** and **hook_user_update**: Syncs user subscriptions based on roles when users are created or updated.
- **hook_cron**: Handles ongoing subscription synchronization via cron.
- **hook_autoload_info**: Provides autoloading for this module.

## Notes

- **Performance**: Enabling auto-remove on large sites may impact performance, as removing users based on role changes can be a resource-intensive process. Consider limiting synchronization frequency using cron settings.
- **Compatibility**: This module is designed specifically for Backdrop CMS and is a conversion from a previous Drupal 7 module.

## Troubleshooting

Bugs and Feature requests should be reported in the Issue Queue:
https://github.com/backdrop-contrib/simplenews_roles/issues.

## Maintainers

This module is ported from Drupal 7 version and maintained by [Alan Mels](https://github.com/alanmels) of [AltaGrade.com](https://www.altagrade.com) and is open to contributions. Please feel free to submit issues and feature requests.
