# Call
In some instances, you may want to pass additional dynamic information back into the macro block. For example, you may have a large piece of code that you want to feed back into the macro, in addition to the arguments. You can do this using call block and caller(). A call block works essentially like a macro but does not get its own name. The expression caller() specifies where the contents of the call block will render.

In the example below, a `` is added into a macro in addition to the two arguments.

#### Example
```jinja2
 {% macro render_dialog(title, class) %}
  <div class="{{ class }}">
      <h2>{{ title }}</h2>
      <div class="contents">
          {{ caller() }}
      </div>
  </div>
 {% endmacro %}

 {% call render_dialog('Hello World', 'greeting') %}
     <p>This is a paragraph tag that I want to render in my.</p>
 {% endcall %}
```

#### Output
```jinja2
<div class="greeting">
      <h2>Hello World</h2>
      <div class="contents">
          
     <p>This is a simple dialog rendered by using a macro and
     a call block.</p>
 
      </div>
  </div>
```

