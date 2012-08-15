Lara: Laravel project generator
===============================

Laravel is my favorite PHP framework. It has a great bundle called
[Bob](http://bundles.laravel.com/bundle/bob) used to generate code
(controllers, models, etc) from the command line in a similar way to
[fire](https://github.com/AzizLight/fire). However, it lacks a tool to
generate new projects. That's where Lara comes in.

**DISCLAIMER: In order to use Lara on Windows, you need to use a Unix
Terminal Emulator like Cygwin, MinGW or Git Bash.**

Requirements
------------

As a requirement, you obviously need to have PHP installed. You also
need to have `php` in your `$PATH` so that you can run `php` from the
command line.

Installation
------------

The first thing to do is to clone Lara. Clone it anywhere you want; For
this example I will clone it in `~/Sandbox/Lara`.

    git clone https://github.com/AzizLight/Lara.git ~/Sandbox/Lara

Next, you need to add the following alias to your `.bashrc`,
`.bash_profile`, `.zshrc`, or the like.

    alias lara="php $HOME/Sandbox/Lara/lara"

Usage
-----

### Bootstrapping Lara

By default, Lara will clone the latest sstable version of Laravel eveytime
you create a new project. To avoid waiting, you need to bootstrap Lara.
What this will do, is clone Laravel in the same directory as the `lara`
executable. The next time you run `lara`, it will copy that sample Laravel
project instead of cloning a fresh copy. Obviously, you can bootstrap Lara
again to get the latest stable version of Laravel. To bootstrap Lara, run
the following command:

    lara --bootstrap

#### Changing the Laravel repository

If you want to clone your own version of Laravel when bootstrapping Lara,
edit the `lara` executable. Find the line:

    'repository' => 'laravel/laravel',

Change the `laravel/laravel` portion to your own repository in the form
`user/repository` or `organisation/repository`. For example, if I want to
use the `AzizLight/laravel` repository, I would change the line as follows:

    'repository' => 'AzizLight/laravel`,

### Creating a new project

To create a new Laravel project using Lara, just supply a project name to
`lara`:

    lara MyProject

To force Lara to clone a fresh copy of Laravel, pass the `--force-clone`
argument:

    lara MyProject --force-clone

By default, Lara adds the [Bob](http://bundles.laravel.com/bundle/bob)
bundle to any new project. To create a new Laravel project without any
bundles, use the `--no-bundles` argument:

    lara MyProject --no-bundles

#### Adding your own bundles

As mentioned above, Lara adds the [Bob](http://bundles.laravel.com/bundle/bob)
bundle to any new project by default. You can add other bundles to the list
of included bundles. To do that, edit the `lara` executable, and find the
following line:

    'bundles' => array('bob'),

Add bundles to the array. For instance, if you want to add the
[Anbu](http://bundles.laravel.com/bundle/anbu) bundle:

    'bundles' => array('bob', 'anbu'),