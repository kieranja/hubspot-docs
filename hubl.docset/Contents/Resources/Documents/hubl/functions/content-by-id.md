# content_by_id
The **`content_by_id`** function returns a landing page, website page or blog post by ID. The only parameter accepted by this function is a numeric content ID.

The below example code shows this function in use to generate a hyperlinked list item.

#### Example
```jinja2
{% set my_content = content_by_id(4715624297) %}
<ul>
    <li>
        <a href="{{ my_content.absolute_url }}">{{my_content.title}}</a>
    </li>
</ul>
```

#### Output
```jinja2
<ul>
    <li>
        <a href="http://www.hubspot.com/blog/articles/kcs_article/email/how-do-i-create-default-values-for-my-email-personalization-tokens">How do I create default values for my email or smart content personalization tokens?</a>
    </li>
</ul>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| id | Id | The id of the content to look up. | 

