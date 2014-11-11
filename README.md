Template
================

This is a template for Course Hero open source projects. 
It contains the standard files needed to get started to make a
new open source project. This is designed primarily for internal
use to bring Course Hero engineers up to speed on our best practices
and procedures for creating open source software, however it is
hopefully also useful in a general sense.

Getting Started
---------------

### Package Name ###

Your package name should reflect the scope of your project.
Try to make sure your project is generally useful, without being too
generally defined.

Make sure your work has a clear boundry. If the core of your code is
useful as a general PHP library make a general PHP library and a 
seperate project to wrap that in a Symfony Bundle

### Namespace ###

All namespaces should begin with CourseHero, followed by the package
name. If your package is FooWidget your namespace would be 
CourseHero\FooWidgets

### Tests ###

Make sure all code is tested with unit and/or functional tests.
Symfony2 recommends bundles have 95% code coverage. Try to maintain
good coverage but don't do silly things just to cap out coverage
metrics.

Folders
---------------

### src ###

The primary code of your package should be in the src directory. This
should also be the start of your psr-0 autoload path, as a result the
structure after src should contain a folder called CourseHero and
then a folder with your package name.

For example if you had a AwesomeWidget class in your FooWidgets
project and it's namespace was CourseHero\FooWidgets\AwesomeWidget
it would be located at src/CourseHero/FooWidgets/AwesomeWidget.php

### tests ###

This is where your tests for your project are housed. In the testing
bootstrap this is set up as another autoload point for psr-0 so if
you need to create helper files for testing they can be referenced
here.

### docs ###

This folder is gitignored however it contains output from running
tests. Code coverage is output in an html format, as well as in a 
format for coveralls.


Files
---------------

### README.md ###

This file should contain information about your project.
This should have a brief clear instruction on the purpose
of the project, how to install it, and how to use it.

This file should also contain travis-ci and coveralls badges:

[![Build Status](https://travis-ci.org/course-hero/template.svg?branch=master)](https://travis-ci.org/course-hero/template) [![Coverage Status](https://img.shields.io/coveralls/course-hero/template.svg)](https://coveralls.io/r/course-hero/template?branch=master)

### .coveralls.yml ###

This file contains configuration for coveralls. As long as PHPUnit
settings are the default this file should not need to be changed.

### .gitignore ###

A basic list of files to ignore. This file only needs to be changed
if your project includes additional output that should not be
included in the repository

### .travis.yml ###

The default configuration for travis-ci. This file will need to be
changed if your project does not work in certain environments.
By default this includes building on PHP 5.3 - PHP 5.6 as well as
hhvm.

If your project will not build in those configurations you may need
to exclude certain versions of PHP or allow them to fail by adding
a section similar to this to .travis.yml

```yml
matrix:
  allow_failures:
    - php: hhvm
    - php: 5.3
```

This will allow the build to fail in those configurations. If the
environment is one you'd like to ultimately support it is worthwhile
to keep the build in travis, but allow it to fail. If however you do
not plan on supporting that environment you can remove it from the
build. In general I would keep hhvm on your build lists. While we
do not currently use hhvm at Course Hero it helps gauge compatiblity

### composer.json ###

This is the base composer.json file. You will need to update the
name, description, authors and any requirements your file has.

Also make sure to update the autoload for your package, replacing
CourseHero\\Template with your actual package namespace

### CONTRIBUTING.md ###

This file contains directions on how to contribute to our open
source projects. This is based on the contributing instructions for
symfony. The wording has been made as generic as possible but be sure
to find all usages of the word 'template' and replace it with your
package name

### install.sh ###

This is a file that can be run to do a composer install and run tests
on a fresh pull of your project. As long as you are using standard
composer and phpunit settings this file should not need to be
modified.

### LICENSE ###

This contains the standard Apache2 License. This should not need
to be changed.

### phpunit.sh ###

This is a helper script for running tests. You can run it from the
command line once the php dependency has been installed

```bash
$ ./phpunit.sh
```

### phpunit.xml.dist ###

This is the base php unit configuration. You will have to update the
test suite name.

### tests/bootstrap.php ###

This is the phpunit bootstrap file that is loaded before tests run.
Replace CourseHero\\Template with the namespace to your package