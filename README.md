# os-build

Build configurations for different OSes

## Directory structure

At present the directories in the project are laid out like so:

    linux/
        arch/
            moarvm/
            nqp/
            rakudo/
        debian/
            moarvm/
            nqp/
            rakudo/
        fedora/

This is to say that various Linux distributions are collected under the
`linux/` directory.  Under each distribution's directory are directories for
the three projects required to build Rakudo Perl 6, `moarvm`, `nqp` and
`rakudo`.  Within each directory there will be a `Makefile` one can use to
build the given project.

It is planned that over time one can add more operating systems than only
Linux as well as to improve the list of supported Linux distributions and
the overall structure so as to easily build all required packages for a
given distribution with a simple `make`-like command.

## Debian Linux

To build the Debian packages, simply change into the `linux/debian`
directory and run:

    $ make all

This will build the `moarvm`, `nqp` and `rakudo` projects, placing the
generated `.deb` files in `/tmp/<project>_debuild/`.

## Arch Linux

Currently in development.  `PKGBUILD` files have been added for `moarvm`,
`nqp` and `rakudo`.
