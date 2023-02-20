<!--jjj-->
# Flask
![](https://miro.medium.com/max/438/1*0G5zu7CnXdMT9pGbYUTQLQ.png)

Flask is a web framework, used to developing web applications, create web API's and to create machine learning applications.

## POCOO style:

Flask uses POCOO style, which is almost similar to PEP8.

## Flask code readability

In flask code to make code easily understable readable, every where written proper comments which specifies about the method or class and given proper names to the variable, method and class to understand the code what the given method, class and variable is used to do.

### Naming Conventions
* Class names: CamelCase, with acronyms kept uppercase (HTTPWriter and not HttpWriter)

* Variable names: lowercase_with_underscores

* Method and function names: lowercase_with_underscores

* Constants: UPPERCASE_WITH_UNDERSCORES

* Module name: module.py, my_module.py

* Package name: package, mypackage(do not give underscore)


### In Flask code for giving indenatations in continuation lines, they given indent vertically and hanging indent.

```python
    default_config = ImmutableDict(
        {
            "ENV": None,
            "DEBUG": None,
            "TESTING": False,
            "PROPAGATE_EXCEPTIONS": None,
            "SECRET_KEY": None,
            "PERMANENT_SESSION_LIFETIME": timedelta(days=31),
            "USE_X_SENDFILE": False,
        }
    )
```

### No operators sit far away from their operands

```python
    def post(self):
        session["counter"] = session.get("counter", 0) + 1
        return redirect(url_for("counter"))
```