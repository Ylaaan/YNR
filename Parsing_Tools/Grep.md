# Grep

grep looks for patterns.

```bash
grep <option> <pattern> <file>
```

or

```bash
<command> | grep <option> <pattern>
```

Options :

- Print lines after pattern :  ``-A <number-of-lines>`` or ``--after-context=<number-of-lines>``
- Print lines before pattern :  ``-B <number-of-lines>`` or ``--before-context=<number-of-lines>``
- Print number of patterns : ``-c`` or ``--count``
- Use Regex pattern : ``-E <regex>`` or ``--extended-regexp <regex>``
- Stop reading after n number of lines : ``-m <line-number>`` or ``--max-count=<line-number>``
- Print boolean resul : ``-q`` or ``--quiet`` or ``--silent``
- Recursive search on directory : ``-R`` or ``-r`` or ``--recursive``
- Show grep version  : ``-V`` or ``--version``
