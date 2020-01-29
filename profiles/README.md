# Profile examples

Here are several jbackup profiles created for my own devices. Note these are
meant to be examples only - they are specific to my setup and depend on
correctly configured `/etc/fstab` and/or `/etc/crypttab`.

Feel free to take inspriration or copy and uncomment `_template` and write your own.

**Remember to remove --dry-run from RSYNC\_OPTIONS** *after* you have confirmed
the profile works. When in doubt about options, see `man rsync`.
