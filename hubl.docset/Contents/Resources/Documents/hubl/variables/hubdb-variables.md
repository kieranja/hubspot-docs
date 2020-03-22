# HubDB variables
The following variables are used to build dynamic pages with HubDB. These variables are only available for dynamic templates.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| dynamic_page_hubdb_table_id | Long | The ID of the table selected in the 'Advanced Settings` tab of the page editor. | 
| dynamic_page_hubdb_row | Dict | The HubDB row of the dynamic page that matches with the page request path. If the request is to the listing page, this value will be null. | 
| row.hs_id | Long | The internal ID of a HubDB row. | 
| row.hs_name | String | The name of the HubDB row. | 
| row.hs_path | String | The path of the HubDB row. Used to resolve a request to one row in the table specified by dynamic_page_hubdb_table_id. | 
| row.hs_child_table_id | Long | The child table ID of the HubDB row. Can be used to build nested templates. | 
| row.hs_parent_row | Dict | The parent row of the HubDB row. Can only be used when using child tables for nested templates. | 
| dynamic_page_route_level | Integer | Current depth of a page in a multi-level dynamic template. The value starts at 0 and increments with each additional table layer. | 

