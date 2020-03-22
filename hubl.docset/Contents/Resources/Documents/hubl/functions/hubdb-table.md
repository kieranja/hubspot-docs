# hubdb_table
For a comprehensive overview of HubDB, read our [HubDB page ](/docs/features/hubdb)in the CMS Developer tools section.

The `hubdb_table` function can be used to get information on a table including its name, columns, last updated, etc.

The following pieces of information can be pulled by calling the appropriate attributes:

- `id` - the ID of the table
- `name` - the name of the table
- `columns` - a list of column information
- `created_at` - timestamp of when this table was first created
- `published_at` - timestamp of when this table was published
- `updated_at` - timestamp of when this table was last updated
- `row_count` - the number of rows in the table

#### Example
```jinja2
{% set table_info = hubdb_table(1548215) %} 
{{ table_info.row_count }}
```

#### Output
```jinja2
25
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| table_id | String | Id or name of the table. | 

