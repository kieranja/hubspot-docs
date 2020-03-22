# hubdb_table_rows
For a comprehensive overview of HubDB, read our [HubDB page ](/docs/features/hubdb)in the CMS Developer tools section.

The `hubdb_table_rows` function can be used to list rows of a HubDB table, to be iterated through.

#### Example
```jinja2
{% for row in hubdb_table_rows(1546258, "years_at_company__gt=3&orderBy=count") %}
  the value for row {{ row.hs_id }} is {{ row.name }}
{% endfor %}
```

#### Output
```jinja2
the value for row 6726439331 is Brian Halligan

the value for row 8438997836 is Dharmesh Shah
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| table_id | String | Id or name of the table to query. | 
| query | String | A query such in the same format as a URL query string. If not passed, returns all rows. Additionally, there are several optional filters that can be used. | 

