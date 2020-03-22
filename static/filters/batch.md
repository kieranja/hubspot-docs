# batch
A batch filter groups up items within a sequence.
| Parameter | Description | 
|  ------  |  ------  | 
| linecount `Required` | The number of items to include in the batch | 
| fill_with `Optional` | Specifies what to include in order to fill up any missing items | 

In the example below, there is variable containing a sequence of types of fruits. The batch filter is applied to a loop that iterates through the sequence. The nested loop runs three times to print 3 types of fruit per row, before the outer loop runs again. Notice in the final output that since there are only 5 types of fruit, the final item is replaced by a &amp;nbsp (the second parameter).

#### Example
```jinja2
{% set rows = ['apples', 'oranges', 'pears', 'grapes', 'blueberries'] %}

<table>
{% for row in rows|batch(3, '&nbsp;') %}
   <tr>
    {% for column in row %}
        <td>{{ column }}</td>
    {% endfor %}
    </tr> 
{% endfor %}
</table>
```

#### Output
```jinja2
<table>
<tbody>
    <tr>
        <td>apples</td>
        <td>oranges</td>
        <td>pears</td>
   </tr> 
   <tr>
        <td>grapes</td>
        <td>blueberries</td>
        <td>&nbsp;</td>
    </tr> 
</tbody>
</table>
```

