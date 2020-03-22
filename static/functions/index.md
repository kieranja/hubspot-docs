# index
Returns the location of the first matching item in a 0 based `array`.

This function accepts 3 parameters, The first parameter is required. The first parameter is the item you are trying to find in the `array`. The second (`start`) and third (`end`) enable you to find that item in a slice of the `array`.

#### Example
```jinja2
{% set shapes = ["triangle","square","trapezoid","triangle"] %}
triangle index: {{shapes.index("triangle")}} <br>
trapezoid index: {{shapes.index("trapezoid")}}
<hr>
adjusted start and end <br>
triangle index: {{shapes.index("triangle",1,5)}}
```

#### Output
```jinja2
triangle index: 0<br>
trapezoid index: 2
<hr>
adjusted start and end<br>
triangle index: 3
```

