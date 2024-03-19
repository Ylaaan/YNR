# Gitlab Pipeline

- [Pre-filled variables](#Pre-filled%20variables)

## 🔡CI-Variables🔢

CI variables can be set at the project or group level, note that only owners cat modify group variables.

> Be careful : Variables keys, cannot contain `-` characters.

Variables can also be used in specific environments only.


### Types

|   Type   | Description               | Default |
|:--------:|:------------------------- |:-------:|
| Variable | Regular variable type     |   ✅    |
|   File   | Treats variable as a file |   ❌    |

### Flags


|   Flags   | Description                                                   |
|:---------:|:------------------------------------------------------------- |
|  Masked   | Hides value in logs, can break code if change without caution |
| Expanded  | Allows the use of variables inside the variable               |
| Protected | Disallow use of this variable outside protected branches      |


## 🎛Pre-filled variables🎛

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