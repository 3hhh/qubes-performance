# qubes-performance

Analyze [Qubes OS](https://www.qubes-os.org/) VM startup performance.

Example output:

```
Xen:
  qrexec startup: 123 ms
  Qubes DB: 3150 ms
  VM handover: 3196 ms
Linux:
  system: 4336 ms
  user: 55 ms
  system critical-chain:
    multi-user.target @4.336s
    └─qubes-misc-post.service @4.166s +169ms
      └─basic.target @3.865s
        └─sockets.target @3.865s
          └─cups.socket @3.865s
            └─sysinit.target @3.862s
              └─qubes-early-vm-config.service @3.807s +52ms
                └─local-fs.target @3.796s
                  └─run-user-1000.mount @4.224s
                    └─local-fs-pre.target @3.796s
                      └─lvm2-monitor.service @246ms +3.548s
                        └─dm-event.socket @228ms
                          └─-.mount @155ms
                            └─systemd-journald.socket @217ms
                              └─-.mount @155ms
                                └─...
  user critical-chain:
    default.target @55ms
    └─basic.target @54ms
      └─sockets.target @54ms
        └─dbus.socket @47ms +6ms
          └─-.mount @37ms
            └─-.slice @37ms
  qrexec call: 2450 ms
Overall: 10105 ms
```

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

© 2021 David Hobach
GPLv3

See `LICENSE` for details.
