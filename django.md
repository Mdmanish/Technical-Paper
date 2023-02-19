# Django Technical Paper

## Settings file

### what is secret key

Secret key is a unique identification key of the project provided by Django.
A secret key for a particular Django installation. This is used to provide cryptographic signing, and should be set to a unique, unpredictable value.

django-admin startproject automatically adds a randomly-generated SECRET_KEY to each new project.

Uses of the key shouldn’t assume that it’s text or bytes. Every use should go through force_text() or force_bytes() to convert it to the desired type.

Django will refuse to start if SECRET_KEY is not set.

The secret key is used for:

    All sessions if you are using any other session backend than django.contrib.sessions.backends.cache, or are using the default get_session_auth_hash().
    All messages if you are using CookieStorage or FallbackStorage.
    All PasswordResetView tokens.
    Any usage of cryptographic signing, unless a different key is provided.

The default settings.py file created by django-admin startproject creates a unique SECRET_KEY for convenience.

#### Generating a Django SECRET_KEY

To generate a new key, we can use the get_random_secret_key() function present in django.core.management.utils. This function returns a 50 character string that consists of random characters. This string can be used as a SECRET_KEY.

```python

    from django.core.management.utils import get_random_secret_key
    # generating and printing the SECRET_KEY
    print(get_random_secret_key())

```

### what are the default Django apps inside it?Are there more?

Following are default django apps:

django.contrib.admin – The admin site.
django.contrib.auth – An authentication system.
django.contrib.contenttypes – A framework for content types.
django.contrib.sessions – A session framework.
django.contrib.messages – A messaging framework.
django.contrib.staticfiles – A framework for managing static files.

Some of these applications make use of at least one database table, though, so we need to create the tables in the database before we can use them.

Default applications are included for the common case, but not everybody needs them. If we don’t need any or all of them, we can comment-out or delete the appropriate line(s) from INSTALLED_APPS before running migrate. The migrate command will only run migrations for apps in INSTALLED_APPS.

### What is middleware? What are different kinds of middleware? Read up a little on each security issue

Middleware is like a middle ground between a request and response. It is like a window through which data passes. As in a window, light passes in and out of the house. Similarly, when a request is made it moves through middlewares to views, and data is passed through middleware as a response.

Here are the default middlewares installed in Django.

Security Middleware
Session Middleware
Common Middleware
Csrf View Middleware
Authentication Middleware
Message Middleware
XFrame Options Middleware

### Read up on Django Security

Django has some built-in features that handle user-submitted data to make it safe for an application. These features escape possible dangerous characters in requests, making the data safe for the application to use.The first rule of web application security is to never trust user-submitted data. Of course, the majority of the data you receive from the user side will be legit and safe. But an attacker can also maliciously craft data to damage your application or system. For example, if your application uses a SQL database and executes queries based on user input, a malicious actor can craft input that executes a query it's not supposed to. And malicious data from the user side means more than data entered in user input fields, like in forms. An attacker can also manipulate web requests, and Django’s got that covered too. Django contains clickjacking protection in the form of the X-Frame-Options middleware which, in a supporting browser, can prevent a site from being rendered inside a frame.

### CSRF (Cross site request forgery)

Cross-site request forgery (also known as CSRF) is a web security vulnerability that allows an attacker to induce users to perform actions that they do not intend to perform. It allows an attacker to partly circumvent the same origin policy, which is designed to prevent different websites from interfering with each other.

#### What is the impact of a CSRF attack?

In a successful CSRF attack, the attacker causes the victim user to carry out an action unintentionally. For example, this might be to change the email address on their account, to change their password, or to make a funds transfer. Depending on the nature of the action, the attacker might be able to gain full control over the user's account. If the compromised user has a privileged role within the application, then the attacker might be able to take full control of all the application's data and functionality.

### XSS (Cross site scripting)

Cross-site scripting (also known as XSS) is a web security vulnerability that allows an attacker to compromise the interactions that users have with a vulnerable application. It allows an attacker to circumvent the same origin policy, which is designed to segregate different websites from each other. Cross-site scripting vulnerabilities normally allow an attacker to masquerade as a victim user, to carry out any actions that the user is able to perform, and to access any of the user's data. If the victim user has privileged access within the application, then the attacker might be able to gain full control over all of the application's functionality and data.

