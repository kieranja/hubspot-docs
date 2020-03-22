# copy
Return a shallow copy of the list. Equivalent to `a[:]`.

A *shallow copy* constructs a new compound object and then (to the extent possible) inserts *references* into it to the objects found in the original.

#### Example
```jinja2
{% set a = ["ham"] %}
{% set b = a.copy() %}
a: {{a}}

b: {{b}}

  After Append
{% do a.append("swiss") %}
a: {{a}}

b: {{b}}
```

#### Output
```jinja2
a: [ham]

b: [ham]

  After Append

a: [ham, swiss]

b: [ham]
```

