# content_by_ids
Given a list of content IDs, returns a dict of landing page, website page or blog posts matching those IDs.

This function takes one parameter, a list of page or blog post IDs to look up, placed within an array. Up to 100 content objects can be passed. The below example code shows this function in use to generate a list of hyperlinked list items.

#### Example
```jinja2
{% set contents = content_by_ids([4715624297, 4712623297, 5215624284]) %}
<ul>
{% for content in contents %}
    <li>
        <a href="{{ content.absolute_url }}">{{content.title}}</a>
    </li>
    {% endfor %}
</ul>
```

#### Output
```jinja2
<ul>
    <li>
        <a href="http://www.hubspot.com/blog/articles/kcs_article/email/how-do-i-create-default-values-for-my-email-personalization-tokens">How do I create default values for my email or smart content personalization tokens?</a>
    </li>
    <li>
        <a href="https://blog.hubspot.com/marketing/content-marketing-strategy-guide">Content Marketing Strategy: A Comprehensive Guide for Modern Marketers</a>
    </li>
</ul>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| ids | List | A list of page or blog post ids to look up. Up to 100 content objects can be passed. | 