#### How does XSS work?

Cross-site scripting works by manipulating a vulnerable web site so that it returns malicious JavaScript to users. When the malicious code executes inside a victim's browser, the attacker can fully compromise their interaction with the application.

### Click Jacking

Clickjacking, also known as a “UI redress attack”, is when an attacker uses multiple transparent or opaque layers to trick a user into clicking on a button or link on another page when they were intending to click on the top level page. Thus, the attacker is “hijacking” clicks meant for their page and routing them to another page, most likely owned by another application, domain, or both.

Using a similar technique, keystrokes can also be hijacked. With a carefully crafted combination of stylesheets, iframes, and text boxes, a user can be led to believe they are typing in the password to their email or bank account, but are instead typing into an invisible frame controlled by the attacker.

#### Defending against Clickjacking

There are three main ways to prevent clickjacking:

* Sending the proper Content Security Policy (CSP) frame-ancestors directive response headers that instruct the browser to not allow framing from other domains. The older X-Frame-Options HTTP headers is used for graceful degradation and older browser compatibility.
* Properly setting authentication cookies with SameSite=Strict (or Lax), unless they explicitly need None (which is rare).
* Employing defensive code in the UI to ensure that the current frame is the most top level window.

### What is Web Server Gateway Interface(WSGI)

WSGI is a specification that describes the communication between web servers and Python web applications or frameworks. It explains how a web server communicates with python web applications/frameworks and how web applications/frameworks can be chained for processing a request.

A mediator is required for carrying out the interaction between the web servers and the Python application. So, the standard for carrying out communication between the web server and Python application is WSGI(Web Server Gateway Interface).

## Models file

### what is ondelete cascade

The on_delete is one of the parameter which helps to perform database-related task efficiently. This parameter is used when a relationship is established in Django. The on_delete parameter allows us to work with the foreign key.

It is clear that whenever the foreign key concept comes into the scenario, the on_delete parameter is expected to be declared as one among the parameters in the foreign key.

This parameter decides whether deletion must happen. It tells what to do when a parent value is deleted. This option allows the extent of flexibility to the database-oriented operations.

Syntax of Django on_delete

```python
    field name = models.ForeignKey(WASD, on_delete = OPERATION TYPE)
```

The on_delete includes the following options -

    CASCADE
    PROTECT
    SET_NULL
    SET_DEFAULT
    SET()
    DO_NOTHING

### A broad understanding of Fields and Validators available to you

Fields: in Django are the data types to store a particular type of data. For example, to store an integer, IntegerField would be used. These fields have in-built validation for a particular data type, that is you can not store “abc” in an IntegerField. Similarly, for other fields. This post revolves around major fields one can use in Django Models.

#### Field types

Each field in the model should be an instance of the appropriate Field class. Django uses field class types to determine a few things:

* The column type, which tells the database what kind of data to store (e.g. INTEGER, VARCHAR, TEXT).
* The default HTML widget to use when rendering a form field
* The minimal validation requirements, used in Django’s admin and in automatically-generated forms.Here is a list of all Field types used in Django.  

AutoField: It is an IntegerField that automatically increments.

BigAutoField: It is a 64-bit integer, much like an AutoField except that it is guaranteed to fit numbers from 1 to 9223372036854775807.

BigIntegerField: It is a 64-bit integer, much like an IntegerField except that it is guaranteed to fit numbers from -9223372036854775808 to 9223372036854775807.

BinaryField: A field to store raw binary data.

BooleanField: A true/false field.

CharField: A field to store text-based values.

DateField: A date, represented in Python by a datetime.date instance

DateTimeField: It is used for date and time, represented in Python by a datetime.datetime instance.

DecimalField: It is a fixed-precision decimal number, represented in Python by a Decimal instance.

DurationField: A field for storing periods of time.

EmailField: It is a CharField that checks that the value is a valid email address.

FileField: It is a file-upload field.

FloatField: It is a floating-point number represented in Python by a float instance.

ImageField: It inherits all attributes and methods from FileField, but also validates that the uploaded object is a valid image.

