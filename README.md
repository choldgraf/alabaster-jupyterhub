# alabaster-jupyterhub

[![PyPI version](https://badge.fury.io/py/alabaster_jupyterhub.svg)](https://pypi.org/project/alabaster_jupyterhub/)

A Sphinx theme used by the JupyterHub org projects. It is a slight modification
of the Alabaster theme.

## Installation

```
pip install alabaster_jupyterhub
```

## Configuration

In `conf.py`, add the following lines:

```
import alabaster_jupyterhub

...

html_theme = 'alabaster_jupyterhub'
html_theme_path = [alabaster_jupyterhub.get_html_theme_path()]

...

# If you have a RTD check, make sure to set theme
on_rtd = os.environ.get('READTHEDOCS', None) == 'True'
if not on_rtd:
    html_theme = 'alabaster_jupyterhub'
    html_theme_path = [alabaster_jupyterhub.get_html_theme_path()]
```

## Making a release

In general, we try to keep the JupyterHub repositories matched to "master" of
this repository. Since the documentation for all repositories are done with
readthedocs via pip, this means releasing new versions of alabaster-jupyterhub
fairly often.

alabaster-jupyterhub uses [the flit package](https://flit.readthedocs.io/en/latest)
for creating new releases. The version of the package is located in the `_version.py` file.

To create a new release, follow these instructions:

1. Ensure that all desired changes are merged into master
2. **Remove the `"dev0"` from the version**. This is in `_version.py`. Then make a
   PR and merge it.
3. Use `flit` to publish a new version of the package to pip. `cd` into the root
   of the repository and then:

   ```
   flit publish
   ```
4. Confirm that the new version of the package is [on the PyPI page](https://pypi.org/project/alabaster_jupyterhub/)
5. Bump the version number in `_version.py` and add the `"dev0"` back in.
   Make a PR and merge it into master.

That's it!