# slice
Slice an iterator and return a list of lists containing those items. The first parameter specifies how many items will be sliced, and the second parameter specifies characters to fill in empty slices.
| Parameter | Description | 
|  ------  |  ------  | 
| slices `Required` | How many items will be sliced. | 
| filler `Required` | Specifies characters to fill in empty slices.  | 


#### Example
```jinja2
{% set items = ['laptops', 'tablets', 'smartphones', 'smart watches', 'TVs'] %}
<div class="columwrapper">
  {% for column in items|slice(3,' ') %}
    <ul class="column-{{ loop.index }}">
    {% for item in column %}
      <li>{{ item }}</li>
    {% endfor %}
    </ul>
  {% endfor %}
</div>
```

#### Output
```jinja2
<div class="columwrapper">
    <ul class="column-1">
      <li>laptops</li>
      <li>tablets</li>
      <li>smartphones</li>
    </ul>
  
    <ul class="column-2">
      <li>smart watches</li>  
      <li>TVs</li>
      <li>&nbsp;</li>
    </ul>
</div>
```

