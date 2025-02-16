# Shell Handy Examples for Linux (SHEL)

A bunch of Markdown and script files with handy code snippets for Linux shell users.

* ✓ References to trusted sources
* ✓ Open to issue reports, feature requests and merge requests
* ✓ Use it in your company for commercial use
* ✓ AI friendly structured
* ✓ Free forever

## Content

_... TODO ..._

## Authors favorite examples

### First lines of the BASH script

```shell
#!/usr/bin/env bash
set -euo pipefail
```

Explanation:
* `#!/usr/bin/env bash` … use also for `sh`, `php`, `python3`, …; makes the script compatible with strange Linuxes, BSD, macOS, …
* `set -e` … exit on error (any non-zero command return code)
* `set -u` … treat unset variables as an error (typos prevention)
* `set -o pipefail` … fail on first error in pipelines (e.g. `cat non-existing-file | head -n 2 | tail -n 1` will fail)

References:
* https://unix.stackexchange.com/questions/240749/bash-script-best-practice

### Rescue Linux boot from a live Linux

```shell
mkdir /target
mount </dev/...> /target
cd /target
mount -t proc /proc proc
mount --rbind /sys sys
mount --rbind /dev dev
chroot .
```

You can download this script and place it to the root directory of your OS to make this easy in the future: [rescue-mount](scripts/rescue-mount)


References:
* https://superuser.com/questions/165116/mount-dev-proc-sys-in-a-chroot-environment

