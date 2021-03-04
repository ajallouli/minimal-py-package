# Minimal package (python)

## 1. Setting the env
```sh
# creation of the virtual env
python -m venv env

# activation of the virtual env
env\Scripts\activate  # (Win10)

# upgrading pip
python -m pip install --upgrade pip

# listing the packages
pip list
```


# 2. Picking A Name
Python module/package names should generally follow the following constraints:
* All lowercase
* Unique on pypi, even if you don’t want to make your package publicly available (you might want to specify it privately as a dependency later)
* Underscore-separated or no word separators at all (don’t use hyphens)

We’ve decided to turn our bit of code into a module called funniest.

# 3. Creating The Scaffolding
The initial directory structure for funniest should look like this:
```
funniest/
    funniest/
        __init__.py
    setup.py
```

For starters we’ll put the `joke()` function in `__init__.py`, so it just contains:

```py
# __init__.py
def joke():
    return (u'Wenn ist das Nunst\u00fcck git und Slotermeyer? Ja! ... '
            u'Beiherhund das Oder die Flipperwaldt gersput.')
```

The main setup config file, `setup.py`, should contain a single call to `setuptools.setup()`, like so:

```py
from setuptools import setup

setup(name='funniest',
      version='0.0.1',
      description='The funniest joke in the world',
      url='http://github.com/storborg/funniest',
      author='Mohamed Amine Jallouli',
      author_email='jallouli.med.amine@gmail.com',
      license='MIT',
      packages=['funniest'],
      zip_safe=False)
```

Now we can install the package locally (for use on our system), with:
```sh
pip install .
```

We can also install the package with a symlink, so that changes to the source files will be immediately available to other users of the package on our system:

```sh
pip install -e .
```

Anywhere else in our system using the same Python, we can do this now:
```py
>>> import funniest
>>> funniest.joke()
```
