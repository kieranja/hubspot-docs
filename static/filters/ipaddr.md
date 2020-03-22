# ipaddr
Evaluates to true if the value is a valid IPv4 or IPv6 address.

#### Example
```jinja2
{% set ip = '1.0.0.1' %}
{% if ip|ipaddr %}
    The string is a valid IP address
{% endif %}
```

#### Output
```jinja2
    The string is a valid IP address
```

