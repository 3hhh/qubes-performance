# qubes-performance

Analyze [Qubes OS](https://www.qubes-os.org/) VM startup performance.

The [samples directory](https://github.com/3hhh/qubes-performance/tree/master/samples) contains some results to compare your own to. Pull requests to add your own results are always welcome!

## Installation

1. Download [blib](https://github.com/3hhh/blib), copy it to dom0 and install it according to [its instructions](https://github.com/3hhh/blib#installation).
2. Download this repository with `git clone https://github.com/3hhh/qubes-performance.git` or your browser and copy it to dom0.
3. Move the repository to a directory of your liking.
4. Symlink the `qubes-performance` binary into your dom0 `PATH` for convenience, e.g. to `/usr/bin/`.

### A word of caution

It is recommended to apply standard operational security practices during installation such as:

- Github SSL certificate checks
- Check the GPG commit signatures using `git log --pretty="format:%h %G? %GK %aN  %s"`. All of them should be good (G) signatures coming from the same key `(1533 C122 5C1B 41AF C46B 33EB) EB03 A691 DB2F 0833` (assuming you trust that key).
- Code review

You're installing something to dom0 after all.

## Usage

Execute `qubes-performance` for a usage description.

## Uninstall

1. Remove all symlinks that you created during the installation.
2. Remove the repository clone from dom0.
3. Uninstall [blib](https://github.com/3hhh/blib) according to [its instructions](https://github.com/3hhh/blib#uninstall).

## Copyright

© 2023 David Hobach
GPLv3

See `LICENSE` for details.
