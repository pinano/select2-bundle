# Select2 Bundle for Symfony2

## Current Version

[Select2 4.0.1](https://select2.github.io/)

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
        "pinano/select2-bundle": "4.0"
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

## Usage

Once all the resources are in place you can edit any of your twig views or layouts to include the Select2
javascript files.

Select2 optionally supports multiple languages by simply including the right language javascript file 
(`i18n/es.js`, `i18n/fr.js`, etc.) after `select2.js`. In the following example we are loading the Spanish locale.

Note: Select2 requires the jQuery library.

``` twig
{% block javascripts %}
    <script src="//ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
    {% javascripts
        ...
        '@PinanoSelect2Bundle/Resources/public/js/select2.min.js'
        '@PinanoSelect2Bundle/Resources/public/js/i18n/es.js'
        ...
        %}
        <script src="{{ asset_url }}"></script>
    {% endjavascripts %}
{% endblock %}
```

Then you will want to load the css resources so your select elements look nice:

``` twig
{% block stylesheets %}
    {% stylesheets filter='cssrewrite'
      ...
      'bundles/pinanoselect2/css/select2.css'
      ...
    %}
        <link rel="stylesheet" href="{{ asset_url }}" />
    {% endstylesheets %}
{% endblock %}
```

Note: See https://github.com/kriswallsmith/assetic/issues/53 for known limitations of assetic with CSS referencing.

I usually follow a simple inheritance schema when it comes to designing twig templates. That is, I have an
app/Resources/views/base.html.twig file that I use as a site-wide template. Then, inside every bundle I have
my own Resources/views/layout.html.twig file that extends the base template. Depending on the kind of application
I'm designing I can place the Bootstrap stuff in the site-wide or the bundle-wide template. Then every view of a
given bundle will extend the corresponding bundle layout.html.twig file, which in turn extends the site-wide template.

The folks at Sensio Labs have already covered this approach and you can check it in their
[documentation](http://twig.sensiolabs.org/doc/templates.html#template-inheritance).

## Licenses

I do not own Select2 files at all, I'm just providing a Bundle package to easy-install them all.
Refer to the source code of the included files from Select2 for license information.

## References

1. https://select2.github.io/
2. http://symfony.com
