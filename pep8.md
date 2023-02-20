<!--hii-->
# PEP8 (Python Enhancement Proposal 8)
![](https://elpythonista.com/wp-content/uploads/2021/02/PEP_8_Eng.jpg)

### What is this PEP8 ?

To make pyhton code easily understable and readable by the other person or myself as well or to test the code, we have to follow some python standards. This PEP8 lets know about all these standards.

## Indentation

Indentation should be given by tab or 4 spaces. Do not mix tab and space in a single Indentation

If we have to write single line code in multiple lines then continuation lines should align wrapped elements either vertically or using a hanging indent.
## Yes

```python
# Aligned with opening delimiter.
foo = long_function_name(var_one, var_two,
                         var_three,var_four)

# More indentation included to distinguish this from the rest.
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)

# Hanging indents should add a level.
foo = long_function_name(
    var_one, var_two,
    var_three, var_four)
```
## No
```python
# Arguments on first line forbidden when not using vertical alignment.
foo = long_function_name(var_one, var_two,
    var_three, var_four)

# Further indentation required as indentation is not distinguishable.
def long_function_name(
    var_one, var_two, var_three,
    var_four):
    print(var_one)
```

## Should a line break before or after a binary operator?

```python
# No: operators sit far away from their operands
income = (gross_wages +
          taxable_interest +
          (dividends - qualified_dividends) -
          ira_deduction -
          student_loan_interest)


# Yes: easy to match operators with operands
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)

```

## Whitespace in Expressions and Statements

### Avoid extraneous whitespace in the following situations:

### Immediately inside parentheses, brackets or braces:

#### Yes:

```python
spam(ham[1], {eggs: 2})
```

#### No

```python
spam( ham[ 1 ], { eggs: 2 } )
```
### Between a trailing comma and a following close parenthesis:

#### Yes

```python
foo = (0,)
```

#### No

```python
bar = (0, )
```

### Immediately before a comma, semicolon, or colon:

#### Yes

```python
if x == 4: print x, y; x, y = y, x
```

#### No

```python
if x == 4 : print x , y ; x , y = y , x
```

### Immediately before the open parenthesis that starts an indexing or slicing:

#### Yes

```python
dct['key'] = lst[index]
```

#### No
```python
dct ['key'] = lst [index]
```
#### More than one space around an assignment (or other) operator to align it with another.


#### Yes

```python
x = 1
y = 2
long_variable = 3
```

#### No
```python
x             = 1
y             = 2
long_variable = 3
```

## Blank lines:
Top level functions and classes are separated by two lines, everything else by one. Do not use too many blank lines to separate logical segments in code. Example:

```python
    def hello(name):
    print 'Hello %s!' % name


    def goodbye(name):
        print 'See you %s.' % name


    class MyClass(object):
        """This is a simple docstring"""

        def __init__(self, name):
            self.name = name

        def get_annoying_name(self):
            return self.name.upper() + '!!!!111'

```




## Naming Conventions
The following naming styles are commonly distinguished:
* Class names: CamelCase, with acronyms kept uppercase (HTTPWriter and not HttpWriter)

* Variable names: lowercase_with_underscores

* Method and function names: lowercase_with_underscores

* Constants: UPPERCASE_WITH_UNDERSCORES

* Module name: module.py, my_module.py

* Package name: package, mypackage(do not give underscore)

Note: When using abbreviations in CapWords, capitalize all the letters of the abbreviation. Thus HTTPServerError is better than HttpServerError.

### Names to Avoid:
Never use the characters ‘l’ (lowercase letter el), ‘O’ (uppercase letter oh), or ‘I’ (uppercase letter eye) as single character variable names.

In some fonts, these characters are indistinguishable from the numerals one and zero. When tempted to use ‘l’, use ‘L’ instead.

### Function Names
Function names should be lowercase, with words separated by underscores as necessary to improve readability.

### Function and method arguments
Always use self for the first argument to instance methods.

Always use cls for the first argument to class methods.

If a function argument’s name clashes with a reserved keyword, it is generally better to append a single trailing underscore rather than use an abbreviation or spelling corruption. Thus class_ is better than clss. (Perhaps better is to avoid such clashes by using a synonym.)

### Docstrings

Docstring conventions:

If it’s just one line, the closing triple quote is on the same line as the opening, otherwise the text is on the same line as the opening quote and the triple quote that closes the string on its own line:

Docstring comment should be written after def.

```python
    def foo():
        """This is a simple docstring"""


    def bar():
        """This is a longer docstring with so much information in there
        that it spans three lines.  In this case the closing triple quote
        is on its own line.
        """
```