IntegerField: It is an integer field. Values from -2147483648 to 2147483647 are safe in all databases supported by Django.

GenericIPAddressField: An IPv4 or IPv6 address, in string format

Validator A validator is a computer program used to check the validity or syntactical correctness of a fragment of code or document.Validators can be used in Django in the models level or the level of the form.
These validators are responsible for validating a field. The validators help to analyse the nature of the field with the value filled in the field.
More importantly, these validators adjudicate the data being passed and post the errors onto the screen. This is the key benefit of Django validators. The Django validators can be done using methods such as clean() or even using field-level validators. It depends on the validator message used.

Syntax:

```py
    Raise validationerror(“”)
```

The process of raising a validation error is taken place through validators. This can be archived by means of the validation error exception, which can be raised at a form level and even at a field level. Here using this will raise the error and display it onto the console. The message which is expected to be raised has to be placed inbetween the double-quotes. The value between the double quotes will be displayed as the message associated to the error.

Methods like clean() or even clean_fieldname can be used for raising these validation based errors. The validation errors can also be used to check all types of fields used across the forms section. The error message alerted onto the screen from the syntax will be very useful in determining the type of message being printed.

### Understanding the difference between Python module and Python class?

Classes are blueprints that allow you to create instances with attributes and bound functionality. Classes support inheritance, metaclasses, and descriptors.

Modules can't do any of this, modules are essentially singleton instances of an internal module class, and all their globals are attributes on the module instance. You can manipulate those attributes as needed (add, remove and update), but take into account that these still form the global namespace for all code defined in that module.

From a Java perspective, classes are not all that different here. Modules can contain more than just one class however; functions and any the result of any other Python expression can be globals in a module too.

So as a general ballpark guideline:

    Use classes as blueprints for objects that model your problem domain.
    Use modules to collect functionality into logical units.

Then store data where it makes sense to your application. Global state goes in modules (and functions and classes are just as much global state, loaded at the start). Everything else goes into other data structures, including instances of classes.

## Django ORM

### Using ORM queries in Django Shell

#### What is a QuerySet?

A QuerySet is, in essence, a list of objects of a given Model. QuerySets allow you to read the data from the database, filter it and order it.

#### Django shell

Open up your local console (not on PythonAnywhere) and type this command:

python manage.py shell

You're now in Django's interactive console. It's just like the Python prompt, but with some additional Django magic. :) You can use all the Python commands here too.

#### Creating objects

To represent database-table data in Python objects, Django uses an intuitive system: A model class represents a database table, and an instance of that class represents a particular record in the database table.

To create an object, instantiate it using keyword arguments to the model class, then call save() to save it to the database.

Assuming models live in a file mysite/blog/models.py, here’s an example:

```py
    from blog.models import Blog
    b = Blog(name='Beatles Blog', tagline='All the latest Beatles news.')
    b.save()
```

This performs an INSERT SQL statement behind the scenes. Django doesn’t hit the database until you explicitly call save().

The save() method has no return value.

#### Saving changes to objects

To save changes to an object that’s already in the database, use save().

Given a Blog instance b5 that has already been saved to the database, this example changes its name and updates its record in the database:

```py
    b5.name = 'New name'
    b5.save()
```

This performs an UPDATE SQL statement behind the scenes. Django doesn’t hit the database until you explicitly call save().

#### Saving ForeignKey and ManyToManyField fields

Updating a ForeignKey field works exactly the same way as saving a normal field – assign an object of the right type to the field in question. This example updates the blog attribute of an Entry instance entry, assuming appropriate instances of Entry and Blog are already saved to the database (so we can retrieve them below):

```py
from blog.models import Blog, Entry
entry = Entry.objects.get(pk=1)
cheese_blog = Blog.objects.get(name="Cheddar Talk")
entry.blog = cheese_blog
entry.save()
```

Updating a ManyToManyField works a little differently – use the add() method on the field to add a record to the relation. This example adds the Author instance joe to the entry object:

```py
from blog.models import Author
joe = Author.objects.create(name="Joe")
entry.authors.add(joe)
```

To add multiple records to a ManyToManyField in one go, include multiple arguments in the call to add(), like this:

