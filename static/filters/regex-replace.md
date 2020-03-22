# regex_replace
Searches for a regex pattern and replaces with a sequence of characters. The first argument is a RE2-style regex pattern, the second is the replacement string.

Information on the RE2 regex syntax can be found [here](https://github.com/google/re2/wiki/Syntax).

#### Example
```jinja2
{{ "contact-us-2"|regex_replace("[^a-zA-Z]", "") }} 
```

#### Output
```jinja2
contactus
```

