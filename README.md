PeepSo Recommendation Engine

## Description
The **PeepSo Recommendation Engine** is a WordPress plugin designed to recommend posts to users based on their activity and preferences. It allows users to set preferences for various content categories (e.g., technology, lifestyle, sports) via sliders. These preferences are stored in a custom database table and can be exported as a CSV file for further analysis or reporting.

This plugin integrates seamlessly with PeepSo, a popular social networking plugin for WordPress, and enhances user experience by personalizing content recommendations.

---

## Features
1. **Dynamic Preferences Management:**
   - Users can adjust their preferences for multiple categories using intuitive range sliders.
   - Preferences are saved securely in a custom database table.

2. **AJAX-Powered Saving:**
   - Preferences are saved asynchronously via AJAX for a smooth user experience.

3. **Customizable Categories:**
   - Predefined categories include `technology`, `lifestyle`, `sports`, `entertainment`, `education`, `health`, `travel`, `comedy`, `pets`, and `global_news`.
   - Each category has a unique color for visual distinction.

4. **Export Preferences:**
   - Administrators can export all user preferences as a CSV file from the WordPress admin dashboard.

5. **Shortcode Integration:**
   - A shortcode `[member_preferences]` is provided to embed the preferences page on any post or page.

6. **Responsive Design:**
   - The preferences page is styled with CSS for a clean, modern look that works on all devices.

7. **Security:**
   - Nonce validation ensures secure handling of AJAX requests.
   - User input is sanitized before being saved to the database.

---

## Installation

### Step 1: Upload the Plugin
1. Download the plugin files as a ZIP archive.
2. Go to your WordPress admin dashboard.
3. Navigate to **Plugins > Add New**.
4. Click **Upload Plugin** and select the ZIP file.
5. Click **Install Now** and then **Activate Plugin**.

### Step 2: Create Database Tables
Upon activation, the plugin automatically creates a custom database table named `{prefix}member_preferences` (e.g., `wpmg_member_preferences`). This table stores user preferences.

### Step 3: Embed the Preferences Page
To display the preferences page, use the shortcode `[member_preferences]` on any post or page:
```html
[member_preferences]
```

Alternatively, you can create a custom page template (`page-member-preferences.php`) and assign it to a WordPress page.

---

## Usage

### For Users
1. Log in to your WordPress site.
2. Navigate to the page where the preferences form is embedded (via shortcode or template).
3. Adjust the sliders for each category to set your preferences.
4. Click **Save Preferences** to store your settings.

### For Administrators
1. Go to **Settings > Member Preferences** in the WordPress admin dashboard.
2. Click **Export Member Preferences** to download a CSV file containing all user preferences.

---

## File Structure
The plugin includes the following files and directories:


---

## Customization

### Adding or Removing Categories
To modify the list of categories, update the `$categories` array in the `enqueue_member_preferences_assets()` function:
```php
$categories = [
    'new_category' => ['color' => '#ff0000'], // Example of a new category
    'technology' => ['color' => '#0073aa'],
    'lifestyle' => ['color' => '#ff9800'],
    // Add or remove categories as needed
];
```

### Changing Default Range Values
To adjust the default range values (min, max, step), modify the `$default_min`, `$default_max`, and `$default_step` variables in the `enqueue_member_preferences_assets()` function.

---

## Exported CSV Format
The exported CSV file contains the following columns:
- **ID:** Unique identifier for the preference entry.
- **User ID:** ID of the user who set the preference.
- **Category:** Name of the category (e.g., `technology`, `sports`).
- **Value:** Preference value (integer between 0 and 100).
- **Timestamp:** Date and time when the preference was saved.

Example:
```
ID,User ID,Category,Value,Timestamp
1,2,technology,75,2025-03-14 22:00:00
2,2,sports,50,2025-03-14 22:00:00
```

---

## Troubleshooting

### Issue: "Table 'contents_wp608.wpmg_comments' doesn't exist"
This error occurs if the database table is not created correctly. To resolve:
1. Deactivate and reactivate the plugin to trigger the activation hook.
2. Check the error log (`wp-content/debug.log`) for details.

### Issue: Sliders Not Working
Ensure that:
- jQuery is properly enqueued.
- The `member-preferences.js` file is loaded on the page.
- There are no JavaScript conflicts with other plugins or themes.

### Issue: Preferences Not Saving
Check the error log for nonce validation failures or database errors. Ensure that:
- The `save_preferences` AJAX handler is registered.
- The `member_preferences` table exists in the database.

---

## Support
For support or feature requests, please contact the plugin author:
- **Author:** Dakota
- **Email:** dakota@contentsocial.net

---

## Changelog

### Version 1.5
- Added export functionality for member preferences.
- Improved security with nonce validation for AJAX requests.
- Enhanced UI with category-specific colors.

### Version 1.0
- Initial release with basic preferences management.

---

## License
This plugin is released under the **GNU General Public License v2 or later**. You are free to use, modify, and distribute this plugin as long as you comply with the terms of the license.

---

Thank you for using the **PeepSo Recommendation Engine**! I hope it enhances your users’ experience and helps personalize content recommendations effectively.