```py
john = Author.objects.create(name="John")
paul = Author.objects.create(name="Paul")
george = Author.objects.create(name="George")
ringo = Author.objects.create(name="Ringo")
entry.authors.add(john, paul, george, ringo)
```

Django will complain if you try to assign or add an object of the wrong type.

#### Retrieving objects

To retrieve objects from your database, construct a QuerySet via a Manager on your model class.

A QuerySet represents a collection of objects from your database. It can have zero, one or many filters. Filters narrow down the query results based on the given parameters. In SQL terms, a QuerySet equates to a SELECT statement, and a filter is a limiting clause such as WHERE or LIMIT.

You get a QuerySet by using your model’s Manager. Each model has at least one Manager, and it’s called objects by default. Access it directly via the model class, like so:

```py
Blog.objects
<django.db.models.manager.Manager object at ...>
b = Blog(name='Foo', tagline='Bar')
b.objects
Traceback:
    ...
AttributeError: "Manager isn't accessible via Blog instances."
```

Managers are accessible only via model classes, rather than from model instances, to enforce a separation between “table-level” operations and “record-level” operations.

The Manager is the main source of QuerySets for a model. For example, Blog.objects.all() returns a QuerySet that contains all Blog objects in the database.

#### Retrieving all objects

The simplest way to retrieve objects from a table is to get all of them. To do this, use the all() method on a Manager:

```py
all_entries = Entry.objects.all()
```

The all() method returns a QuerySet of all the objects in the database.

#### Retrieving specific objects with filters

The QuerySet returned by all() describes all objects in the database table. Usually, though, you’ll need to select only a subset of the complete set of objects.

To create such a subset, you refine the initial QuerySet, adding filter conditions. The two most common ways to refine a QuerySet are:

filter(**kwargs)
    Returns a new QuerySet containing objects that match the given lookup parameters.
exclude(**kwargs)
    Returns a new QuerySet containing objects that do not match the given lookup parameters.

The lookup parameters (**kwargs in the above function definitions) should be in the format described in Field lookups below.

For example, to get a QuerySet of blog entries from the year 2006, use filter() like so:

Entry.objects.filter(pub_date__year=2006)

With the default manager class, it is the same as:

Entry.objects.all().filter(pub_date__year=2006)

#### Chaining filters

The result of refining a QuerySet is itself a QuerySet, so it’s possible to chain refinements together. For example:

```py
    Entry.objects.filter(
     headline__startswith='What'
 ).exclude(
     pub_date__gte=datetime.date.today()
 ).filter(
     pub_date__gte=datetime.date(2005, 1, 30)
 )
```

This takes the initial QuerySet of all entries in the database, adds a filter, then an exclusion, then another filter. The final result is a QuerySet containing all entries with a headline that starts with “What”, that were published between January 30, 2005, and the current day.

#### Filtered QuerySets are unique

Each time you refine a QuerySet, you get a brand-new QuerySet that is in no way bound to the previous QuerySet. Each refinement creates a separate and distinct QuerySet that can be stored, used and reused.

Example:

```py
q1 = Entry.objects.filter(headline__startswith="What")
q2 = q1.exclude(pub_date__gte=datetime.date.today())
q3 = q1.filter(pub_date__gte=datetime.date.today())
```

These three QuerySets are separate. The first is a base QuerySet containing all entries that contain a headline starting with “What”. The second is a subset of the first, with an additional criteria that excludes records whose pub_date is today or in the future. The third is a subset of the first, with an additional criteria that selects only the records whose pub_date is today or in the future. The initial QuerySet (q1) is unaffected by the refinement process.

#### QuerySets are lazy

QuerySets are lazy – the act of creating a QuerySet doesn’t involve any database activity. You can stack filters together all day long, and Django won’t actually run the query until the QuerySet is evaluated. Take a look at this example:

```py
q = Entry.objects.filter(headline__startswith="What")
q = q.filter(pub_date__lte=datetime.date.today())
q = q.exclude(body_text__icontains="food")
print(q)
```

Though this looks like three database hits, in fact it hits the database only once, at the last line (print(q)). In general, the results of a QuerySet aren’t fetched from the database until you “ask” for them. When you do, the QuerySet is evaluated by accessing the database. For more details on exactly when evaluation takes place, see When QuerySets are evaluated.

