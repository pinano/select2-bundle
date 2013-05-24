# Select2 Bundle for Symfony2

## Current Version

Select2 3.4.0 (73)

## Installation

### Add bundle to your composer.json file

``` js
// composer.json

{
    "require": {
        // ...
        "pinano/select2-bundle": "dev-master"
    }
}
```

### Or, if you prefer, choose a specific version

``` js
// composer.json

{
    "require": {
        // ...
        "pinano/select2-bundle": "3.4.0"
    }
}
```

### Add bundle to your application kernel

``` php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Pinano\Select2Bundle\PinanoSelect2Bundle(),
        // ...
    );
}
```

### Download the bundle using Composer

``` bash
$ php composer.phar update pinano/select2-bundle
```

### Install assets

Given your server's public directory is named "web", install the public vendor resources

``` bash
$ php app/console assets:install web
```

Optionally, use the --symlink attribute to create links rather than copies of the resources

``` bash
$ php app/console assets:install --symlink web
```

Notes: All the urls of the original routes have been changed to '../images/*' due to Bundle package requirements.

## Usage

Once you have imported all the resources to the vendor folder, you can self-import the JS into your Symfony project as usual with:

``` twig
{# block js #}
{% block javascripts %}
    {% javascripts filter='cssrewrite' output='js/base.js'
        ...
        '@PinanoSelect2Bundle/Resources/public/js/select2.min.js'
        '@PinanoSelect2Bundle/Resources/public/js/select2_locale_XX.js'
        ...
        %}
        <script src="{{ asset_url }}"></script>
    {% endjavascripts %}
{% endblock %}
```

And with the CSS as well using with:
``` twig

{# block css #}
{% block stylesheets %}
    {% stylesheets filter='cssrewrite' output='css/base.css'
        ...
        'bundles/pinanoselect2/css/select2.css'
        ...
        %}
        <link rel="stylesheet" type="text/css" media="screen" href="{{ asset_url }}" />
    {% endstylesheets %}
{% endblock %}
```
Note: See https://github.com/kriswallsmith/assetic/issues/53 for known limitations of assetic with CSS referencing.

## Licenses

I do not own Select2 files at all, I'm just providing a Bundle package to easy-install them all. Refer to the source code of the included files from Select2 for license information.

## References

1. http://ivaynberg.github.io/select2/
2. http://symfony.com
