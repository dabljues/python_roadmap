# Python roadmap

## Language

### Basics

* builtin types
  * ints, strings, floats and so on
  * tuples
    * [namedtuple](https://docs.python.org/3/library/collections.html#collections.namedtuple)
  * lists
  * dictionaries
    * very widely used - one has to have a good knowledge of them
    * mutability, objects as keys, hashing
    * [defaultdict](https://docs.python.org/3/library/collections.html#collections.defaultdict)
* functions
  * functions as first-class objects
  * lambdas
  * `*args`, `**kwargs`
  * default function parameters
    * mutable default function arguments (like `def foo(bar=[])`)
* classes
  * `__init__` and `__new__` methods
  * other dunder/magic methods (`__<something>__`)
  * inheritance
    * MRO (method resolution order)
  * `@staticmethod`, `@classmethod`, `@property`
  * private/protected attributes and methods (spoiler alert: there are none)
* string formatiing
  * ["".format()](https://docs.python.org/3/tutorial/inputoutput.html#the-string-format-method) (old)
  * [f-strings](https://docs.python.org/3/tutorial/inputoutput.html#the-string-format-method) (new, better)
  * raw strings ()
* basic I/O on files
* [builtins](https://docs.python.org/3/library/functions.html) - the more you know the better, but most importantly:
  * filters like `all()`, `any()`, `filter()`
  * conversions like: `int()` or `dict()`
  * methods decorators like `classmethod()`, `staticmethod()`, `property()`
  * iterators - `iter()`, `next()`
  * `abs()`
  * `bool()`
  * `enumerate()` - stop doing `for x in range(10): tab[x] = y`
  * `input()`
  * `len()`
  * `print()`
  * `range()`
  * `sorted()`
  * `type()`
  * `zip()`
* most used libs from the [standard library](https://docs.python.org/3/library/)
  * [json](https://docs.python.org/3/library/json.html) - used for reading/parsing jsons (JSONs are dictionaries in Python, there's no difference, no `Newtonsoft.Json`)
    * same goes for `yaml` and `toml`, it's just good to know how to read/save a file in those formats
  * [functools](https://docs.python.org/3/library/functools.html) - operations on callable objects
  * [collections](https://docs.python.org/3/library/collections.html) - many useful collections
  * [datetime](https://docs.python.org/3/library/datetime.html) - dates manipulation
  * [enum](https://docs.python.org/3/library/enum.html) - for enums
  * [math](https://docs.python.org/3/library/math.html)
  * [random](https://docs.python.org/3/library/random.html)
  * [pathlib](https://docs.python.org/3/library/pathlib.html) - very useful for path manipulations, operating on filepaths
    * theres also [os.path](https://docs.python.org/3/library/os.path.html) - older solution
  * [os](https://docs.python.org/3/library/os.html) - interface with OS
  * [time](https://docs.python.org/3/library/time.html)
    * 99% of people just use `time.sleep`
  * and many more (you kinda learn about them when you Google stuff)

### Intermediate (?) - just deeper into the language

* mutability in Python
  * what's mutable, what's not
  * can you override it?
* [typing](https://docs.python.org/3/library/typing.html) (types in python)
  * very important in modern codebases
  * not mandatory, it's just a hint to type checkers
* [dataclasses](https://docs.python.org/3/library/dataclasses.html)
  * almost like structures, but with functions
  * many goodies that regular classes don't have
  * used very very often
* decorators
  * how to create them
  * decorators accepting argumnets
* Python's [GIL](https://wiki.python.org/moin/GlobalInterpreterLock)
  * how to do concurrency or parallelism in Python
    * [threading](https://docs.python.org/3/library/threading.html)
    * [multiprocessing](https://docs.python.org/3/library/multiprocessing.html)
  * thread vs process (in general, but in Python as well)
* [regexes](https://docs.python.org/3/library/re.html)
  * everybody has to know regexes, but learn the search methods and flags in python
* generics and protocols
  * most people don't use generic in python
  * most people use inheritance instead of protocols
    * but protocols are better, they're just new
* Python's directory structure
  * available on the internet, most popular is something like this
  * `<app_name>/` - repo
    * `<app_name>/` - all code is in one folder, unless it's a monorepo (also checkout `<app_name>/` vs `src/<app_name>/`)
      * `__init__.py`
      * `__main__.py` - doesn't have to be that
      * `package1/`
        * `module1.py`
      * `package2/`
    * `tests/` - where the tests go
    * (optionally) - `docs`, `devops`, `assets` etc.
    * `.gitignore`
    * `setup.cfg`/`setup.py`
    * `requirements.txt`
* model libraries (creating ORMs or simple ordinary classes for validation in code)
  * [pydantic](https://pydantic-docs.helpmanual.io/) - used in FastAPI, very popular
  * [marshmallow](https://marshmallow.readthedocs.io/en/stable/) - very good for data validation

## Frameworks/libraries

### Backend

* [Django](https://www.djangoproject.com/) - the oldest, most popular
* [Flask](https://flask.palletsprojects.com/en/2.2.x/) - small, easier to learn, but less capable, less feature-packed
* [FastAPI](https://fastapi.tiangolo.com/) - the newest and arguably the best, not bloated, fully capable

### Data science

* [pandas](https://pandas.pydata.org/) - operating on datasets like CSVs, JSONs, you name it
* [numpy](https://numpy.org/) - basically algebra, operations on arrays, vectors
* [scipy](https://scipy.org/) - contains numpy and other scientific tools

You kinda need all those above. ML is probably either tensorflow, pytorch or scikit-learn, but I don't know about it.

## Development tools

* VS Code - language server and plugins, arguably the best
* [virtualenv](https://docs.python.org/3/tutorial/venv.html)
  * must have, don't install packages globally
* Linters
  * mandatory (kinda)
    * [mypy](https://github.com/python/mypy) - typing
    * [flake8](https://flake8.pycqa.org/en/latest/) + [wps](https://github.com/wemake-services/wemake-python-styleguide) (and other plugins if you want) - code style
    * [black](https://github.com/psf/black) - formatiing
    * [pytest](https://docs.pytest.org/en/7.1.x/) - tests, please for the love of merciful god don't use unittest (except for `unittest.mock`) - btw this is used by many testers to test other applications
  * optional
    * doctest
    * hypothesis
    * whatever you like
* [tox](https://tox.wiki/en/latest/index.html) - running CI
* [pyenv](https://github.com/pyenv/pyenv) - multiple python versions in one system
* [setup.py](https://docs.python.org/3/distutils/setupscript.html) vs [setup.cfg](https://docs.python.org/3/distutils/configfile.html)
* [requirements.txt](https://pip.pypa.io/en/stable/reference/requirements-file-format/)
* [pyproject.toml](https://pip.pypa.io/en/stable/reference/build-system/pyproject-toml/) - new, but will become a standard in the language and most of the libs
