# range
Returns a list containing an arithmetic progression of integers. With one parameter, range will return a list from 0 up to (but not including) the `value`. With two parameters, the range will start at the first value and increment by 1 up to (but not including) the second `value`. The third parameter specifies the step increment. All values can be negative. Impossible ranges will return an empty list. Ranges can generate a maximum of 1000 values.

Range can be used within a [for loop](/docs/hubl/for-loops) to specify the number of iterations that should run.

#### Example
```jinja2
{{ range(11) }}
{{ range(5, 11) }}
{{ range(0, 11, 2) }}
       
       
{% for number in range(11) %}
{{ number }}
{% endfor %}
```

#### Output
```jinja2
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[5, 6, 7, 8, 9, 10]
[0, 2, 4, 6, 8, 10]
       
       

0

1

2

3

4

5

6

7

8

9

10
```

