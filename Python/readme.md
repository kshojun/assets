# Manipulaton of string
```python
a = 'hello python'
```  

# len(a)
```12```

# a[0]
```'h'```

# a[-1]
```'n'```

# a[6:12]
```'python'```

# a*2
```'hello pythonhello python'```

# concat
```'hello' + ' ' + 'world' -> 'hello world'```

# formatting
```'one {} {} four'.format('two', 'three') -> 'one two three four'```  
```'{first:d} two {three:d}'.format(first=1, three=3) -> '1 two 3'```

- soft tab(space 4つ)が推奨されている  

# single comment
```# this is comment```  

# multiple comment
```python
"""
this
is
comment
"""
```

# writing in multiple lines
```
print("""
a
b
c
"""
)
```

# Data Types
int  3  
float  3.4  
string  "mozi"  
typeはtype関数で調べる

# Casting
flaot("3.4") floatに変換
int("4") intに変換
str(3.444) stringに変換

# List(Mutable)
```list = ["a", "b", "c"]```  
```list[0] = "d"```

# Taple(Immutable)
```taple = ("sunday", "monday")```  
```taple[0] -> "sunday"```

# Import Modules
```python
import calendar, math

cal = calendar.TextCalendar()
cal.prmonth(2019,11)
```

# Shortened Style of import module
```python
from calendar import TextCalendar

cal = TextCalendar()
```
のように短く書ける
