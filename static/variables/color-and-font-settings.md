# Color and font settings
There are several basic color and font controls in **Settings &gt; Marketing &gt; Configuration &gt; Color** that can be printed to templates and files. Please note that if you use these variables in CSS files, you will need to republish/recompile your CSS file when you change one of the settings, for the new color to apply.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| site_settings.background_color | Dict	 | Background color setting from Settings > Marketing > Email > Configuration > Color. Prints a HEX value. | 
| site_settings.body_border_color | String | Body border color setting from Settings > Marketing > Email > Configuration > Color. This option becomes available when you select "Manually set email border color" under the "Border Color Options" dropdown. Prints a HEX value. | 
| site_settings.body_border_color_choice | Enumeration | The variable is used in HubSpot's default email templates to determine whether or not a border should be added. The setting is controlled in Content Settings > Colors and Fonts. It prints values: BORDER_AUTOMATIC, BORDER_MANUAL, BORDER_NONE | 
| site_settings.body_color | String | Body color setting from Settings > Marketing > Email > Configuration > Color. Prints a HEX value. | 
| site_settings.color_picker_favorite_1 | String | Favorite color 1 setting from Settings > Marketing > Email > Configuration > Color. Prints a HEX value. Replace 1 with 2-6 to modify the tag for other favorite color settings. | 
| site_settings.primary_accent_color | String | Primary accent color setting from Settings > Marketing > Email > Configuration > Color. Prints a HEX value. | 
| site_settings.primary_font | Enumeration | Primary font setting from Settings > Marketing > Email > Configuration > Font. Prints value from dropdown. | 
| site_settings.primary_font_color | String | Primary font color setting from Settings > Marketing > Email > Configuration > Font. Prints a HEX value. | 
| site_settings.primary_font_size | String | Primary font size setting from Settings > Marketing > Email > Configuration > Font. Includes "px". | 
| site_settings.secondary_accent_color | String | Secondary font color setting from Settings > Marketing > Email > Configuration > Color Prints a HEX value. | 
| site_settings.secondary_font | Enumeration | Secondary font setting from Settings > Marketing > Email > Configuration > Font. Prints value from dropdown. | 
| site_settings.secondary_font_color | String | Secondary font color setting from Settings > Marketing > Email > Configuration > Font Prints a HEX value. | 
| site_settings.secondary_font_size | String | Primary font size setting from Settings > Marketing > Email > Configuration > Font. Includes "px". | 

