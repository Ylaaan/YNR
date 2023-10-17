# Adding option flags to a script

[Basic bash commands](../Bash_commands.md)

Allows bash script to use options flags (`-<letter> and --<word>` format.)

## Exemple

An exemple with the `-a`,`-b` and `-h`/`--help` flags.

```bash
while test $# -gt 0; do
  case "$1" in

    -h|--help)
      echo "Show Help"
      exit 0
      ;;
    
    -a)
      shift # Goes to next options
      <commands-to-apply>
      shift
      ;;
    
    -b)
      shift
      <commands-to-apply>
      shift
      ;;
    
    *) #In case wrong argument
      echo "Invalid argument."
      break
      ;;
    
  esac
done
```
