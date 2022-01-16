# qubes-performance

Analyze [Qubes OS](https://www.qubes-os.org/) VM startup performance.

Example output:

```
Xen:
  qrexec startup: 126 ms
  Qubes DB: 3461 ms
  VM handover: 3511 ms
Linux:
  kernel: 1344 ms
  system: 4220 ms
  user: 91 ms
  system critical-chain:
    multi-user.target @4.220s
    └─qubes-misc-post.service @4.005s +213ms
      └─basic.target @3.712s
        └─sockets.target @3.712s
          └─cups.socket @3.712s
            └─sysinit.target @3.707s
              └─qubes-early-vm-config.service @3.663s +42ms
                └─local-fs.target @3.662s
                  └─run-user-1000.mount @4.050s
                    └─local-fs-pre.target @3.626s
                      └─lvm2-monitor.service @266ms +3.360s
                        └─systemd-journald.socket @219ms
                          └─system.slice @150ms
                            └─-.slice @150ms
  user critical-chain:
    default.target @91ms
    └─basic.target @88ms
      └─sockets.target @88ms
        └─dbus.socket @80ms +7ms
          └─-.slice @71ms
  qubes.GetDate: n/a
  qubes.WindowIconUpdater: 808 ms
qrexec (1st run):
  exec time: 1090 ms (depends on clock sync)
  return: 1144 ms
qrexec (2nd run):
  exec time: 218 ms (depends on clock sync)
  return: 265 ms
Overall: 10345 ms (excl. 2nd qrexec run)
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
