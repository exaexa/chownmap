
# chownmap

Shell tool to map file owners accordingly to userns ranges. Handy e.g. for
easily creating/renumbering unprivileged LXC containers and similar stuff.

## Usage

```
chownmap <from> <to> <length> [ files ] ...
```

- `from` -- start of the original UID/GID range
- `to` -- start of the new UID/GID range
- `length` -- length of the range

Example:
```
chownmap 0 100000 65536 /var/lib/lxc/thecontainer/rootfs
```
will move all user/group IDs of `thecontainer` from "privileged" (root is 0) to
"unprivileged" (root is 100000).

`find`, `stat`, and `chown` are run internally for actual work. If you have
something special to tell to `chown` (`-v`, `--preserve-root` or so), use
environment variable `CHOWN_EXTRA_OPTS`.

## License

Oh please.