#### Retrieving a single object with get()

filter() will always give you a QuerySet, even if only a single object matches the query - in this case, it will be a QuerySet containing a single element.

If you know there is only one object that matches your query, you can use the get() method on a Manager which returns the object directly:

```py
one_entry = Entry.objects.get(pk=1)
```

You can use any query expression with get(), just like with filter() - again, see Field lookups below.

Note that there is a difference between using get(), and using filter() with a slice of [0]. If there are no results that match the query, get() will raise a DoesNotExist exception. This exception is an attribute of the model class that the query is being performed on - so in the code above, if there is no Entry object with a primary key of 1, Django will raise Entry.DoesNotExist.

Similarly, Django will complain if more than one item matches the get() query. In this case, it will raise MultipleObjectsReturned, which again is an attribute of the model class itself.

#### Other QuerySet methods

Most of the time you’ll use all(), get(), filter() and exclude() when you need to look up objects from the database. However, that’s far from all there is; see the QuerySet API Reference for a complete list of all the various QuerySet methods.

#### Limiting QuerySets

Use a subset of Python’s array-slicing syntax to limit your QuerySet to a certain number of results. This is the equivalent of SQL’s LIMIT and OFFSET clauses.

For example, this returns the first 5 objects (LIMIT 5):

Entry.objects.all()[:5]

This returns the sixth through tenth objects (OFFSET 5 LIMIT 5):

Entry.objects.all()[5:10]

Negative indexing [i.e. Entry.objects.all(](-1)) is not supported.

Generally, slicing a QuerySet returns a new QuerySet – it doesn’t evaluate the query. An exception is if you use the “step” parameter of Python slice syntax. For example, this would actually execute the query in order to return a list of every second object of the first 10:

Entry.objects.all()[:10:2]

Further filtering or ordering of a sliced queryset is prohibited due to the ambiguous nature of how that might work.

To retrieve a single object rather than a list (e.g. SELECT foo FROM bar LIMIT 1), use an index instead of a slice. For example, this returns the first Entry in the database, after ordering entries alphabetically by headline:

Entry.objects.order_by['headline'](0)

This is roughly equivalent to:

Entry.objects.order_by['headline'](0:1).get()

Note, however, that the first of these will raise IndexError while the second will raise DoesNotExist if no objects match the given criteria. See get() for more details.

#### Field lookups

Field lookups are how you specify the meat of an SQL WHERE clause. They’re specified as keyword arguments to the QuerySet methods filter(), exclude() and get().

Basic lookups keyword arguments take the form field__lookuptype=value. (That’s a double-underscore). For example:

Entry.objects.filter(pub_date__lte='2006-01-01')

translates (roughly) into the following SQL:

SELECT * FROM blog_entry WHERE pub_date <= '2006-01-01';

How this is possible

Python has the ability to define functions that accept arbitrary name-value arguments whose names and values are evaluated at runtime. For more information, see Keyword Arguments in the official Python tutorial.

The field specified in a lookup has to be the name of a model field. There’s one exception though, in case of a ForeignKey you can specify the field name suffixed with _id. In this case, the value parameter is expected to contain the raw value of the foreign model’s primary key. For example:

Entry.objects.filter(blog_id=4)

If you pass an invalid keyword argument, a lookup function will raise TypeError.

The database API supports about two dozen lookup types; a complete reference can be found in the field lookup reference. To give you a taste of what’s available, here’s some of the more common lookups you’ll probably use:

exact

An “exact” match. For example:

    Entry.objects.get(headline__exact="Cat bites dog")

Would generate SQL along these lines:

    SELECT ... WHERE headline = 'Cat bites dog';

If you don’t provide a lookup type – that is, if your keyword argument doesn’t contain a double underscore – the lookup type is assumed to be exact.

For example, the following two statements are equivalent:

    Blog.objects.get(id__exact=14)  # Explicit form
    Blog.objects.get(id=14)         # __exact is implied

This is for convenience, because exact lookups are the common case.
iexact

A case-insensitive match. So, the query:

    Blog.objects.get(name__iexact="beatles blog")

