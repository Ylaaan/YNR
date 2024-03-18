# Gitlab Pipeline

- [Pre-filled variables](#Pre-filled%20variables)

## Pre-filled variables

This will only work in the global `variables:` field.

```yaml
variables:
  VARIABLE_NAME:
    value: "option1"
    options:
      - "option1"
      - "option2"
      - "..."
    description: "Service à deployer."
```

fields : 
- `value:` Mandatory field, give a default value to the variable, of the field `options` is present, the value need to be in that list.
- `options:` optional field, gives the user a drop down list of options when running pipeline
- `description` optional field, gives the user a description of what the variable is for