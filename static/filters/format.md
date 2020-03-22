# format
Apply Python string formatting to an object. %s can be replaced with another variable.

#### Example
```jinja2
{{ "Hi %s %s"|format(contact.firstname, contact.lastname) }} 
```

#### Output
```jinja2
Hi Brian Halligan
```

