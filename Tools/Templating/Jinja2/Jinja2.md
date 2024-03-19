# Jinja2 templates

- [Variables](#Variables)
- [For loops](#For%20loops)

Jinja allows you to generate text based files from templates.

It includes functionalities such as:
- Variables
- For loops...

If can be used very easily in Python with the `jinja2` library.

## Variables

In templates, variables follow the following scheme:
```jinja2
{{VARIABLE_NAME}}
```


## For loops

```jinja2
{%- for <VAR> in <LIST> %}
	TEXT
{% endfor %}
```