Would match a Blog titled "Beatles Blog", "beatles blog", or even "BeAtlES blOG".
contains

Case-sensitive containment test. For example:

Entry.objects.get(headline__contains='Lennon')

Roughly translates to this SQL:

SELECT ... WHERE headline LIKE '%Lennon%';

Note this will match the headline 'Today Lennon honored' but not 'today lennon honored'.

There’s also a case-insensitive version, icontains.
startswith, endswith
Starts-with and ends-with search, respectively. There are also case-insensitive versions called istartswith and iendswith.

#### The pk lookup shortcut

For convenience, Django provides a pk lookup shortcut, which stands for “primary key”.

In the example Blog model, the primary key is the id field, so these three statements are equivalent:

```py
Blog.objects.get(id__exact=14) # Explicit form
Blog.objects.get(id=14) # __exact is implied
Blog.objects.get(pk=14) # pk implies id__exact
```

The use of pk isn’t limited to __exact queries – any query term can be combined with pk to perform a query on the primary key of a model:

```py
# Get blogs entries with id 1, 4 and 7
Blog.objects.filter(pk__in=[1,4,7])

# Get all blog entries with id > 14
Blog.objects.filter(pk__gt=14)
```

pk lookups also work across joins. For example, these three statements are equivalent:

```py
Entry.objects.filter(blog__id__exact=3) # Explicit form
Entry.objects.filter(blog__id=3)        # __exact is implied
Entry.objects.filter(blog__pk=3)        # __pk implies __id__exact
```

### Turning ORM to SQL in Django Shell

To get the SQL query, we need to print or use the str() and pass the queryset object along with query.

```py
queryset = MyModel.objects.all()
print(queryset.query)
SELECT "myapp_mymodel"."id", ... FROM "myapp_mymodel"
```

### What are Aggregations?

Aggregation is “the collection of  related items of content so that they can be  displayed or linked to”. there are different situations that you will need to use Aggregation in Django.

Example:

for finding “maximum”, “minimum” value of column in database table in django models.
for finding “count” of records in database table based on a column.
for finding “average” value of a group of similar objects.
also for finding sum of values in a column.

In most of the cases we use aggregation on columns of data type “integer”, “float”, “date”, “datetime” etc.

essentially, aggregations are nothing but a way to perform an operation on group of rows. In databases, they are represented by operators as sum, avg etc. to do these operations Django added two new methods to querysets.

these two methods are aggregate and annotate. also we can tell that in sql terms, aggregate is a operation(SUM, AVG, MIN, MAX), without a group by, while annotate is a operation with a group by on rowset_table.id. (Unless explicitly overriden).

Get the number of totals books from your model like this.

from MyApp.models import Book

Book.objects.count()

Total number of books according to publication.

Book.objects.filter(publisher__name = 'Second')
<QuerySet [<Book: Python New Book>, <Book: Kotlin Book>]>  

Finding average price across all books.

from django.db.models import Avg

Book.objects.all().aggregate(Avg('price'))
{'price__avg': Decimal('121.25')}

Max price across all books.

from django.db.models import Max

Book.objects.all().aggregate(Max('price'))
{'price__max': Decimal('185')}

Finding min price for all books.

from django.db.models import Min

Book.objects.all().aggregate(Min('price'))
{'price__min': Decimal('50')}

Sum of prices for all books.

from django.db.models import Sum

Book.objects.all().aggregate(Min('price'))
{'price__min': Decimal('50')}

Also you can do multiple aggregation in a queryset.

Book.objects.aggregate(Avg('price'), Max('price'), Min('price'))

{'price__avg': Decimal('121.25'),
 'price__max': Decimal('185'),
 'price__min': Decimal('50')}

Listing all the publisher for the book using annotate.

from MyApp.models import Publisher

from django.db.models import Count

pubs = Publisher.objects.annotate(num_books=Count('book'))

pubs[0].num_books
3

### What are Annotations?

Annotate generate an independent summary for each object in a queryset. In simpler terms, annotate allows us to add a pseudo field to our queryset. This field can then further be used for filter lookups or ordering.

How Annotate Works?

