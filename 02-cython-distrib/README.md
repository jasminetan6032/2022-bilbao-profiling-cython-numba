This is a very simple package that uses Cython.
It shows how to "package" a Python package with compiled sources.

The source code is just the `.pyx` file (`integrate_f6.pyx`).

The other files are "metadata":

- [pyproject.toml](02-cython-distrib/pyproject.toml)
- [meson.build](02-cython-distrib/meson.build)
- [setup.py](02-cython-distrib/setup.py)

Exercise: install the module so that it can be imported from anywhere:

    cd /
    python -c 'import integrate_f6; print(integrate_f6)'

--

The "new" way is to use `pip`:

    pip install --user .

To just build a distributable bundle:

    pip wheel .

This creates a binary "wheel" (zip archive) in dist/ .

--

The "old" way is to use setup.py:

    python setup.py build

or

    python setup.py build_ext --inplace

to compile the code.

Load the resulting module in the python interpreter.
Call the `integrate_f6()` function.

--

Optionally:

`meson` can also be invoked without `pip`:

    meson build-meson
    meson compile -C build-meson

This builds a module (underneath `build-meson/`), but does not put it the Python module search path.