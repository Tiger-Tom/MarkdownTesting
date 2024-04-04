# What it is
A regular expression builder that manages cross-pattern references and easy
runtime mutability by default

# Features
- Configurable: the default pattern 

# Why & priorities
When working on my programming language, [Caustic](https://codeberg.org/Caustic),
I was displeased at most of the parsers I found, and decided to make my own. For
the parsing of regular expressions, I wanted the following, so this package prioritizes:
- *Runtime modification*: given how one of Caustic's major selling points is the
  variable syntax, I need to be able to easily modify an expression whenever,
  and have all patterns that source from a sub-pattern update

# Examples
Note that examples are given with the default matching pattern, so references will be made as `(?~name)`

## [/examples/pragma-parser.py](https://codeberg.org/Shae/RegExCompose/src/branch/main/examples/pragma-parser.py)
The following script runs a REPL that will match each line of input against
a "pragma" statement that can change the patterns on-the-fly

```python3
#> Imports
import re
import regex_compose
#</Imports

#> Header
base_patterns = {
    'word': r'\w',
    'number': r'\d',
    'wordnum': r'(?~word)|(?~number)',
}

pragma_patterns = {
    'pragma.start': r'^\$',
    'pragma.stop': r'$',
    'pragma.key': r'(?P<key>(?:(?~wordnum)|\.)+)',
    'pragma.delim': r':',
    'pragma.val': r'(?P<val>.*?)',
    'pragma.flags': r'(?m)',
    'pragma': r'(?~pragma.flags)(?~pragma.start)(?~pragma.key)(?~pragma.delim)(?~pragma.val)(?~pragma.stop)',
}
#</Header

#> Main >/
# Create parser and add `base_patterns` and `pragma_patterns`
p = regex_compose.PatternComposer()
p.multiadd(base_patterns)
p.multiadd(pragma_patterns)

print(f'Pragma pattern: {rc.patterns["pragma"]}\n -> {rc.compiled["pragma"]}')
while True:
    inp = input('Enter text to parse > ')
    if m := re.match(p['pragma'], inp):
        rc.add(m.group('key'), m.group('val'), replace=True)
        print(p.compiled['pragma'])
    else: print(inp) # echo the line back when there's no pragma
```

> `Pragma pattern: (?~pragma.flags)(?~pragma.start)(?~pragma.key)(?~pragma.delim)(?~pragma.val)(?~pragma.stop)`
>> `test`

> `test`
>> `$pragma.start:%`

> `(?m)%(?P<key>(?:\w|\d|\.)+):(?P<val>.*?)$`
>> `%pragma.stop:;`

> `(?m)%(?P<key>(?:\w|\d|\.)+):(?P<val>.*?);`
>> `(?m)%(?P<key>(?:\w|\d|\.)+)=(?P<val>.*?);`

> `(?m)%(?P<key>(?:\w|\d|\.)+)=(?P<val>.*?);`

For further examples, see [https://codeberg.org/Shae/RegExCompose/src/branch/main/examples](https://codeberg.org/Shae/RegExCompose/src/branch/main/examples)

# Links
- Source code: [https://codeberg.org/Shae/RegExCompose](https://codeberg.org/Shae/RegExCompose)
- License: [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)