The process in which annotate works is very simple and lean; it expects the model for which the annotation is performed and the aggregate function through which the annotation is going to be wrapped upon.
The annotate function allows the aggregate method to be encapsulated within it. The column which is going to be considered for annotation has to be declared within the aggregate function.
The column value will be expected to be enclosed within a pair of single quotations. In addition, the output of the annotate will be assigned to the annotated output variable, which can be flexibly used for identifying the output of the annotation.

Let’s now have a look at a simple annotation and its syntax.

Here we are asking for Provider records. For each provider, we’re adding the field circuit_count. That field will record a number of the circuits linked to each of the providers.

```py
    from django.db.models import Count

    providers = Provider.objects.annotate(circuit_count=Count("circuits"))
```

with order_by

providers = Provider.objects.annotate(circuit_count=Count("circuits")).order_by("-circuit_count")

Query to return only selected fields and their values. We’ll do this by appending the values() method.

```py
    providers = Provider.objects.annotate(circuit_count=Count("circuits")) \
    .order_by("-circuit_count") \
    .values("name", "circuit_count")
```

with filter

```py
    providers = Provider.objects.annotate(circuit_count=Count("circuits")) \
        .filter(circuit_count__gt=0) \
        .order_by("-circuit_count") \
        .values("name", "circuit_count")
    providers
    <RestrictedQuerySet [{'name': 'NTT', 'circuit_count': 40}, {'name': 'Telia Carrier', 'circuit_count': 40}]>
```

### What is a migration file? Why is it needed?

Migration files. Migrations are stored as an on-disk format, referred to here as “migration files”. These files are actually normal Python files with an agreed-upon object layout, written in a declarative style.

#### Why migration needed?

Migrations are Django's way of propagating changes you make to your models (adding a field, deleting a model, etc.) into your database schema. They're designed to be mostly automatic, but you'll need to know when to make migrations, when to run them, and the common problems you might run into.

#### The Commands

There are several commands which you will use to interact with migrations and Django’s handling of database schema:

    migrate, which is responsible for applying and unapplying migrations.
    makemigrations, which is responsible for creating new migrations based on the changes you have made to your models.
    sqlmigrate, which displays the SQL statements for a migration.
    showmigrations, which lists a project’s migrations and their status.

You should think of migrations as a version control system for your database schema. makemigrations is responsible for packaging up your model changes into individual migration files - analogous to commits - and migrate is responsible for applying those to your database.

The migration files for each app live in a “migrations” directory inside of that app, and are designed to be committed to, and distributed as part of, its codebase. You should be making them once on your development machine and then running the same migrations on your colleagues’ machines, your staging machines, and eventually your production machines.

### What are SQL transactions? (non ORM concept)

A transaction is a unit of work that is performed against a database. Transactions are units or sequences of work accomplished in a logical order, whether in a manual fashion by a user or automatically by some sort of a database program.

A transaction is the propagation of one or more changes to the database. For example, if you are creating a record or updating a record or deleting a record from the table, then you are performing a transaction on that table. It is important to control these transactions to ensure the data integrity and to handle database errors.

SQL Server can operate 3 different transactions modes and these are:

    Autocommit Transaction mode is the default transaction for the SQL Server. In this mode, each T-SQL statement is evaluated as a transaction and they are committed or rolled back according to their results. The successful statements are committed and the failed statements are rolled back immediately

    Implicit transaction mode enables to SQL Server to start an implicit transaction for every DML statement but we need to use the commit or rolled back commands explicitly at the end of the statements

    Explicit transaction mode provides to define a transaction exactly with the starting and ending points of the transaction

### What are atomic transactions?

An atomic transaction is the smallest set of operations to perform the required steps. Either all of those required operations happen(successfully) or the atomic transaction fails.

An atomic operation usually has nothing in common with transactions.

Django gives us a few ways to control how database transactions are managed. We mostly used transaction property into the transaction related queries. Each query is directly committed to the database unless a transaction is active cause of Django is run in auto-commit mode.

A transaction is an atomic set of database queries. These functions take a using argument which should be the name of a database. If it isn’t provided, Django uses the “default” database. Django will refuse to commit or to rollback when an atomic() block is active because that would break atomicity.
