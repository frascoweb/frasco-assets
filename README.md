# Frasco-Assets

Assets manager for Frasco using [webassets](http://webassets.readthedocs.org/en/latest/),
[Flask-Assets](http://flask-assets.readthedocs.org/en/latest/) and
[easywebassets]().

## Installation

    pip install frasco-assets

## Setup

Feature name: assets

Options of this feature are the same as [webassets options](http://webassets.readthedocs.org/en/latest/environment.html#configuration).

## Defining assets packages

You can create assets packages (using easywebassets) by defining them under the *ASSETS*
configuration key. This must be a hash where keys are package names and values a list
of assets.

```yaml
features:
  - assets
assets:
  jquery:
    - vendor/jquery.js
  default:
    - css/layout.css
    - js/app.js
```

## Current assets

Frasco-Assets maintain a default package available through `frasco_assets.current_assets`.
If you define a *default* package in your configuration, it will be automatically added to
the current assets.

```python
from frasco_assets import current_assets
current_assets.append('@jquery')
```

## Rendering assets

You can use the *assets* directive in your Jinja templates to render assets. Without
any arguments, this will render the current assets.

You can also use this directive to create packages on the fly.

    {% assets 'css/home.css', '@jquery' %}

## Commands

Webassets command are available through the *assets* command.

    $ frasco assets build
    $ frasco assets watch
    $ frasco assets clean
    $ frasco assets check