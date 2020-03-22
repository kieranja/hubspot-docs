# hubdb_table_row
For a comprehensive overview of HubDB, read our [HubDB page ](/docs/features/hubdb)in the CMS Developer tools section.   
  
The `hubdb_table_row` function can be used to pull a single row from a HubDB table. From this row, you can pull information from each table cell by calling on the corresponding attribute:   
  
(Built-in and custom column names are case insensitive. HS\_ID will work the same as hs\_id)

- `hs_id` - the globally unique id for this row
- `hs_created_at` - a timestamp representing when this row was created
- `hs_path` - when used with dynamic pages, this string is the last segment of the url's path for the page
- `hs_name` - when used with dynamic pages, this is the title of the page
- `` or `[""]` - Get the value of the column for this row by the `name` of the column

#### Example
```jinja2
{% set row = hubdb_table_row(1548264, 6726439331)  %} 
{{ row.role  }}
```

#### Output
```jinja2
CTO
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| table_id | String | Id or name of the table. | 
| row_id | Integer | Id of the row of the table. | 

