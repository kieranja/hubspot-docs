# personalization_token
Returns the value of a contact or contact related property, or a default.

#### Example
```jinja2
Hi {{ personalization_token("contact.firstname", "there") }}!
```

#### Output
```jinja2
<!-- If the contact is known -->
Hi Dharmesh!

<!-- If the contact is unknown -->
Hi there!
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| expression | String | An expression for the object and property to render. | 
| default | String | (Optional) A default value to use if the expression has no value. | 

