# hubdb_table_column
For a comprehensive overview of HubDB, read our [HubDB page ](/docs/features/hubdb)in the CMS Developer tools section.

The `hubdb_table_column` function can be used to get information on a column in table such as its label, type and options. This function accepts two parameters.

These pieces of information about the column can be pulled by calling the appropriate attributes:

- `id` - the ID of the column
- `name` - the name of the column
- `label` - the label to be used for the colum
- `type` - the type of the column
- `options` - for columns of type 'select', a map of optionId to option information
- `foreignIds` - for columns of type `'foreignId'`, a list of `foreignIds` (with `id` and `name` properties)

In addition to the above attributes, there is also a method which can be called: **`getOptionByName("")`** whereby for columns of type `'select'`, this will get option info by the option's name.

#### Example
```jinja2
{% set column_info = hubdb_table_column(123456, 6)  %} 
{{ column_info.label }}
```

#### Output
```jinja2
role
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| table_id | String | Id or name of the table. | 
| column | String | Id or name of the column. | 

