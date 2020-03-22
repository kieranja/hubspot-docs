# Key, value pairs in loops
If the dict of information you are looping through has key and value pairs, a simple for loop would only have access to the values. If you wish to have access to both the keys and values within the for loop, the HubL would be formatted as such:

#### Example
```jinja2
{‌% set dict_var = {'name': 'Cool Product', 'price': '$20', 'size':'XL'} %}  
{‌% for key, val in dict_var.items() %}
    {‌{ key }}: {‌{ val }}<br>
{‌% endfor %}
```

#### Output
```jinja2
name: Cool Product <br>
price: $20 <br>
size: XL <br>
```

