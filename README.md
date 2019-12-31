# mezzio

[![Build Status](https://travis-ci.org/mezzio/mezzio.svg?branch=master)](https://travis-ci.org/mezzio/mezzio)

*Begin developing PSR-7 middleware applications in minutes!*

mezzio builds on [laminas-stratigility](https://github.com/laminas/laminas-stratigility)
to provide a minimalist PSR-7 middleware framework for PHP, with the following
features:

- Routing. Choose your own router; we support:
    - [Aura.Router](https://github.com/auraphp/Aura.Router)
    - [FastRoute](https://github.com/nikic/FastRoute)
    - [Laminas's MVC router](https://github.com/laminas/laminas-mvc)
- DI Containers, via [container-interop](https://github.com/container-interop/container-interop).
  Middleware matched via routing is retrieved from the composed container.
- Optionally, templating. We support:
    - [Plates](http://platesphp.com/)
    - [Twig](http://twig.sensiolabs.org/)
    - [Laminas's PhpRenderer](https://github.com/laminas/laminas-view)

## Installation

We provide two ways to install Mezzio, both using
[Composer](https://getcomposer.org): via our
[skeleton project and installer](https://github.com/mezzio/mezzio-skeleton),
or manually.

### Using the skeleton + installer

The simplest way to install and get started is using the skeleton project, which
includes installer scripts for choosing a router, dependency injection
container, and optionally a template renderer and/or error handler. The skeleton
also provides configuration for officially supported dependencies.

To use the skeleton, use Composer's `create-project` command:

```bash
$ composer create-project -s rc mezzio/mezzio-skeleton <project dir>
```

This will prompt you through choosing your dependencies, and then create and
install the project in the `<project dir>` (omitting the `<project dir>` will
create and install in a `mezzio-skeleton/` directory).

### Manual Composer installation

You can install Mezzio standalone using Composer:

```bash
$ composer require mezzio/mezzio
```

However, at this point, Mezzio is not usable, as you need to supply
minimally:

- a router.
- a dependency injection container.

We currently support and provide the following routing integrations:

- [Aura.Router](https://github.com/auraphp/Aura.Router):
  `composer require mezzio/mezzio-aurarouter`
- [FastRoute](https://github.com/nikic/FastRoute):
  `composer require mezzio/mezzio-fastroute`
- [Laminas MVC Router](https://github.com/laminas/laminas-mvc):
  `composer require mezzio/mezzio-laminasrouter`

We recommend using a dependency injection container, and typehint against
[container-interop](https://github.com/container-interop/container-interop). We
can recommend the following implementations:

- [laminas-servicemanager](https://github.com/laminas/laminas-servicemanager):
  `composer require laminas/laminas-servicemanager`
- [pimple-container-interop](https://github.com/xtreamwayz/pimple-container-interop):
  `composer require xtreamwayz/pimple-container-interop`
- [Aura.Di](https://github.com/auraphp/Aura.Di):
  `composer require aura/di:3.0.*@beta`

Additionally, you may optionally want to install a template renderer
implementation, and/or an error handling integration. These are covered in the
documentation.

## Documentation

Documentation is [in the doc tree](doc/), and can be compiled using [bookdown](http://bookdown.io):

```bash
$ bookdown doc/bookdown.json
$ php -S 0.0.0.0:8080 -t doc/html/ # then browse to http://localhost:8080/
```

> ### Bookdown
>
> You can install bookdown globally using `composer global require bookdown/bookdown`. If you do
> this, make sure that `$HOME/.composer/vendor/bin` is on your `$PATH`.

Additionally, public-facing, browseable documentation is available at
http://mezzio.rtfd.org.

## Architecture

Architectural notes are in [NOTES.md](NOTES.md).

Please see the tests for full information on capabilities.
