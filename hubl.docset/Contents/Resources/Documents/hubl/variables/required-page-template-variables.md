# Required page template variables
To publish a coded file as an editable page or blog template, the following variables must be included. If you want to publish an HTML file without these variables, to use within another template, you can do so by unchecking the option "Make this template available for new content".
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| standard_footer_includes | String | Renders the HubSpot tracking code and any other code included in your Footer HTML in Content Settings or the options of a particular page. This tag should be inserted directly before the closing body tag. | 
| standard_header_includes | String | Adds jQuery, public_common.css, layout.css, any attached stylesheets, a meta viewport tag, Google Analytics tracking code, other page meta information, and code added to the head tag at the domain/template/page level. This variable should be added to the <head> of HTML templates. | 

